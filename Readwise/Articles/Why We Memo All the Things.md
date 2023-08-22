# Why We Memo All the Things

![rw-book-cover](https://attardi.org/static/memo-all-the-things-cd5577fb4f159409c9227a729272d7ea.png)

## Metadata
- Author: [[attardi.org]]
- Full Title: Why We Memo All the Things
- Category: #articles
- URL: https://attardi.org/why-we-memo-all-the-things/

## Highlights
- If we don’t `memo` a component that should be, we are:
  1. Running a render function
  2. Allocating all callbacks anew
  3. Allocating all `useMemo` functions anew
  4. Allocating a bunch of new JSX elements
  5. Repeating 1–4 recursively for all the children
  6. Causing the React reconciler to compare the old tree with the new tree ([View Highlight](https://read.readwise.io/read/01h8cv5z0327j5hyb7ehg4hsrt))
- But, you may be thinking, what if the vast majority of my components are cheap to rerender? Won’t the cost of all these unnecessary `memo`s add up to more than the possible cost of a wasted expensive rerender?
  In my experience, the answer is no. I have never seen `memo` itself show up in a profile, whereas it’s pretty common to see expensive renders take mega amounts of CPU time. If you see something different, you probably have a bigger problem, like having way too many components mounted. ([View Highlight](https://read.readwise.io/read/01h8ctwervn6anmsh73et8eavc))
- Many people aren’t aware of this: `children` is a sneaky prop that breaks `memo`. JSX creates a new data structure on every render. Any time a component rerenders and passes JSX to another component, it’s gonna break the child component’s `memo`. ([View Highlight](https://read.readwise.io/read/01h8cwbqne9e5vz91ck1evjws4))
- Using `memo` and its cousins everywhere is a sane default. It’s like a mask mandate during a coronavirus pandemic. Sure, we could have everybody tested every day and only ask people who are actively contagious to wear a mask. But it’s far cheaper, simpler, and ultimately more effective to ask everybody to wear a mask by default. ([View Highlight](https://read.readwise.io/read/01h8cwpwankd4e6kjc6aj0qxcd))
