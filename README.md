# Software engineering at Google

My arbitrary selection of quotes and notes on the book [Software engineering at Google](https://abseil.io/resources/swe-book "Software engineering at Google").  

- [Management](#management)
    - [What Is Software Engineering?](#what-is-software-engineering)
    - [How to work well on teams](#how-to-work-well-on-teams)
    - [Knowledge Sharing](#knowledge-sharing)
    - [How to Lead a Team](#how-to-lead-a-team)
    - [Leading at scale](#leading-at-scale)
- [Processes](#processes)
    - [Style Guides and rules](#style-guides-and-rules)
    - [Code Review](#code-review)
    - [Documentation](#documentation)
- [Tests](#tests)
    - [Testing Overview](#testing-overview)
    - [Unit Testing](#unit-testing)
    - [Test Doubles](#test-doubles)
    - [Larger Testing](#larger-testing)
- [Various notes](#various-notes)
    - [Depreciation](#depreciation)
    - [Version Control and Branch Management](#version-control-and-branch-management)
    - [Dependency management](#dependency-management)
    - [Continuous integration](#continuous-integration)
    - [Continuous delivery](#continuous-delivery)

## Management
### What Is Software Engineering?

- Software engineering is programming integrated over time.
- We might need to delineate between **programming** tasks (development) and **software engineering** tasks (development, modification, maintenance).
- Programming is about producing code. Software engineering extends that to include **the maintenance** of that code for its useful life span.
- Our project is sustainable if, for the expected life span of your software, we are capable of reacting to whatever valuable change comes along, for either technical or business reasons. We may choose to not change things, but we need to be capable.
- Hyrum’s Law: > with a sufficient number of users of an API, it does not matter what you promise in the contract: all observable behaviors of your system will be depended on by somebody.
- There's a fundamental difference between “it works” versus “it is correct”. A basic example:  
    > “Can I assume a particular output sequence for my hash container?” For a short-lived program, depending on the iteration order of your containers will not cause any technical problems. For a software engineering project, on the other hand, such reliance on a defined order is a risk—given enough time, something will make it valuable to change that iteration order.
- "Because I said so" is a terrible reason to do things. This is not to say that decisions need to be made unanimously, or even with broad consensus; in the end, someone must be the decider. This is primarily a statement of how the decision-making process should flow for whoever is actually responsible for the decision.
- Being data driven is a good start, but in reality, most decisions are based on a mix of data, assumption, precedent, and argument. Being data driven over time implies the need to change directions when the data changes

### How to work well on teams

- Software development is a **team endeavor**. And to succeed on an engineering team — or in any other creative collaboration — we need to reorganize our behaviors around the core principles of **humility**, **respect**, **and trust** (the three pillars of social interaction):
    - **Humility** : You are not the center of the universe (nor is your code!). You’re neither omniscient nor infallible.  You’re open to self-improvement.
    - **Respect**: You genuinely care about others you work with.  You treat them kindly and appreciate their abilities and accomplishments.
    - **Trust**: You believe others are  competent and will do the right thing, and you’re OK with letting them drive when appropriate.
- If you perform a root-cause analysis on almost any social conflict, you can ultimately trace it back to a lack of humility, respect, and/or trust.
- What will make or break your career, is **how well you collaborate with others**.
- The **Genius Myth** is the tendency that we as humans need to ascribe the success of a team to a single person/leader.
    - The Genius Myth is just another manifestation of our **insecurity**.
    - Many programmers are afraid to share work they’ve only just started because it means peers will **see their mistakes** and know **the author of the code is not a genius**.
    - This is an extremely common feeling among programmers, and the natural reaction is to hide in a cave, work, work, work, and then polish, polish, polish, sure that no one will see your goof-ups and that you’ll still have a chance to unveil your masterpiece when you’re done. Hide away until your code is perfect.
- If you spend all of your time working alone, you’re increasing the risk of **unnecessary failure** and cheating your **potential for growth**.
- If you refuse to show anyone anything until the implementation is polished, you’re taking a huge gamble: 
    - It’s easy to make fundamental design mistakes early on.
    - You risk reinventing wheels.
- The more feedback you **solicit early on**, the more you lower the risk of an early misstep.
- Remember the tried-and-true mantra of ***“Fail early, fail fast, fail often.”***
- In Short, **Don’t Hide**:
    - Even though you might be afraid of someone stealing your idea or thinking you’re not intelligent, **you should be much more concerned about wasting huge swaths of your time toiling away on the wrong thing**.
- You are not your code.
- YOU ARE NOT YOUR CODE.
- **YOU ARE NOT YOUR CODE!**
    - You need to not only believe it yourself, but **get your coworkers to believe it, too**.
- The key to learning from your mistakes is to **document your failures** by performing a root-cause analysis and writing up a ***postmortem***.
- A good postmortem should include the following:
    - A brief summary of the event
    - A timeline of the event, from discovery through investigation to resolution
    - The primary cause of the event
    - Impact and damage assessment
    - A set of action items (with owners) to fix the problem immediately
    - A set of action items to prevent the event from happening again
    - Lessons learned

### Knowledge Sharing

- Sharing expertise across an organization is not an easy task. Without a strong culture of learning, challenges can emerge:
    - ***Lack of psychological safety***: An environment in which people are afraid to take risks or make mistakes in front of others because they fear being punished for it.
    - ***Information islands***: Knowledge fragmentation that occurs in different parts of an organization that don’t communicate  with one another or use shared resources.  In such an environment, each group develops its own way of doing things.
    - ***Single point of failure (SPOF)***: A bottleneck that occurs when critical information is available from only a single person.
    - ***All-or-nothing expertise***: A group of people that is split between people who know “everything” and novices, with little middle ground.  This problem often reinforces itself if experts always do everything themselves and don’t take the time to develop new experts through mentoring or documentation.
    - ***Parroting***: Mimicry without understanding. This is typically characterized by mindlessly copying patterns or code without understanding their purpose.
    - ***Haunted graveyards***: Places, often in code, that people avoid touching or changing because they are afraid that something might go wrong.
- An enormous part of learning is being able to try things and feeling safe to fail. In a healthy environment, people feel comfortable asking questions, being wrong, and learning new things.
- **Psychological safety is the foundation for fostering a knowledge-sharing environment.**
    - The most important way to achieve this safe and welcoming environment is for group interactions to **be cooperative**, not adversarial.
    - See the [Recurse Center’s social rules](https://oreil.ly/zGvAN "Recurse Center’s social rules")
- One of the biggest mistakes that beginners make is not to ask for help when they’re stuck. Don’t fall into this trap! Your coworkers are often the **best source of information**: leverage this valuable resource.
- There is no magical day when you suddenly always know exactly what to do in every situation—there’s always more to learn.
- Don’t be afraid to say *"I don’t know what that is; could you explain it?"*
- **Embrace not knowing things as an area of opportunity** rather than one to fear.
- You should always **be in an environment in which there’s something to learn**. If not, you stagnate.
- Seek out and **understand context**, especially for decisions that seem unusual.
- After you’ve understood the context and purpose of the code, consider whether your change **still makes sense**.
    - If it does, go ahead and make it.
    - If it doesn’t, document your reasoning for future readers.
- At a meta level, code is knowledge, so the very act of **writing code can be considered a form of knowledge transcription**.
- Code is read far more than it is written. 
- Code documentation is one way to share knowledge; clear documentation not only benefits consumers of the library, but also future maintainers.
- Similarly, implementation comments transmit knowledge across time: you’re writing these comments expressly for the sake of future readers.
- Code comments and documentation need to be actively maintained or they can quickly become out of date.

### How to Lead a Team

- The **engineering manager** is responsible for the performance, productivity, and happiness of every person on their team while still making sure that the needs of the business are met.
- The **tech lead** (TL) is responsible for the technical aspects of the product, including technology decisions and choices, architecture, priorities, velocity, and general project management.
- The TL will usually work hand in hand with the engineering manager to ensure that the team is adequately staffed for their product and that engineers are set to work on tasks that best match their skill sets and skill levels.
- On small teams, the default is often to have a TLM: a single person who can handle both the people and technical needs of their team.
- The job of TLM is a tricky one and often requires the TLM to learn how to balance individual work, delegation, and people management.
- If you’ve spent the majority of your career writing code, you typically end a day with something you can point to and say, “That’s what I did today.” But at the end of a busy day of *management*, you’ll usually find yourself thinking, “I didn’t do a damned thing today.”
    - As tempting as it might be to focus on purely the technical health of the team, **the social health of the team is just as important**.  

A collection of the patterns that you don’t want to follow if you want to be a successful manager:
- Hire Pushovers.
- Ignore Low Performers.
- Ignore Human Issues.
- Be Everyone’s Friend.
- Compromise the Hiring Bar.
- Treat Your Team Like Children.  

A collection of positive patterns for successful leadership and management:
- Lose the Ego: Apologize when you make a mistake. You need to sincerely mean it. Apologizing doesn’t cost money.
- Be a Zen Master.
- Be a Catalyst.
- Remove Roadblocks.
- Be a Teacher and a Mentor.
- Set Clear Goals.
- Be Honest.
- Track Happiness.  

A good simple way to track your team’s happiness is to ask the team member at the end of each one-on-one meeting, “What do you need?” This simple question is a great way to wrap up and make sure each team member has what they need to be productive and happy.

### Leading at scale
- Delegation is really difficult to learn.  It goes against all our instincts for efficiency and achievement.  
That difficulty is the reason for the adage, “If you want something done right, do it yourself.”  

Here’s a simple test: think about the last vacation you took that was at least a week long.  
Did you keep checking your work email?  
Ask yourself why. Will things fall apart if you don’t pay attention? If so, you have very likely made yourself an SPOF (Single Point Of Failure).  
**You need to fix that**.  

Before you carry out a task be mindful and stop yourself. Ask this critical question: Am I really the only one who can do this work?  
Unless the task is truly time sensitive and on fire, bite the bullet and assign the work to someone else.  

- A common mistake is to put a team in charge of a specific product rather than a general problem:
    - A product is a ***solution*** to a problem.
- Your most precious resource is your limited pool of time, attention, and energy.
- Divide your task list into three groups:
    - The bottom 20% are probably neither urgent nor important and very easy to delete or ignore.
    - There’s a middle 60%, which might contain some bits of urgency or importance, but it’s a mixed bag.
    - At the top, there’s 20% of things that are absolutely, critically important.

## Processes
### Style Guides and rules
At Google, to manage their codebase, they maintain a [set of style guides](https://google.github.io/styleguide/) that define their rules.  
- **Rules are laws**. They are not just suggestions or recommendations, but **strict, mandatory laws**.  
- As an organization grows, the established rules and guidelines shape the **common vocabulary of coding**.  
    - A common vocabulary allows engineers to concentrate on **what their code needs to say** rather than how they’re saying it.
- Principles that guide the development of their rules:
    - **Rules must pull their weight**:
        - Not everything should go into a style guide.
        - With too many rules, not only will it become harder for engineers to remember all relevant rules, but it also becomes harder for new engineers to learn their way.
    - **Optimize for the reader**:
        - Given the passage of time, **our code will be read far more frequently than it is written**.
        - They value **“simple to read”** over “simple to write.” 
    - **Be consistent**:
        - Consistency is what enables any engineer to jump into an unfamiliar part of the codebase and get to work fairly quickly.
        - A local project can have its unique personality, but its **tools** are the same, its **techniques** are the same, its **libraries** are the same, and it all **Just Works**.
        - Hierarchy of consistency: “Be consistent” starts **locally**, where the norms within a given file precede those of a given team, which precede those of the larger project, which precede those of the overall codebase.
    - **Avoid error-prone and surprising constructs**:
        - Their style guides restrict the use of some of the more surprising, unusual, or tricky constructs in the languages that they use.
        - They place higher value on **simplified, straightforward code** that is easier to **understand** and **maintain**.
    - **Concede to practicalities when necessary**:
        - When necessary, they permit concessions to optimizations and practicalities that might otherwise conflict with their rules.
        - **Documenting the reasoning** behind a given decision gives them the advantage of being able to recognize when things need to change.
- **Comments**:
    - **Documentation comments** (the block comments prepended to a given file, class, or function) describe the design or intent of the code that follows.
    - **Implementation comments** (the comments interspersed throughout the code itself) justify or highlight non-obvious choices, explain tricky bits, and underscore important parts of the code.
They have style guide rules covering both types of comments, requiring engineers to **provide the explanations another engineer might be looking for** when reading through the code.
- Google 101:
    Software engineers come in to a new project or codebase with knowledge of the programming language they are going to be using, but lacking the knowledge of how the programming language is used within Google. To bridge this gap, they maintain a series of *language@Google 101* courses for each of the primary programming languages in use.
    
### Code Review
At Google, code reviews take place before a change can be committed to the codebase; this stage is also known as a *precommit review*.  

The primary end goal of a code review is to get another engineer to consent to the change, which they denote by tagging the change as “looks good to me” (**LGTM**).  

At Google, **only one LGTM is required by default**.  

Their code review tool is called "Critique".  

- **A typical code review at Google**:
    1. A user writes a change to the codebase in their workspace.
        - This *author* then creates a snapshot of the change: a patch and corresponding description that are uploaded to the code review tool.
        -  This change produces a *diff* against the codebase, which is used to evaluate what code has changed.
    2. The *author* can use this initial patch to apply automated review comments or do self-review.
        - When the author is satisfied with the diff of the change, they mail the change to one or more *reviewers*.
    3. Reviewers open the change in the code review tool and post comments on the diff.
    4. The author modifies the change and uploads new snapshots based on the feedback and then replies back to the reviewers.
    5. After the reviewers are happy with the latest state of the change, they agree to the change and accept it by marking it as "looks good to me" (LGTM).
    6. After a change is marked LGTM, the author is allowed to commit the change to the codebase.

- There are three aspects of review  that require “approval” for any given change at Google:
    - A **correctness** and **comprehension** check from another engineer that the code is **appropriate** and does **what the author claims it does**.
    - Approval from one of the code owners that the code is appropriate for this particular part of the codebase.
    - Approval that the code conforms to the language’s style and  best practices, checking whether the code is written in the manner they expect.
Most reviews have **one person assuming all three roles**, which speeds up the process quite a bit.  
Importantly, **the author can also assume the latter two roles**, needing **only an LGTM** from another engineer to check code into their own codebase.  

A well-designed code review process and a culture of taking code review seriously provides the following benefits:
- Checks code correctness
- Ensures the code change is comprehensible to other engineers
- Enforces consistency across the codebase
- Psychologically promotes team ownership
- Enables knowledge sharing
- Provides a historical record of the code review itself  

Many of these benefits are **critical** to a software organization **over time**, and many of them are **beneficial** to not only the **author** but also the **reviewers**.  

An obvious benefit of code review is that it **allows a reviewer to check the “correctness” of the code change**.  

Having another set of eyes look over a change helps ensure that the change **does what was intended**.  

Unlike the deference reviewers should give authors regarding design decisions, it’s often useful to treat questions on code comprehension using the maxim **“the customer is always right.”**  

**Any questions you get now will be multiplied many-fold over time**.  

***Remember that you are not your code, and that this change you propose is not “yours” but the team’s.***
> It is human nature to be proud of one’s craft and to be reluctant to open up one’s code to criticism by others.  
> It is also natural to be somewhat reticent to welcome critical feedback about code that one writes.  
> The code review process provides a mechanism to **mitigate what might otherwise be an emotionally charged interaction**.  

- Code Review Best Practices:
    - **Be Polite and Professional**
        - Reviewer:
            - Reviewers should defer to authors on particular approaches and only point out alternatives if the author’s approach **is deficient**.
            - It’s better to **ask questions** on why something was done the way it was before assuming that approach is wrong.
        - Author:
            - Be receptive to questions on your approach, and be prepared to **explain why you did things in certain ways**.
            - Remember that part of the responsibility of an author is to make sure this code is **understandable** and **maintainable** for the future.
            - It’s important to treat each reviewer comment within a code review as a **TODO item**.
            - If you disagree with a reviewer’s comment, **let them know**, and let them know why and don’t mark a comment as resolved until each side has had a chance to offer alternatives.
            - If an author doesn’t agree with a reviewer, the author should offer an alternative and ask the reviewer to [PTAL (please take another look)](https://en.wiktionary.org/wiki/PTAL).
    - **Write Small Changes**
        - A code review should ideally be **easy to digest** and **focus on a single issue**.
        - Changes should generally be limited to about **200 lines of code**.
    - **Write Good Change Descriptions**
    - **Keep Reviewers to a Minimum**
    - **Automate Where Possible**
        - Opportunities to automate mechanical human tasks should be explored (Static Analysis, etc...).
        - Automation is critical for scaling the process.
- Types of Code Reviews:
    - **Greenfield reviews** (new code and and new functionnality)
    - **Behavioral Changes, Improvements, and Optimizations**
    - **Bug Fixes and Rollbacks**
    - **Refactorings and Large-Scale Changes**  

### Documentation  
Documentation refer to standalone documents and code comments.  

Documentation helps **answer questions** like these :
- Why were these **design decisions** made?
- Why did we implement this code in **this manner**?
- Why did ***I*** implement this code in this manner, if you’re looking at your own code two years later?  

Documentation provides the following **benefits**:
- Writing documentation is one of the **surest ways** to figure out if your API makes sense.
- It provides a **road map** for maintenance and a historical record.
- It makes your code look **more professional** and drive traffic. 
- It will prompt **fewer questions** from other users.

Documentation is generally considered “poor” by engineers for the following reasons:
- Documentation generally requires **more effort up front** and doesn’t provide **clear benefits** to an author until later.
- Engineers often view writing as a **separate skill** than that of programming.
- Some engineers don’t feel like they are **capable writers**.
- Writing documentation is often **more difficult** because of limited tools support or integration into the developer workflow.
- Documentation is viewed as an **extra burden** rather than something that will make maintenance of their existing code easier.  

Documentation is like code (see *[Docs as Code](https://www.writethedocs.org/guide/docs-as-code/)*)

Like a programming language, documentation has **rules**, a particular **syntax**, and **style** decisions, often to accomplish a similar purpose as that within code:
- Enforce consistency
- Improve clarity
- Avoid (comprehension) errors.  

**A good documentation should**:
- Have internal policies or rules to be followed
- Be placed under source control
- Have clear ownership responsible for maintaining the docs
- Undergo reviews for changes
- Have issues tracked, as bugs are tracked in code
- Be periodically evaluated
- If possible, be measured for aspects such as accuracy, freshness, etc.  

**Know your audience**:
- One of the most important mistakes that engineers make when writing documentation is to write only for themselves.  
- Before you begin writing, you should (formally or informally) identify the audience(s) your documents need to satisfy.  
- Always try to identify a primary audience and write to that audience.  

WHO, WHAT, WHEN, WHERE, and WHY:
- **WHO** identifies the **audience**.
- **WHAT** identifies the **purpose of this document**: “This document is a tutorial designed to start a Frobber server in a test environment.”
- **WHEN** identifies when this document was **created**, **reviewed**, or **updated**.
- **WHERE** is often implicit as well, but decide where the document **should live**.
- **WHY** sets up the **purpose** for the document.  

**Documentation Types**:
- Reference documentation, including code comments
- Design documents
- Tutorials
- Conceptual documentation
- Landing pages

**Design Docs**:  

Most teams at Google require an approved design document **before starting work** on any major project.  

Some teams at Google require such design documents to be **discussed and debated** at specific team meetings.  

A good design document should cover the **goals of the design**, its **implementation strategy**, and propose **key design decisions** with an emphasis on their **individual trade-offs**.  

The best design documents suggest **design goals** and cover **alternative designs**, denoting their **strong** and **weak** points.  

## Tests
### Testing Overview
**Benefits of Testing Code**:
- Less debugging
- Increased confidence in changes
- Improved documentation
- Simpler reviews
- Thoughtful design
- Fast, high-quality releases  

As the first clients of your code, a test can tell you much about your **design choices**.  

As a codebase grows, the test suite will begin to face challenges like **instability** and **slowness**.  

If testing becomes a productivity sink, constantly inducing toil and uncertainty, engineers will lose trust and begin to find workarounds.  

**A bad test suite can be worse than no test suite at all.**

> Our experience suggests that as you approach 1% flakiness, the tests begin to lose value.  

At Google, they have three sizes of tests:
- **Small Tests**:
    - Must run in a **single process**.
    - At Google, they restrict this even further to say that the small tests must run on a **single thread**.
    - They aren’t allowed to sleep, **perform I/O operations** or make any other blocking calls.
- **Medium Tests**:
    - Can span **multiple processes**, use threads and **can make blocking calls**, including **network calls**, to localhost.
- **Large Tests**:
    - Large tests **remove the localhost restriction** imposed on medium tests, allowing the test and the system being tested to span across multiple machines.  

Placing restrictions on small tests makes **speed** and **determinism** much easier to achieve.  

Larger tests are saved for only the most **complex** and **difficult** testing scenarios.  

At Google, they tend to aim to have a mix of around:
- 80% of small tests
- 15% of medium tests
- 5% of large tests  

**The Beyoncé Rule**: *“If you liked it, then you shoulda put a test on it.”*  

**Code coverage** is a measure of which lines of feature code are exercised by which tests.  

If you have 100 lines of code and your tests execute 90 of them, you have 90% code coverage.  

Code coverage only measures that a line was invoked, **not what happened as a result**.  

### Unit Testing  
Unit tests are usually **small** in size, but this isn’t always the case.  

After preventing bugs, the most important purpose of a test is to **improve productivity**.  

They tend to be **easy to write** at the same time as the code they’re testing.  

They tend to make it **easy to understand** what’s wrong when they fail.  

> A  test is complete when its body contains all of the information a reader needs in order to **understand** how it arrives at its result.

> A test is concise when it contains **no other distracting or irrelevant information**.

It can often be worth violating the [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle if it leads to **clearer tests**.  

**Test Behaviors, Not Methods**:
- Rather than writing a test for each method, **write a test for each behavior**.
- Behaviors can often be expressed using the words **"given,"** **"when,"** and **"then"**:
    - *“**Given** that a bank  account is empty, **when** attempting to withdraw money from it, **then** the transaction is rejected."*

- The mapping between methods and behaviors is **many-to-many**:
    - Most nontrivial methods implement **multiple behaviors**, and some behaviors rely on the interaction of **multiple methods**.  

**Don't put logic in tests**  

### Test Doubles
A test double is an object or function that can **stand in for a real implementation in a test**, similar to how a stunt double can stand in for an actor in a movie.  

For example: An in-memory database.  

Techniques for using test doubles:
- *Faking* (for example, an in-memory database)
- *Stubbing* (the process of giving behavior to a function that otherwise has no behavior on its own)
- *Interacting Testing* (how a function is called without actually calling the implementation of the function)  

A fake is often the ideal solution if a real implementation can’t be used in a test.  

### Larger Testing
Large tests provide more confidence that the **overall system** works as intended.  

- They may be **slow** (Google have tests that run for multiple hours or even days).
- They may be **nonhermetic**.
- They may be **nondeterministic**.  

## Various Notes

### Depreciation  

- Software systems have continuing maintenance costs that should be weighed **against** the costs of removing them.  

- Removing things is often more difficult than building them to begin with because existing users are often **using the system beyond its original design**.  

> Unlike with most of the other topics we have discussed in this book, Google is still learning how best to deprecate and remove software systems.

### Version Control and Branch Management  

-  A VCS (Version Control System) helps coordinate the activities of teams by allowing multiple developers to work on the same set of files **simultaneously**.  

- **Version control allows us to scale up teams and organizations**.  

- Google rely on an in-house-developed centralized VCS called **Piper**, built to run as a **distributed microservice** in their production environment.  

- **Consistency has a profound importance at all levels in an organization**.  

- If every project in our organization has the same secrecy, legal, privacy, and security requirements, a true **monorep** is a fine way to go.  

- Complex technology doesn’t need to be used in a complex fashion: **keeping branch policies simple generally leads to better engineering outcomes**  

### Dependency management  

 External dependencies are those on artifacts that are built and stored outside of the build system.  

 One of the biggest differences between external and internal dependencies is that external dependencies have versions, and those versions exist independently of the project’s source code.  

 **Considerations When Importing**:
 - Does the project have tests that you can run?
 - Do those tests pass?
 - Who is providing that dependency?
 - What sort of compatibility is the project aspiring to?
 - Does the project detail what sort of usage is expected to be supported?
 - How popular is the project?
 - How long will we be depending on this project?
 - How often does the project make breaking changes?  

**Add to this a short selection of internally focused questions**:
 - How complicated would it be to implement that functionality within our organization?
 - What incentives will we have to keep this dependency up to date?
 - Who will perform an upgrade?
 - How difficult do we expect it to be to perform an upgrade?  

 > We also need to be aware of the **impact of time**: all software has bugs, some of those will be security critical, and some fraction of our dependencies will therefore be critical to **update over a long enough period of time**.  

 ### Continuous integration  
The fundamental goal of *Continuous Integration* (CI) is to **automatically catch problematic changes as early as possible**.  

It is natural to conceptualize CI in terms of **testing** because the two are **tightly coupled**.  

From a testing perspective, CI is a paradigm  to inform the following:
- *Which* tests to run when in the development/release workflow.
- *How* to compose the system under test (SUT) at each point.  

 **The cost of a bug grows almost exponentially the later it is caught**.  

 ***Canarying***—or deploying to a small percentage of production first—can **help minimize issues** that do make it to production, with a subset-of-production initial feedback loop preceding all-of-production.  
 However, canarying can cause problems, too, particularly around compatibility between deployments when multiple versions are deployed at once.  

 ### Continuous delivery
 Continuous Delivery is a software development discipline where you **build software in such a way that the software can be released to production at any time**.  

 From Eric Raymond’s [The Cathedral and the Bazaar](http://www.catb.org/~esr/writings/cathedral-bazaar/) to Eric Reis’ [The Lean Startup](http://theleanstartup.com/book), the key to any organization’s long-term success has always been in its **ability to get ideas executed and into users’ hands as quickly as possible and reacting quickly to their feedback**.  

 Martin Fowler, in his book [Continuous Delivery](https://martinfowler.com/bliki/ContinuousDelivery.html) (aka CD), points out that
 > “The biggest risk to any software effort is that you end up building something that isn’t useful.  
 **The earlier and more frequently you get working software in front of real users, the quicker you get feedback to find out how valuable it really is**.”  

 Over time, smaller batches of changes result in higher quality.  

 > “One of our codebases, YouTube, is a large, monolithic Python application. The release process is laborious, with Build Cops, release managers, and other volunteers. Almost every release has multiple cherry-picked changes and respins. There is also a 50-hour manual regression testing cycle run by a remote QA team on every release.”  

 **Ship only what gets used**  

 *Bloat* is an unfortunate side effect of most software development life cycles, and **the more successful a product becomes, the more *bloated* its code base typically becomes**.  
 One downside of a speedy, efficient release train is that this bloat is often magnified.  
 It can manifest in challenges to the product team and even to the users: This can mean the user’s device pays the cost in terms of space, download, and data costs, **even for features they never use**, whereas developers pay the cost of **slower builds, complex deployments, and rare bugs**.  

 **Ship only what gets used**: Monitor the cost and value of any feature in the wild to know whether it’s still **relevant** and delivering sufficient **user value**.  

 **Faster is safer**: Ship **early** and **often** and in **small batches** to reduce the risk of each release and to minimize time to market.