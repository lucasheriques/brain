when we first start learning how to code, we're eager to start writing software and making new features

as you grow in seniority, you start noticing that code is read, moved or refactored many times more that it is written

because of that, you need to be careful about the code you write - you have to optimize for readability.

as the company grows, the code on the platform keeps changing. maybe you start working on feature X, but then you move on to next projects. then, a new engineer joins, and they have to work on a fix at feature X. problem is, feature X was so poorly written, that it takes a long time for a new person to understand what is it doing.

as a senior engineer, you need to see this problem ahead of time. sure, you can implement a function with a fancy one-liner function that does the job. however, is that trade-off worth it? or are you just showing off your functional programming skills?

maybe that first code that we all begin writing is the better one. remember that double for with an if inside? maybe that's better than using a fancy `.reduce` one-liner.

As Guido Van Rossum, the creator of Python, has noted: Code is read more often than it is written. Code should always be written in a way that promotes readability.

design your code around readability. even if nobody else is reading that code, that just means that it's gonna be you, and worse, 12 months later when you don't even remember writing that.


```js
function range(start, end, step = 1) {
  let output = [];

  if (typeof end === 'undefined') {
    end = start;
    start = 0;
  }

  for (let i = start; i < end; i += step) {
    output.push(i);
  }

  return output;
};
```

```js
function range(n) {
  return Array.from({ length: n }, (_, index) => index);
}
```