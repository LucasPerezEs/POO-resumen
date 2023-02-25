# What Is The Point of Test Driven Development? 

### Software Development as a Learning Process
Everyone involved in a software project has to learn as it progresses. They all know there will be changes, they just don’t know what
changes. 
They **need a process that will help them cope with uncertainty** as their experience grows—**to anticipate unanticipated changes**.

### Feedback Is the Fundamental Tool
A team needs **repeated cycles of activity**. In each cycle it adds new features and gets feedback about the quantity and quality of the work already done.  

**Deploying completed work** to some kind of environment **at each cycle is _critical_**. Every time a team deploys, its members have an opportunity to measure how much progress they’re really making, detect and correct any errors, and adapt the current plan in response to what they’ve learned. Without deployment, the feedback is not complete.  

In our work, we apply feedback cycles at every level of development, **organizing projects as a system of _nested loops_** ranging from seconds to months, such as:
pair programming, unit tests, acceptance tests, daily meetings, iterations, releases, and so on.  
The inner loops are more focused on the technical detail, while the outer loops are more focused on the organization and the team.

### Practices That Support Change
We’ve found that we need two technical foundations if we want to grow a system reliably and to cope with the unanticipated changes that always happen: 

- **Constant testing to catch regression errors**, so we can add new features without breaking existing ones. We must automate testing as much as we can to reduce the costs of building, deploying, and modifying versions of the system.
- **Keep the code as simple as possible**, so it’s easier to understand and modify. Simplicity takes effort, so we constantly refactor our code as we work with it.

The catch is that few developers enjoy testing their code.

Test-Driven Development (TDD) turns this situation on its head. We write our tests before we write the code. Instead of just using testing to verify our work after it’s done, **TDD turns testing into a design activity**.  

We find that the effort of writing a test first also gives us **rapid feedback about the quality of our design ideas**. We can **build up a safety net of automated regression tests** that give us the confidence to make changes.

### Test-Driven Development in a Nutshell
> Write a test; write some code to get it working; refactor the code to be as simple an implementation of the tested features as possible. Repeat.

As we develop the system, **we use TDD to give us feedback on the quality of both its implementation** (“Does it work?”) **and design** (“Is it well structured?”).

 Writing tests:
 - Makes us clarify the acceptance criteria for the next piece of work
 - encourages us to write loosely coupled components, so they can easily be tested in isolation and, at higher levels, combined together 
 - adds an executable description of what the code does 
 - adds to a complete regression suite

whereas running tests:
-  detects errors while the context is fresh in our mind
-  lets us know when we’ve done enough, discouraging “gold plating” and unnecessary features

### The Golden Rule of Test-Driven Development
> ***Never write new functionality without a failing test.***

### The Bigger Picture
When we’re implementing a feature, we start by writing an ***acceptance test***, which exercises the functionality we want to build. While it’s failing, an acceptance test demonstrates that the system does not yet implement that feature; when it passes, we’re done. 
Underneath the acceptance test, we follow the unit level test/implement/refactor cycle to develop the feature; 

![image](https://user-images.githubusercontent.com/86437352/221301753-d9460bce-aafe-4797-9e11-997fc71e97e0.png)

### Testing End-to-End
An acceptance test should exercise the system end-to-end without directly calling its internal code. An **end-to-end test interacts with the system only from the outside: through its user interface**, by sending messages as if from third-party systems. We try to avoid acceptance tests that just exercise the internal objects of the system.

### Levels of Testing
We build a hierarchy of tests that correspond to some of the nested feedback loops we described above:

- **Acceptance**: Does the whole system work?
- **Integration**: Does our code work against code we can't change?
- **Unit**: Do our objects do the right thing, are they convenient to work with?

We use ***“acceptance tests”*** to help us understand and agree on what we are going to build next. We also use them to make sure that we haven’t broken any existing features as we continue developing.  

We use the term ***"integration tests"*** to refer to the tests that check how some of our code works with code from outside the team that we can’t change.

### External and Internal Quality

We can make a distinction between external and internal quality: 
> ***External quality:***  How well the system **meets the needs of its customers and users** (is it functional, reliable, available, responsive, etc.)
> ***Internal quality:***  How well it **meets the needs of its developers and administrators** (is it easy to understand, easy to change, etc.).

The point of maintaining internal quality is to allow us to modify the system’s behavior safely and predictably, because it minimizes the risk that a change will force major rework.

Running end-to-end tests tells us about the external quality of our system, andwriting them tells us something about how well we (the whole team) understand the domain, but **end-to-end tests don’t tell us how well we’ve written the code**.

Writing unit tests gives us a lot of feedback about the quality of our code, and running them tells us that we haven’t broken any classes—but, again, **unit tests
don’t give us enough confidence that the system as a whole works**.

Integration tests fall somewhere in the middle

![image](https://user-images.githubusercontent.com/86437352/221381299-d82b948d-98b6-4fa5-8b14-6b6d1878190d.png)

Thorough unit testing helps us improve the internal quality because it needs to create the object, provide its dependencies, interact with it, and check that it behaved as expected. So, for a class to be easy to unittest, the class must have explicit dependencies that can easily be substituted and clear responsibilities that can easily be invoked and verified. That means that the code must be ***loosely coupled*** and ***highly cohesive***.
