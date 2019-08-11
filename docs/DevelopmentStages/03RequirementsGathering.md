# What Are Requirements?

Starting with a basic requirement definition, requirements in digital can be categorized into two types: <strong>functional</strong> and <strong>non-functional</strong>.there are other types, such as legal and technical requirements, and depending on the context, the person in charge of handling requirements documentation may need additional training in technical writing, information mapping, and more.

## What Are <strong>Functional</strong> Requirements?
For a digital engagement, functional requirements relate to a product’s functionality: its capabilities, usability, features, and operations as they relate to the intended purpose of the product. Often, functional requirements are clearly referenced as such in Functional Requirements Documentation (FRD). While a Statement of Work (SOW) outlines the high-level goals and requirements of the desired product, an FRD provides a more in-depth elaboration of these requirements, which are gathered as soon as a project kicks off and up until a project begins production.

Depending on the size and scope of a project, you might decide on a milestone between the SOW and FRD (as this timeframe can span for months). In this case, some teams create Business Requirements Documentation (BRD) to provide a formal midway sign-off—an expectation checkpoint—for all parties. This presents the opportunity for the Project Manager to confirm the team is heading in the right direction before getting too far down the road with deliverables.

## What Are <strong>Non-Functional</strong> Requirements?
Non-functional requirements encompass anything not related to a product’s functionality: its performance, stability, security, and technical specifications, to name just a few types of non-functional requirements in the digital industry.

## Functional vs. Non-Functional Requirement Examples
Both functional and non-functional requirements documentation are equally instrumental in their own ways. They exist hand in hand; one is directly affected by the other.

Even so, not all non-functional requirements correspond directly to a functional requirement. Server setup and configuration, for example, is a non-functional requirement that has an impact on an entire site’s stability, without a direct 1:1 relationship with any singular functional requirement.

Here are a few examples of functional and non-functional requirements, and how they are related:

  * Functional Requirement: payment processing functionality
  * Non-Functional Requirement: SSL certificate
  While it’s 2018 and websites should have SSL certificates regardless, it’s especially important to do so if there is payment processing functionality implemented on the site. This is an example of a non-functional requirement (SSL certificate, an element of the implementation which affects security) directly affecting a functional requirements (payment, an element of the implementation which affects usability).

Here’s another example:

  * Functional Requirement: tools and resources (PDF, infographics, courseware, spreadsheets) available for users, accessible via the Resources landing page
  * Non-Functional Requirement: administrative panel file format specs (e.g. “The following file formats are valid for upload within the administrative user panel, in relation to the Resources page: .zip, .jpeg, .csv, .pdf”)
  
  Per the functionality of the Resources landing page, users are able to access resources such as PDFs, infographics, courseware, or spreadsheets. This functionality is a feature and an operation of the page. It is a functional requirement.

The administrative panel file format specs, on the other hand, are a non-functional requirement; they are technical specs related to administrative functionality. They do not affect the usability of the end users. Yes, these specs do affect the usability of the administrative users, but it does not directly define what the product’s functionality is for the end user. This is a non-functional requirement.

## The Importance Of Requirements Management
Requirements management is important for two main reasons:

  * Requirements documentation serves as a point of reference to document the evolution of a project, its moving parts, and its implementation
  * Requirements documentation serves as a blueprint for the client to better understand what to expect out of the project (the what, where, when, and why of the project).
In addition to outlining what they can expect, part of requirements management planning should outline what not to expect. Including an “Assumptions” and/or “Exclusions” section is a wise approach to eliminate the risk of the dreaded client imagination.

Let’s look at an example showing how requirements gathering is important as a point of reference and a blueprint for managing expectations:

Requirement Example:
What: PayPal integration
Where: Checkout
When: Within step 3 of 4 in the checkout experience (after the shipping address webform, before confirmation)
Why: An established integration (e.g. PayPal) is a better solution than a robust custom build integration for a payment service in this case because it easily meets client requirements.
Assumptions
Flat fee for all shipping & handling
All shipping is within the U.S. (not including Alaska or Hawaii)
Taxes do not apply
Exclusions
Custom shipping & handling fee calculations
Shipping internationally, to Alaska, or to Hawaii
Tax rules
Remember: the smaller the delta between client expectation and reality with their digital product, the happier your client is going to be with the end result.

#Requirements Gathering Process

#### 1. Take notes
In every meeting you’re in—whether that be internal with your project team or external with your client—always take notes. Never assume someone else is taking them. Chances are…they aren’t.

Digital Projects Managers are not secretaries, but there is an expectation that we capture action items, needs for clarification, opportunities for additional research/discussion, and any other important information discussed in meetings. In the moment, it may be easy to assume everything being discussed will be remembered, but 3 months and 15 meetings later, your team and your client will thank you for having a record of those discussions to look back on.

Read more on great note-taking strategies or check out some of my recommended procedure for taking requirements notes here:

Before going into your meeting, prepare your notes document to reflect your agenda so organizing the action items and points will be easier. For example, your agenda may have the points, “Paypal integration”, “Checkout landing page”, and “Promotional code functionality”. On your notes document, add those items as headers and include any points you or your team may want to bring up underneath the corresponding header. This way, you’ll remember to bring up what’s needed while capturing related information in an organized manner.
After any meeting, schedule 15-30 minutes for yourself to review your notes, digest what was discussed, prioritize action items, identify challenges/red flags and needs for clarification or additional meetings.
Send your notes to your internal project team. Have them review and verify what you’ve identified as action items, red flags, etc.
Once the team has given you their blessing, send your notes to your client.
Finally, leverage your notes as reference for creating tasks (e.g. JIRA tasks) out of each action item. Add any new information into your requirements documentation, and schedule any needed meetings for additional discovery or discussion.
Save your notes in a shared space, perhaps within a “Meeting Notes” folder of a Google Drive instance, so that your project team members are able to easily access and reference them in the future.

#### 2. Go Over The Creative Requirements
Don’t leave design and styling decisions up for grabs: provide creative requirements whenever possible. If your timeline and budget allows, creative guidance is invaluable for developers. While you may find that rare unicorn developer who doubles as a designer, more often than not you’ll find a developer is best at developing; do not task them with the design.

At the very least, provide a style guide—even if the style guide is as bare bones as font and brand colors. Ideally, you will have both wireframes and full user interface designs for mobile and desktop across all page types.

Once you have gathered them, upload all the creative assets to shared space for full team access and visibility. Make sure you’re saving the final versions of these designs in one place, separate from any older versions, so your team is absolutely certain they are referencing the final creative assets.

When creative is finalized and formally approved by the client, it’s valuable to schedule an internal handoff meeting for the project team; this presents an opportunity for your creative team members to smoothly hand off their work to the development team members. It also allows for discussion to ask questions, clear up needs for clarification, and reduce the risk of developer assumptions—an otherwise dangerous game. Your “creative team” may not be limited to your UX/UI designers; this may also include a digital strategist to speak for the user journeys, or a content architect to discuss the sitemap. Include everyone who contributed to deliverables thus far, which will inevitably play into the development, production, and implementation ahead.

#### 3. Make Annotations
Once you’ve handed off the deliverables from creative to development, it’s time to annotate your page elements across all page types. This can include static vs. carousel hero images, dropdowns vs. text fields in webforms, dropdowns vs. slideouts, pop-up modals vs. new page loads, and any other functionality on each page type.

Only annotate pages once they are absolutely final. There is nothing worse than having to re-annotate a page with 35 elements on it just because a pagination bullet shadow was removed (okay—there are worse things, but you get my point).

Each page element requires an annotation. Use a tool such as Invision or Skitch to annotate the page designs.

Typically, I start by annotating the mobile page design and then I annotate the corresponding desktop design—only where functionality of that page differs from the mobile experience to the desktop experience. Why start with mobile? In the digital industry, it’s most beneficial to keep a “Mobile First” mentality in mind when producing a digital solution. That being said, you may very well have a client in the Industrial or Mechanical Product space whose users access their platform via warehouse desktops and are unable to access via mobile devices. In that case, by all means you should accommodate and annotate the desktop page designs first.

My point is this: whether mobile, tablet, desktop, portrait, landscape, what have you … annotate the format or type of page design first that makes most sense. Then, adjust the remaining designs for each page if/as needed.  I include the following note within my requirements documentation to disclaim this intent:

Once your creative is annotated, load the images into your documentation. Do this in an order that makes most sense. If a user journey exists, it’s most beneficial to leverage this as guidance for the order in which you organize the annotated designs. For example:

Homepage
Product Category Landing Page
Product Detail Page
Product Customization Page
Checkout Page
Payment Page
Confirmation Page
If you do not have a user journey to leverage, then organize your annotate page designs in a way that makes sense for your client. Homepage is always a safe bet for a first design to display in your requirements documentation – likely it’s the page design with which your client is most familiar at this point. Remember: at this point of the engagement, nothing you are including within the requirements documentation should be a surprise for your client. This is not a vehicle for presenting anything new to them; this documentation formalizes what has already been discussed, decided, and (at least softly) approved by your client.

### Write The Requirements Document
As you dive into documentation, remember: your first go at requirements documentation will be the most difficult. Why? Because you do not have a previous document from which to leverage (aka COPY-PASTE). Lucky for you, dear DPM friend, this article includes a requirements documentation template to serve as a foundation for you.

As displayed in this template, I organize my requirements documentation into four parts:

Annotation
Includes the numbers from your annotated design. If your page design has 8 elements on it, you will have 8 annotations, and your annotation column will have 8 rows
Element
Includes element titles, as they relate to each annotation
Functional requirement
Includes a definition (the requirements, spelled out) for each element
Admin/CMS functionality
Define any administrative and/or CMS functionality, as is related to the corresponding element

#### 4. Hold An Internal Review

Once you have completed your first draft of the requirements documentation, crack a beer. Or a root beer. Enjoy it. But only one. There is still work to do. And I promise: the work up front is worth it.

In this part of the requirements gathering process, you schedule another internal meeting with your project team to review your requirements documentation all together. This is a final internal checks and balances to ensure your understanding of the implementation. This is imperative. Because guess what? As the DPM, you manage the client expectations for the implementation. Your understanding of it is critical to the success of the project and your client’s happiness.

If possible, have the team review your requirements documentation prior to the meeting so they’re able to come ready with their questions and/or feedback. Use the meeting to discuss any questions, and feedback on the requirements. Identify gaps in understanding nd verify consistency of the requirements documentation.

As part of the internal review phase, you’ll need to make any necessary revisions to the documentation, based on your internal discussion. Finally, re-send the revised requirements documentation to the team for one final blessing.

Once the internal project team provides their final approval of the requirements documentation, save the document as a PDF (here’s some info on PDFs and how to edit PDFs) to ensure that remains in its finalized state for the next step: task buildout.

#### 5. Build Out Tasks

Provide the PDF version of the requirements documentation to your development team. Ideally, your developers or development lead will perform the task buildout for the build. While some organizations may operate under a process where DPMs build out all tasks, I prefer to have developers build out their own tasks; the handful of hours it takes for them is worth it. This allows developers to build out tasks in a way that suits their development approach.

You can still provide useful guidelines for your team as they build out their development tasks. Here are some example guidelines for a website build:

No task should exceed 8 hours
Follow verbiage specific to JIRA, but applicable across other tools
Each page type element annotated in the requirements documentation should have its own subtask
Mobile and desktop should have separate stories
1 sprint = 1 week
Use time estimates (story points or hours)
After task buildout, you will be able to get a final hour estimate. For example, if a developer builds out all of their tasks with hour estimates and their hours total 150, then…

Assume your developer is single-threaded (focused only on your project)
Each week you will get 35 hours of their time
150 hours total at 35 hours per week = 4.3 weeks
Add QA, which should typically be 20% of your development time
150 hours development = 30 hours of QA, or 1 week
Now, you can confirm your development timeline is 4 or 5 weeks followed by 1 week of QA.
mind-blown

At this point, you compare that projection to the timeline that has been communicated to your client previously, and manage accordingly if/as needed. For more on estimating projects, see this complete [project estimation guide](https://thedigitalprojectmanager.com/project-budget-cost-estimation-guide/).

#### 6. Hold An External Review

At this point, you have:

*Written your requirements documentation
*Confirmed the documentation with your internal project team
*Built out development tasks, based on the requirements documentation
*Confirmed the projected timeline through QA, based on the requirements documentation

It’s time to present the requirements documentation to your client. Provide this as a PDF to ensure no edits are made. Include a message immediately requesting a meeting to walk through this documentation together. This (1) exemplifies investment on your part to ensure client understanding of the digital solution and (2) will be insurance for you, as a DPM, to be able to say “I told you so” (but far more eloquently) when scope creep inevitably rears its ugly head later on in the process.

Educate your client. Walk them through this precious documentation you so painstakingly put together for them. You may have clients who has a rich history of implementing digital solutions. But I’m betting that more often than not, you don’t and they haven’t.

While your client may scoff off a documentation walk through, you may be surprised with their interest and appreciation in having the ability to walk through the documentation with you. Remember: they are the experts of their business. You are the expert of the digital solution you’re offering them. They are paying you for this solution. Educate and empower your client. They (probably) deserve that. Kick off the conversation with making sure they understand this is the time to ask whatever questions they may have, ask for clarify, and that no question is a dumb question. They will appreciate that. Worst case scenario: they decline the request for a walk through. At least you can say you offered. And I will tell you this: I have not had one client decline this request.

Once the client has confirmed their understanding of the requirements documentation (whether or not they decided to do a walk through with you), it’s finally time to receive formal approval. I highly recommend receiving a signature for this requirements documentation prior to starting any development whatsoever. It seems like a given – but this dependency is abused more often than not. Do your very best to adhere to it.

Send the signed and approved requirements documentation to your team and save in a shared space, so there is a formal indication that development may begin.

### The Wrong Way To Gather Rquirements

Below is an example of a not-so-great requirement—an example where requirements management is severely lacking. This is a real requirement that was included within documentation that a real client signed off on for a custom e-commerce website build.

All extensions that exist on the current [VERSION 1 OF UNDISCLOSED ECOMMERCE PLATFORM] website will be implemented and functional on the new [VERSION 2 OF UNDISCLOSED ECOMMERCE PLATFORM] website.

Oh my Lanta. The ambiguity.

While I’m not going to rewrite the multiple pages of technical and functional requirements documentation the sentence above truly deserves, I am going to outline a few questions to break open the requirement and challenge the author to further clarify and document what exactly this means.

* Which extensions exist on the current VERSION 1 of this website?
* For each extension, I want to know:
      * Which version is it?
      * Who is the creator/source/developer?
      * What feature or functionality does it offer?
* Are all extensions capable of running on VERSION 2 of this platform?
      * If yes, list out each extension that is capable of running on the new platform
      * If no, list out each extension that is not capable of running on the new platform, as well as the replacement solution, whether that be another extension that is capable on the new platform or a custom solution.
* Is there a cost associated with any of these extensions? For each cost:
      * Is it a one-time implementation license/cost? Will the cost carry over from the previous license, or is a new license required?
      * Are there any subscription costs?
* Will the cost be the same if running on a newer version of the platform?
      * Will any additional costs be considered a change order?


While your team may very well know the answers to all of the above, knowing does not suffice. That knowledge must be documented thoroughly. The DPM must manage ask those questions and poke those holes in order to make sure those holes get filled.

The above questions easily prompt a few pages of requirements, depending on the number of extensions applicable to the build. With this particular example, there were more than 100 extensions implemented on the current VERSION 1 of the platform. Needless to say…chaos ensued. I’ll leave the rest of that story to your imagination.

# Requirements Gathering Techniques

#### 1. Start Right Away

#### 2. Make Use Of Templates
[document templates](https://thedigitalprojectmanager.com/requirements-gathering-guide/#documenttemplate)

#### 3. Teamwork

It’s highly unlikely you’ll have just one individual drumming up project requirements—this is where requirements elicitation comes in. If there are different types of resources on a project (e.g. User Experience Designer, User Interface Designer, Software Engineer, Frontend Developer, Digital Strategist, Content Architect, etc.), the requirements for each area of expertise may be authored by the respective experts.

Have you ever played telephone? Of course you have. When a DPM scribes documentation that originated in the mind of a developer (or a strategist, or a designer), you run the risk of something getting lost in translation. In many cases, the conversation about requirements is a winding trail of phone calls, various separate meetings and conversations, etc. This is where is is critical that you, as the DPM, assign out requirements documentation to respective team members in order to elicit and compile requirements.

To help your team with requirements elicitation, make sure you:

* provide documentation templates
* capture and share your notes
* arrange for the right conversations to happen
* facilitate requirements documentation planning meetings and reviews
* put the final touches on the documentation

By the time you start writing the requirements for your requirements documentation, you should already have had multiple points of checks and balances related to requirements, including:

* Client meetings (where designs were reviewed and at least softly approved)
* Shared nots (where decisions were captured, reviewed by both internal and client team, and confirmed as valid)
* Internal review/handoff (where designs were reviewed and page elements were confirmed)
That said, make sure you leverage your team members as you need to complete the requirements sufficiently.

#### 4. Don’t Just Record Requirements—Learn
Do more than take notes. Expect more than resources emailing you a wall of text comprising their portion of the requirements. Take the time to sit down with your team of developers and learn the solutions the team has in mind for implementation. Discuss why and how. Ask questions.

Before you say, “But we only have so much time in the day—and what about the budget?”, understand this: if a solution you’re working on is applicable to more than one project, then this additional time for getting an understanding does not necessarily need to be billable. You’re growing your subject matter expertise that directly improves your day-to-day work.

#### 5. Keep Your Client In The loop

Requirements documentation does not have to be Level 1 Confidentiality with a big red Top Secret stamped diagonally across the front page. While you can absolutely have an internal requirements document where you’re less worried about including more transparent notes, it doesn’t hurt to have a client-facing WIP requirements document.

If you’re not dealing with sensitive information, you can create this shared space through a Google Doc, with permissions enabled for the client to comment.

If you are dealing with sensitive information, share a version of the requirements document on a weekly basis to provide a client a snapshot of what’s been captured. After all, this is a document they’ll eventually have to sign off on.

#### 6. Assume Your Client Knows Nothing

Rather than running the risk of assuming your client knows more than they do (then having that burn you later on when they truly didn’t know the difference between “plug-in solution” and “custom solution”), assume your client knows nothing. Define as much as you can. How? For each annotation, ask yourself “Why?” five times to ensure thoroughness of each requirement.

Here is an example of asking “Why?” 5 times in order to define your requirements:

Annotation for Registration Page:
User Store Location must be a dropdown selection.

Why?
Text field input increases the risk of errors in user entry. Dropdown selection limits the number of options from which a user may choose.

Why?
If there was a text field input, “MINNEAPOLIS” could be entered in as “MINNEAPOLIS” or “MPLS” or “Mini-apple-us” and data would be messy. This is not good. A drop down selection limits the options to whichever options the admin enters into the backend admin panel. This limited selection is good, for sake of accuracy.

Why?
The client wants to use their user data in order to eventually segment content based on user location.

Why?
This client has content specific to location/region based on the products they offer.

Why?
Because BUSINESS.

Asking yourself “Why?” five times for each requirement also challenges you to really consider the logic behind every element and functionality of each page type. You may be surprised with how much you learn (or realize you need to learn).

# Some Expert Tips: How To Write A Project Requirements Document
#### 1. Write Requirements For Global Elements Separately
To eliminate redundancy, cover all global elements in a “Global Elements” section of your requirements documentation. This is applicable for global elements such as your main navigation menu items, anything within your global header, and anything within your footer. Once you’ve written requirements for these global elements, do not bother annotating them throughout the other pages; only annotate elements specific to those pages.
#### 2. Copy-Paste Identical Functionality To Ensure Consistency
This is merely a tip to keep in mind for your  (and your client’s) sanity. You’ll see this most with common page elements such as hero/banner images, headers, or “back” icons…among a large number of repeated functionality across page types (not to be confused with global elements). This is not new age Google SEO Strategy where you have to worry about repeating words or phrases, and this is not your Grade 9 English Essay where you have to make the same idea sound profound by rewording it six different times. This is requirements documentation.
#### 3. Acknowledge Admin And CMS (Or Lack Thereof)
When we are so focused on functionality of each page element, it is easy to disregard administrative and/or CMS functionality. If you’re implementing a solution which offers administrative and/or CMS functionality, be sure to include this as its own column in your requirements. Example below:
#### 

## Helpful Tools

Develop a <strong>use case diagram</strong>, including all the imagined steps in a new process. It could mean using the “As-Is” and “To-Be” model, where you diagram the current steps required (As-Is) and then add a “swim lane” (To-Be) showing the optimised solution.

It’s worth spending the time documenting the ‘As-Is’model for major or complex processes so the entire team can develop a common understanding of the business process.

The ‘To-Be’ model shows how the business process becomes adjusted with the new system in place (sometimes it’s helpful to overlay the As-Is with the To-Be to understand the changes).

Put yourself in the role of the user and think about how they go from one step to another to achieve their goals using the software and what dependencies might be involved (such as querying the database for a unique identifier). Note that it’s also important to know what users should not be doing with the software, or abilities that should be invisible to them!

Another useful tool is to collect <strong>user stories</strong> on how they do things. If a user story is too complicated, it can be broken down into smaller stories and supported with diagrams.

Often scoping the project might require a <strong>context diagram</strong> to define the system’s boundary, its surrounding environment and all the interacting entities.

Being complete also means being thorough: know the system and how it works in the context necessary. How will it integrate with other systems? How will the databases communicate? What APIs will be needed and how are they already being used? By constructing a visual model of the software solution, you’ll get a better idea of the major interactions and players in your system.

A different sort of diagram that can be used is the top-down illustration, called a <strong>functional decomposition diagram</strong>, which is useful to break down the system into major chunks.

Remember not to make assumptions or take anything for granted. Be as detailed as possible and document every step needed to accomplish a task. Reiterate the key objectives during the requirements gathering process to ensure everyone is happy. One way to do this is to use SMART goals: Specific, Measurable, Agreed-upon, Realistic and Time-based.

Ask your stakeholders what they need and how your team can make their lives easier. Have they encountered pitfalls on other projects and can it be worked into the current spec as potential hazards? This is part diplomacy and part functional requirement gathering.

Finally, if you hit problems, then it’s better to have encountered them early on, during the requirements gathering stage, rather than at some time further down the road, when it could cost additional time and money to put right!

### Source Information
[Master Your Requirements Gathering (Here’s How)](https://thedigitalprojectmanager.com/requirements-gathering-guide/#typesrequirements)

[Requirements Gathering for Software](https://www.bbconsult.co.uk/blog/requirements-gathering)

[Return](README.md)
