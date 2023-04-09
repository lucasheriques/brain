Because a parent div has one of a `transform`, `filter` or `will-change` CSS properties (it becomes the containing block for the fixed position child).

```js
const selector = '.the-fixed-child';

function findCulprits(elem) {

if (!elem) {

throw new Error(

'Could not find element with that selector'

);

}

let parent = elem.parentElement;

while (parent) {

const {

transform,

willChange,

filter,

} = getComputedStyle(parent);

if (

transform !== 'none' ||

willChange === 'transform' ||

filter !== 'none'

) {

console.warn(

'🚨 Found a culprit! 🚨\n',

parent,

{ transform, willChange, filter }

);

}

parent = parent.parentElement;

}

}

findCulprits(document.querySelector(selector));