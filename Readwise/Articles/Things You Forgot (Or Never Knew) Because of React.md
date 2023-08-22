# Things You Forgot (Or Never Knew) Because of React

![rw-book-cover](https://joshcollinsworth.com/images/post_images/because-of-react.png)

## Metadata
- Author: [[Josh Collinsworth]]
- Full Title: Things You Forgot (Or Never Knew) Because of React
- Category: #articles
- URL: https://joshcollinsworth.com/blog/antiquated-react#part-1-an-intro-about-music-defaults-and-bubbles

## Highlights
- React trained us that things need to be built *specifically for a certain framework*. But that’s not very true anymore, and it arguably never should have been. ([View Highlight](https://read.readwise.io/read/01h8exmehdts6j5eabdejm5002))
- It’s worth remembering: the world that gave us React had a different set of problems.
  In that world, most frontend UIs were built either with vanilla JavaScript, or with jQuery (or similar alternatives). And that method of building apps, as we now know, didn’t scale well beyond a certain limit.
  That’s because you had to write your own selectors for each and every element and DOM node you might want to interact with, and you had to come up with your own manual way of tracking and syncing state. That usually involved writing to and retrieving from the DOM, which was messy, error-prone, and most importantly, slow. (That’s where the virtual DOM came in, but even *that* has been [pretty thoroughly outdated for years](https://svelte.dev/blog/virtual-dom-is-pure-overhead).) ([View Highlight](https://read.readwise.io/read/01h8exv531mq30tm2n3jfk3dhr))
- Frontend is similar: every frontend framework has components; they’re all compatible with TypeScript; they all have the concept of props, children, and reactive state. These are things we’ve generally agreed we like and are good. They just have different takes on implementation. ([View Highlight](https://read.readwise.io/read/01h8ey615fkf9b112ghjqstfsh))
