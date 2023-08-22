Here's how to think about it: `position: sticky` can only stick in one "context". If it's within a scroll container, it can only stick within that container.

Frustratingly, it doesn't have to be a direct parent, either — it might be a great-great-great-great-grandparent that sets `overflow: hidden`, maybe to remove an unwanted horizontal scrollbar!

```js
// Replace “.the-sticky-child” for a CSS selector

// that matches the sticky-position element:

const selector = '.the-sticky-child';

function findCulprits(elem) {

if (!elem) {

throw new Error(

'Could not find element with that selector'

);

}

let parent = elem.parentElement;

while (parent) {

const { overflow } = getComputedStyle(parent);

if (['auto', 'scroll', 'hidden'].includes(overflow)) {

console.log(overflow, parent);

}

parent = parent.parentElement;

}

}

findCulprits(document.querySelector(selector));