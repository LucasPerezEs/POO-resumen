## What's a Model For? Resumen (UML)
> What exactly is the UML for? Why do we use it, and if we don’t why should we?

### Costs and Value of creating a UML
It’s important to recognize that creating a UML diagram involves a cost, and a **UML model is not something that fundamentally matters to a customer**. Customers want software.
that works. **If the model improves the quality or reduces the cost, then the model has value**. But the model has no value on its own.  
The **value** that a model provides is fundamentally about **giving the user a greater understanding of something than the software itself**.

### Over detailing
I’ll start by looking at the simple transformation from text to graphics, leaving all the details in. In this approach you take everything you can say in text and put it in the model
- This takes a lot of work; doing this level of detail with model and source code takes too much time to be worthwhile, unless you have tools that automate the task.
- You can gain in structural relationships (such as data structures), but with control flow you often lose clarity.

### Highlighting
You can use a model to highlight just the important parts of the system, so that you can understand the key structures that make the software work first, and then you’re in a better position to investigate all the details. I prefer to think of this style as a ***Skeletal Model***. It shows you the bones of the system, which can be
quite detailed. 

### Advantages of a skeletal model:
- When trying to understand a model, it's **easier to figure out where to start**.
- Similarly, when creating a model before building the system, the key decisions are in those important details.
- A skeletal model is **easier to maintain** than a fully-fleshed one. Important details change less often. And the skeletal model is more useful, so people are more inclined to keep it up to date. 

The crux is that **a model is either fully-fleshed or skeletal, it can’t be both**. You either include all details, or you decide to leave something out. As soon as you leave something out, you are going down the skeleton path, even though your skeleton may look less anorexic than mine. **Your decision will be based on what you find most valuable in visualizing the system**.
