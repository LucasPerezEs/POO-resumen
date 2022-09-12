## The Art of Enbugging Resumen
**Referring to errors as “bugs”** lets a programmer avoid direct blame, but it **does several disservices** in the process.  

### "Bugs somehow spontaneously appear in source code"
**They do not**. We put those errors in the code ourselves (*we are enbugging the code*).  
But it’s actually more insidious than that. We rarely put bugs in directly; instead, we might set up conditions that will trick us into putting in bugs later.  
How can we prevent this? One of the best ways to keep future bugs out is to **maintain a proper “separation of concerns”**—that is, design the code so that classes and modules have clear, well-defined, and isolated responsibilities and well-understood semantics.  
The fundamental goal is to write ***shy code***—code that doesn’t reveal too much of itself to anyone else and doesn’t talk to others any more than is necessary.

### Tell, don’t ask
>  We want to tell objects what to do, not ask them for their state.

A distinction of OO code is the idea of issuing a command to some entity to get something done. Procedural code tends to get information and then make decisions based on that information. **OO code tells objects to do things**. We explicitly **do not want to query an object about its state, make a decision, and then tell the object what to do**. That starts to sound a bit like the gossipy neighbor—and **not something that shy code should do**.  

As the caller, you should not make decisions based on the called object’s state and then change the object’s state, it violates its encapsulation and provides a fertile breeding ground for bugs.

### Commands and Querys
“Tell, Don’t Ask” is easier if you mentally categorize each of your functions and methods as either a command or a query.
A **command** will likely change the object’s state and might also return some useful value as a convenience.  
A **query** just gives you information about the object’s state—and does not modify the object’s externally visible state.  

**Advantages**:
- Command-query separation **keeps code shy**; the caller doesn’t know too much about how its command will be performed.
- Implementation details are free to change with less chance of affecting the caller.
- Because the query methods are known to be side effect free, we can use them freely in unit tests and call them from assertions or from the debugger.

### Law of Demeter for Functions 
The more objects you talk to, the greater your risk of breaking when one of those objects changes.  So not only do you want to **say as little as possible to other objects**, you also want to **talk to as few other objects as possible**.  

This good idea suggests that an object should only call:
- Itself
- Any parameters that were passed in to the method
- Any objects it created
- Any directly held component objects

Example: 
Instead of `my_television.front_panel.switches.power.on();` it's better to just tell the television what to do: `my_television.power_up();`

Now the **caller doesn’t need knowledge of my_television’s internal object model**. This higher-level call sounds more like a user requirement and less like an implementation detail.

The **disadvantage** of this approach is that you end up writing **many small wrapper methods** that do very little but **delegate** container traversal and such. The cost trade-off is inefficiency versus **higher-class coupling**. In the long run, higher-class coupling is simply unacceptable, as that **increases the odds that any change you make will break something somewhere else**.  
But for those occasions when speed is primordial and high coupling is acceptable, couple it to the hilt!
