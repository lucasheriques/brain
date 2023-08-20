

SSR: we use React on the server side to generate the initial HTML so we're not showing just an empty black page on first load. All interactive elements (JS, fonts, etc) are loaded after, so the interactivity still takes a while.
CSR: we send a barebones HTML file, that loads the JavaScript then. Then, the JS script dynamically adds all DOM nodes.

> For content-heavy websites and apps like this course platform, SSR can have a _huge_ impact on user experience. The content appears 3-4x faster!


![[server-side-rendering.png]]
Server Side Rendering illustration

1. Server does the initial React render
2. HTML file is sent to the client (what the arrow indicates), which then the browsers loads. Marks the *Content Painted*, which is the moment when the user can start reading the website. Referred as the [Largest Contentful Paint](https://web.dev/lcp/).
3. JS bundle is downloaded and executed, which marks the *Page Interactivity* (content becomes dynamic). Often referred as [Time To Interactive](https://web.dev/tti/).

![[client-side-rendering.png]]
Client Side Rendering Illustration


# Hydration

When the HTML first loads, it doesn't have any interactivity.

Hydration is where we add it. At a high level:

- React performs a "speed render" to figure out the shape of the component tree, then initializes the [[7 - Component Instance]].
- Wire up all interactivity (event listeners, refs, etc).

![[Pasted image 20230820003017.png]]