# Resumen Lecturas obligatorias

## Design Principles Behind Smalltalk

> **Uniform Metaphor**: *A language should be designed around a powerful metaphor that can be uniformly applied in all areas.*

The purpose of the Smalltalk project is to provide computer support for the creative spirit in everyone. We have chosen to concentrate on two principle areas of research: a language of description (programming language) that serves as an interface between the models in the human mind and those in computing hardware, and a language of interaction (user interface) that matches the human communication system to that of the computer. 
In this article, I present some of the general principles we have observed in the course of our work. While the presentation frequently touches on Smalltalk "motherhood", the principles themselves are more general and should prove useful in evaluating other systems and in guiding future work.

>***Personal Mastery***: *"If a system is to serve the creative spirit, it must be entirely comprehensible to a single individual.*  

The point here is that the human potential manifests itself in individuals. To realize this potential, we must provide a medium that can be mastered by a single individual. Any barrier that exists between the user and some part of the system will eventually be a barrier to creative expression.

Any part of the system that cannot be changed or that is not sufficiently general is a likely source of impediment. We can thus infer a general principle of design:

>***Good Design***: *A system should be built with a minimum set of unchangeable parts; those parts should be as general as possible; and all parts of the system should be held in a uniform framework.*

### Language
In designing a language for use with computers, we do not have to look far to find helpful hints.  
The mechanisms of human thought and communication have been engineered for millions of years,  since we must work with this design for the next million years, it will save time if we make our computer models compatible with the mind, rather that the other way around.

>***Purpose of Language***: *To provide a framework for communication.*

>***Scope***: *The design of a language for using computers must deal with internal models, external media, and the interaction between these in both the human and the computer.*

![imagen](https://www.cs.virginia.edu/~evans/cs655/readings/smalltalk_files/dpbs_figure1.gif)  
**Figure 1**: The scope of language design. Communication between two people (or between one person and a computer) includes communication on two levels. Explicit communication includes the information that is transmitted in a given message. Implicit communication includes the relevant assumptions common to the two beings.

### Communicating Objects

>***Objects***: *A computer language should support the concept of "object" and provide a uniform means for referring to the objects in its universe.*

If one wishes to participate, literally to take a part, in the universe, one must draw distinctions. In so doing one identifies an object in the universe, and simultaneously all the rest becomes not-that-object.   
Every time you want to talk about "that chair over there", you must repeat the entire processes of distinguishing that chair. This is where the **act of reference** comes in: we can associate a unique identifier with an object, and, from that time on, only the mention of that identifier is necessary to refer to the original object.  
We have said that a computer system should provide models that are compatible with those in the mind. Therefore:

> ***Storage Management***: *To be truly "object-oriented", a computer system must provide automatic storage management.*

The Smalltalk storage manager provides an object-oriented model of memory for the entire system. Uniform reference is achieved simply by associating a unique integer with every object in the system.  
Objects are created when expressions are evaluated, and they can be passed around by uniform reference. When all references to an object have disappeared from the system, the object itself vanishes, and its storage is reclaimed.  
If a language is sprinkled with statements that relate to the management of storage, then their internal model is not well matched to that of humans.

> ***Messages***: *Computing should be viewed as an intrinsic capability of objects that can be uniformly invoked by sending messages.*

Just as programs get messy if object storage is dealt with explicitly, control in the system becomes complicated if processing is performed extrinsically.  
Smalltalk provides a clean solution: it sends the name of the desired operation, along with any arguments, as a message to the number, with the understanding that the receiver knows best how to carry out the desired operation. 

### Organization
A uniform metaphor provides a framework in which complex systems can be built. Several related organizational principles contribute to the successful management of complexity.
> ***Modularity***: *No component in a complex system should depend on the internal details of any other component.*

The message-sending metaphor provides modularity by decoupling the intent of a message (embodied in its name) from the method used by the recipient to carry out the intent.

>***Classification***: *A language must provide a means for classifying similar objects, and for adding new classes of objects on equal footing with the kernel classes of the system.*

 The complexity of a system can often be reduced by grouping similar components. Such grouping is achieved through data typing in conventional programming languages, and through classes in Smalltalk.
