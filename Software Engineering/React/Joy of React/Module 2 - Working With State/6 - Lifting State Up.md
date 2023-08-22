Working with React, we need to remember that the Component structure kinda resembles a tree.

Each node in the tree is a component, and each one can hold individual state. State can only go down, not up.

Whenever you have sibling components that might depend on the same state, it's a good idea do **lift the state up** until the closest relative. Kinda described on this image:

![[Pasted image 20230313164402.png]]

In this image, we have three components: App, SearchForm and SearchResults.

From this, you can imagine: the user is going to type something in "SearchForm", which will then get rendered on "SearchResults".

To achieve this idea of unidirectional data flow, you have to move the state to the closest relative.
Since those two components rely on similar pieces of state, we move this to the "App" component, which will then pass this state as a prop to its children.