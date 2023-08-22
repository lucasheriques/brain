The term comes from the security field.

The ideia is that every member of an organization should only have the amount of access, of authorization, that they need to do their job.

We can imagine that every component in a React applications is a member of this organization.
Each component should only have access to the data it needs to perform its function.

## Why do something like this?
It's true that, in a similar codebase, where you're the only developer, this might be an overkill, since you're not going to break your own components.

But imagine you're one of fifty developer working on a codebase with hundreds of thousands lines of code. If you're tasked to update one of this components on this huge codebase, you might not have the full context to make sure you're not breaking anything. If you have too much power on a child component, you might cause subtle bugs that can go unnoticed.

---

In real-world production settings like this, we're often tossed into corners of the codebase that we aren't familiar with at all. You might be tasked with tweaking the `AddNewItemForm` component without knowing anything about how it works!

In those types of situations, it's _so so easy_ to introduce subtle bugs. And so, the less privilege we give to our components, the less problems we'll have down the road.