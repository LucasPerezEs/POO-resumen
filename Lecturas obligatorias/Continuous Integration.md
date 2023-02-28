## Continuous Integration

- Software development practice where **members of a team integrate their work frequently**, usually each person integrates at least daily - leading to multiple integrations per day. 

- **Each integration is verified by an automated build** (including test) to detect integration errors as quickly as possible.

- Many teams find that this approach leads to **significantly reduced integration problems** and allows a team to **develop cohesive software more rapidly**.


### Building a Feature with Continuous Integration
1) I begin by taking a copy of the current integrated source onto my local development machine. (hacer pull)
2) Now I take my working copy and do whatever I need to do to complete my task. This will consist of both altering the production code, and also adding or changing automated tests. 
3) Once I'm done (and usually at various points when I'm working) I carry out an automated build on my development machine.
4) With a good build, I can then think about committing my changes into the repository. Other people may have made changes to the mainline before I get chance to commit, so I first update my working copy with their changes and rebuild. If their changes clash with my changes, it will manifest as a failure. In this case it's my responsibility to fix this and repeat until I can build a working copy that is properly synchronized with the mainline.
5) However my commit doesn't finish my work. At this point we build again, but this time on an integration machine based on the mainline code. Only when this build succeeds can we say that my changes are done.

The result of doing this is that there is a stable piece of software that works properly and contains few bugs.

### Practices of Continuous Integration

- **Maintain a Single Source Repository**:    Although many teams use repositories a common mistake I see is that they don't put everything in the repository. The basic rule of thumb is that you should be able to walk up to the project with a virgin machine, do a checkout, and be able to fully build the system.

- **Automate the Build**:     Asking people to type in strange commands or clicking through dialog boxes is a waste of time and a breeding ground for mistakes.

- **Make Your Build Self-Testing**:     A good way to catch bugs more quickly and efficiently is to include automated tests in the build process. Testing isn't perfect, of course, but it can catch a lot of bugs - enough to be useful. TDD and XP are not necessary for the purposes of Continuous Integration, where we have the weaker requirement of self-testing code. 

- **Everyone Commits To the Mainline Every Day**:     The more frequently you commit, the less places you have to look for conflict errors, and the more rapidly you fix conflicts.

- **Every Commit Should Build the Mainline on an Integration Machine**:  Using daily commits, a team gets frequent tested builds. In practice, however, things still do go wrong. As a result you should ensure that regular builds happen on an integration machine and only if this integration build succeeds should the commit be considered to be done. There are two main ways I've seen to ensure this: using a manual build or a continuous integration server.

- **Fix Broken Builds Immediately**: A key part of doing a continuous build is that if the mainline build fails, it needs to be fixed right away. The whole point of working with CI is that you're always developing on a known stable base.

- **Keep the Build Fast**: The whole point of Continuous Integration is to provide rapid feedback.

- **Test in a Clone of the Production Environment**: The point of testing is to flush out, under controlled conditions, any problem that the system will have in production. If you test in a different environment, every difference results in a risk that what happens under test won't happen in production. As a result you want to set up your test environment to be as exact a mimic of your production environment as possible.

- **Make it Easy for Anyone to Get the Latest Executable**: Anyone involved with a software project should be able to get the latest executable and be able to run it.

- **Everyone can see what's happening**: Continuous Integration is all about communication, so you want to ensure that everyone can easily see the state of the system and the changes that have been made to it.

- **Automate Deployment**: To do Continuous Integration you need multiple environments, one to run commit tests, one or more to run secondary tests. It's important to have scripts that will allow you to deploy the application into any environment easily.   


### Benefits of Continuous Integration
 
- **Reduced risk**: There's no long integration, you completely eliminate the blind spot. At all times you know where you are, what works, what doesn't, the outstanding bugs you have in your system.

- **Less Bugs**: Continuous Integrations doesn't get rid of bugs, but it does make them dramatically easier to find and remove. Bugs are also cumulative. The more bugs you have, the harder it is to remove each one. As a result projects with Continuous Integration tend to have dramatically less bugs, both in production and in process.

- **Frequent Deployment**: Frequent deployment is valuable because it allows your users to get new features more rapidly, to give more rapid feedback on those features, and generally become more collaborative in the development cycle.
