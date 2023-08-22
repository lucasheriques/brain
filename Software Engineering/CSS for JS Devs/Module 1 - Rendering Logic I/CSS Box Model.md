Four layers:
1. Content
2. Padding
3. Border
4. Margin

Padding and border both consume the internal size of the element. So, if they increase, you're kinda reducing the "util" area from the box.

Margin has no effect on this; it just makes the separation from the box to other boxes.

If you don't use `box-sizing: border-box` , when making a new child element, it'll not consider the `padding` and `border` to be part of its internal size. It'll be added in addition to whatever `height` or `width` properties are set up.