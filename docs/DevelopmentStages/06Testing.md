
#Testing: After the code is developed it is tested against the requirements to make sure that the product is actually solving the needs addressed and gathered during the requirements phase. During this phase all types of functional testing like unit testing, integration testing, system testing, acceptance testing are done as well as non-functional testing are also done.

## [Unit testing](https://www.toptal.com/qa/how-to-write-testable-code-and-why-it-matters)

A typical unit test contains 3 phases: 

1. it initializes a small piece of an application it wants to test (also known as the system under test, or SUT), 
2. it applies some stimulus to the system under test (usually by calling a method on it), 
3. it observes the resulting behavior. If the observed behavior is consistent with the expectations, the unit test passes, otherwise, it fails, indicating that there is a problem somewhere in the system under test. 

These three unit test phases are also known as Arrange, Act and Assert, or simply AAA.

A unit test can verify different behavioral aspects of the system under test, but most likely it will fall into one of the following two categories: <strong> state-based </strong> or <strong> interaction-based</strong>. Verifying that the system under test produces correct results, or that its resulting state is correct, is called state-based unit testing, while verifying that it properly invokes certain methods is called interaction-based unit testing.

### Unit Test vs. Integration Test
Another important thing to consider is the difference between unit testing and integration testing.

The purpose of a <strong>unit test in software engineering is to verify the behavior of a relatively small piece of software, independently from other parts</strong>. Unit tests are narrow in scope, and allow us to cover all cases, ensuring that every single part works correctly.

On the other hand, <strong>integration tests demonstrate that different parts of a system work together in the real-life environment</strong>. They validate complex scenarios (we can think of integration tests as a user performing some high-level operation within our system), and usually require external resources, like databases or web servers, to be present.

A reasonable combination of unit and integration tests ensures that every single unit works correctly, independently from others, and that all these units play nicely when integrated, giving us a high level of confidence that the whole system works as expected.

However, we must remember to always identify what kind of test we are implementing: a unit or an integration test. The difference can sometimes be deceiving. If we think we are writing a unit test to verify some subtle edge case in a business logic class, and realize that it requires external resources like web services or databases to be present, something is not right — essentially, we are using a sledgehammer to crack a nut. And that means bad design.

## What Makes a Good Unit Test?
Before diving into the main part of this tutorial and writing unit tests, let’s quickly discuss the properties of a good unit test. Unit testing principles demand that a good test is:

* Easy to write. Developers typically write lots of unit tests to cover different cases and aspects of the application’s behavior, so it should be easy to code all of those test routines without enormous effort.

* Readable. The intent of a unit test should be clear. A good unit test tells a story about some behavioral aspect of our application, so it should be easy to understand which scenario is being tested and — if the test fails — easy to detect how to address the problem. With a good unit test, we can fix a bug without actually debugging the code!

* Reliable. Unit tests should fail only if there’s a bug in the system under test. That seems pretty obvious, but programmers often run into an issue when their tests fail even when no bugs were introduced. For example, tests may pass when running one-by-one, but fail when running the whole test suite, or pass on our development machine and fail on the continuous integration server. These situations are indicative of a design flaw. Good unit tests should be reproducible and independent from external factors such as the environment or running order.

* Fast. Developers write unit tests so they can repeatedly run them and check that no bugs have been introduced. If unit tests are slow, developers are more likely to skip running them on their own machines. One slow test won’t make a significant difference; add one thousand more and we’re surely stuck waiting for a while. Slow unit tests may also indicate that either the system under test, or the test itself, interacts with external systems, making it environment-dependent.

* Truly unit, not integration. As we already discussed, unit and integration tests have different purposes. Both the unit test and the system under test should not access the network resources, databases, file system, etc., to eliminate the influence of external factors.

That’s it — there are no secrets to writing unit tests. However, there are some techniques that allow us to write testable code.

## Testable and Untestable Code
Some code is written in such a way that it is hard, or even impossible, to write a good unit test for it. So, what makes code hard to test? Let’s review some anti-patterns, code smells, and bad practices that we should avoid when writing testable code.

### Poisoning the Codebase with Non-Deterministic Factors
Let’s start with a simple example. Imagine that we are writing a program for a smart home microcontroller, and one of the requirements is to automatically turn on the light in the backyard if some motion is detected there during the evening or at night. We have started from the bottom up by implementing a method that returns a string representation of the approximate time of day (“Night”, “Morning”, “Afternoon” or “Evening”):

    public static string GetTimeOfDay()
    {
        DateTime time = DateTime.Now;
        if (time.Hour >= 0 && time.Hour < 6)
        {
           return "Night";
       }
        if (time.Hour >= 6 && time.Hour < 12)
        {
        return "Morning";
        }
        if (time.Hour >= 12 && time.Hour < 18)
       {
            return "Afternoon";
        }
        return "Evening";
    }

Essentially, this method reads the current system time and returns a result based on that value. So, what’s wrong with this code?

If we think about it from the unit testing perspective, we’ll see that it is not possible to write a proper state-based unit test for this method. DateTime.Now is, essentially, a hidden input, that will probably change during program execution or between test runs. Thus, subsequent calls to it will produce different results.

Such non-deterministic behavior makes it impossible to test the internal logic of the GetTimeOfDay() method without actually changing the system date and time. Let’s have a look at how such test would need to be implemented:

    [TestMethod]
    public void GetTimeOfDay_At6AM_ReturnsMorning()
    {
        try
        {
            // Setup: change system time to 6 AM
            ...
    
            // Arrange phase is empty: testing static method, nothing to initialize
    
            // Act
            string timeOfDay = GetTimeOfDay();
    
            // Assert
            Assert.AreEqual("Morning", timeOfDay);
        }
        finally
        {
            // Teardown: roll system time back
            ...
        }
    }
    
Tests like this would violate a lot of the rules discussed earlier. It would be expensive to write (because of the non-trivial setup and teardown logic), unreliable (it may fail even if there are no bugs in the system under test, due to system permission issues, for example), and not guaranteed to run fast. And, finally, this test would not actually be a unit test — it would be something between a unit and integration test, because it pretends to test a simple edge case but requires an environment to be set up in a particular way. The result is not worth the effort, huh?

Turns out that all these testability problems are caused by the low-quality GetTimeOfDay() API. In its current form, this method suffers from several issues:

* It is tightly coupled to the concrete data source. It is not possible to reuse this method for processing date and time retrieved from other sources, or passed as an argument; the method works only with the date and time of the particular machine that executes the code. Tight coupling is the primary root of most testability problems.

* It violates the Single Responsibility Principle (SRP). The method has multiple responsibilities; it consumes the information and also processes it. Another indicator of SRP violation is when a single class or method has more than one reason to change. From this perspective, the GetTimeOfDay() method could be changed either because of internal logic adjustments, or because the date and time source should be changed.

* It lies about the information required to get its job done. Developers must read every line of the actual source code to understand what hidden inputs are used and where they come from. The method signature alone is not enough to understand the method’s behavior.

* It is hard to predict and maintain. The behavior of a method that depends on a mutable global state cannot be predicted by merely reading the source code; it is necessary to take into account its current value, along with the whole sequence of events that could have changed it earlier. In a real-world application, trying to unravel all that stuff becomes a real headache.

After reviewing the API, let’s finally fix it! Fortunately, this is much easier than discussing all of its flaws — we just need to break the tightly coupled concerns.

FIXING THE API: INTRODUCING A METHOD ARGUMENT
The most obvious and easy way of fixing the API is by introducing a method argument:

    public static string GetTimeOfDay(DateTime dateTime)
    {    
        if (dateTime.Hour >= 0 && dateTime.Hour < 6)
        {
            return "Night";
        }
        if (dateTime.Hour >= 6 && dateTime.Hour < 12)
        {
            return "Morning";
        }
        if (dateTime.Hour >= 12 && dateTime.Hour < 18)
        {
            return "Noon";
        }
        return "Evening";
    }
    
Now the method requires the caller to provide a DateTime argument, instead of secretly looking for this information by itself. From the unit testing perspective, this is great; the method is now deterministic (i.e., its return value fully depends on the input), so state-based testing is as easy as passing some DateTime value and checking the result:
    [TestMethod]
    public void GetTimeOfDay_For6AM_ReturnsMorning()
    {
        // Arrange phase is empty: testing static method, nothing to initialize

        // Act
        string timeOfDay = GetTimeOfDay(new DateTime(2015, 12, 31, 06, 00, 00));

        // Assert
        Assert.AreEqual("Morning", timeOfDay);
    }
    
Notice that this simple refactor also solved all the API issues discussed earlier (tight coupling, SRP violation, unclear and hard to understand API) by introducing a clear seam between what data should be processed and how it should be done.

Excellent — the method is testable, but how about its clients? Now it is the caller’s responsibility to provide date and time to the GetTimeOfDay(DateTime dateTime) method, meaning that they could become untestable if we don’t pay enough attention. Let’s have a look how we can deal with that.

FIXING THE CLIENT API: DEPENDENCY INJECTION
Say we continue working on the smart home system, and implement the following client of the GetTimeOfDay(DateTime dateTime) method — the aforementioned smart home microcontroller code responsible for turning the light on or off, based on the time of day and the detection of motion:

    public class SmartHomeController
    {
        public DateTime LastMotionTime { get; private set; }

        public void ActuateLights(bool motionDetected)
        {
            DateTime time = DateTime.Now; // Ouch!

            // Update the time of last motion.
            if (motionDetected)
            {
                LastMotionTime = time;
            }

            // If motion was detected in the evening or at night, turn the light on.
            string timeOfDay = GetTimeOfDay(time);
            if (motionDetected && (timeOfDay == "Evening" || timeOfDay == "Night"))
            {
                BackyardLightSwitcher.Instance.TurnOn();
            }
            // If no motion is detected for one minute, or if it is morning or day, turn the light off.
            else if (time.Subtract(LastMotionTime) > TimeSpan.FromMinutes(1) || (timeOfDay == "Morning" || timeOfDay == "Noon"))
            {
                BackyardLightSwitcher.Instance.TurnOff();
            }
        }
    }

Ouch! We have the same kind of hidden DateTime.Now input problem — the only difference is that it is located on a little bit higher of an abstraction level. To solve this issue, we can introduce another argument, again delegating the responsibility of providing a DateTime value to the caller of a new method with signature ActuateLights(bool motionDetected, DateTime dateTime). But, instead of moving the problem a level higher in the call stack once more, let’s employ another technique that will allow us to keep both ActuateLights(bool motionDetected) method and its clients testable: Inversion of Control, or IoC.

Inversion of Control is a simple, but extremely useful, technique for decoupling code, and for unit testing in particular. (After all, keeping things loosely coupled is essential for being able to analyze them independently from each other.) The key point of IoC is to separate decision-making code (when to do something) from action code (what to do when something happens). This technique increases flexibility, makes our code more modular, and reduces coupling between components.

Inversion of Control can be implemented in a number of ways; let’s have a look at one particular example — Dependency Injection using a constructor — and how it can help in building a testable SmartHomeController API.

First, let’s create an IDateTimeProvider interface, containing a method signature for obtaining some date and time:

    public interface IDateTimeProvider
    {
        DateTime GetDateTime();
    }

Then, make SmartHomeController reference an IDateTimeProvider implementation, and delegate it the responsibility of obtaining date and time:

    public class SmartHomeController
    {
        private readonly IDateTimeProvider _dateTimeProvider; // Dependency

        public SmartHomeController(IDateTimeProvider dateTimeProvider)
        {
            // Inject required dependency in the constructor.
            _dateTimeProvider = dateTimeProvider;
        }

        public void ActuateLights(bool motionDetected)
        {
            DateTime time = _dateTimeProvider.GetDateTime(); // Delegating the responsibility

            // Remaining light control logic goes here...
        }
    }

Now we can see why Inversion of Control is so called: the control of what mechanism to use for reading date and time was inverted, and now belongs to the client of SmartHomeController, not SmartHomeController itself. Thereby, the execution of the ActuateLights(bool motionDetected) method fully depends on two things that can be easily managed from the outside: the motionDetected argument, and a concrete implementation of IDateTimeProvider, passed into a SmartHomeController constructor.

Why is this significant for unit testing? It means that different IDateTimeProvider implementations can be used in production code and unit test code. In the production environment, some real-life implementation will be injected (e.g., one that reads actual system time). In the unit test, however, we can inject a “fake” implementation that returns a constant or predefined DateTime value suitable for testing the particular scenario.

A fake implementation of IDateTimeProvider could look like this:

    public class FakeDateTimeProvider : IDateTimeProvider
    {
        public DateTime ReturnValue { get; set; }

        public DateTime GetDateTime() { return ReturnValue; }

        public FakeDateTimeProvider(DateTime returnValue) { ReturnValue = returnValue; }
    }
    
With the help of this class, it is possible to isolate SmartHomeController from non-deterministic factors and perform a state-based unit test. Let’s verify that, if motion was detected, the time of that motion is recorded in the LastMotionTime property:

    [TestMethod]
    void ActuateLights_MotionDetected_SavesTimeOfMotion()
    {
        // Arrange
        var controller = new SmartHomeController(new FakeDateTimeProvider(new DateTime(2015, 12, 31, 23, 59, 59)));

        // Act
        controller.ActuateLights(true);

        // Assert
        Assert.AreEqual(new DateTime(2015, 12, 31, 23, 59, 59), controller.LastMotionTime);
    }

Great! A test like this was not possible before refactoring. Now that we’ve eliminated non-deterministic factors and verified the state-based scenario, do you think SmartHomeController is fully testable?

### Poisoning the Codebase with Side Effects







[Return](README.md)
