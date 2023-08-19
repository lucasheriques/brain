

SSR: we use React on the server side to generate the initial HTML so we're not showing just an empty black page on first load. All interactive elements (JS, fonts, etc) are loaded after, so the interactivity still takes a while.
CSR: we send a barebones HTML file, that loads the JavaScript then. Then, the JS script dynamically adds all DOM nodes.

> For content-heavy websites and apps like this course platform, SSR can have a _huge_ impact on user experience. The content appears 3-4x faster!


![[Pasted image 20230819150949.png]]
Server Side Rendering illustration

1. Server does the initial React render
2. HTML file is sent to the client (what the arrow indicates)
3. 