## Getter Eradicator Resumen
I've often come across **people who tell you to avoid having getting methods on classes**, treating such things as a violation of encapsulation. There's some sense to this argument, and I certainly suggest that you shouldn't write accessors until you really need them, but it also brings in the danger of **missing the point of encapsulation**.  
For me, the **point of encapsulation** isn't really about hiding the data, but in **hiding design decisions**, particularly in areas where those decisions may have to change.  


### Objects need to exchange data
It's still common to see procedures that pull data out of an object to do something, when that behavior would better fit in the object itself - a violation of the pragmatic programmers principle of "Tell Don't Ask". You can only do this kind of procedural programming if you have getters, so telling people to get rid of getters helps push them to move behavior into the right place. **I fear that just telling people to avoid getters is a rather blunt tool**. There are too many times when **objects do need to collaborate by exchanging data, which leads to genuine needs for getters**.  

### Better rules of thumbs
If we're looking for a simple rule of thumb, the one I prefer is one that I first heard from Kent Beck, which is to always **beware of cases where some code invokes more than one method on the same object.**

Another good warning sign of trouble is the Data Class - **a class that has only fields and accessors**. That's almost **always a sign of trouble** because it's devoid of behavior. Look for who uses the data and try to see if some of this behavior can be moved into the object. 

A good rule of thumb is that **things that change together should be together**. Data and the behavior that uses it often change together, but often you see other groupings that matter more.
