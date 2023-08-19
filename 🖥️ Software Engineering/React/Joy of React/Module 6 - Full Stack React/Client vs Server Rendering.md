

SSR: we use React on the server side to generate the initial HTML so we're not showing just an empty black page on first load. All interactive elements (JS, fonts, etc) are loaded after, so the interactivity still takes a while.
CSR: we send a barebones HTML file, that loads the JavaScript then. Then, the JS script dynamically adds all DOM nodes.