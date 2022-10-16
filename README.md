# Software engineering at Google

My arbitrary selection of quotes and notes on the book [Software engineering at Google](https://abseil.io/resources/swe-book "Software engineering at Google").  

It's a work in progress, I haven't finished reading it yet.

- [Management](#management)
    - [What Is Software Engineering?](#what-is-software-engineering)
    - [How to work well on teams](#how-to-work-well-on-teams)
    - [Knowledge Sharing](#knowledge-sharing)
    - [How to Lead a Team](#how-to-lead-a-team)
    - [Leading at scale](#leading-at-scale)
- Processes *(Work in progress)*
- Tests *(Work in progress)*
- Various notes (Depreciation, Version Control, Code Search) *(Work in progress)*

## Management
### What Is Software Engineering?

- Software engineering is programming integrated over time.
- We might need to delineate between **programming** tasks (development) and **software engineering** tasks (development, modification, maintenance).
- Programming is about producing code. Software engineering extends that to include the maintenance of that code for its useful life span.
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