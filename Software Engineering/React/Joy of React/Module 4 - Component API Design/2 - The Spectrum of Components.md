![[Pasted image 20230323144928.png]]

When implementing a component, it's good to think about what is it going to be used for.

It's nice to have a couple of primitive, UI-only components, that will be used on the entire application. Those are close to the left-side of the spectrum, like `Button`, `Modal`, `Slider`, etc.

As you go to the right, you kinda develop specialized components. For instance, you might have a `Card` component, however, in the user profile, you'll show the `UserProfileCard`, which is composed by the `Card` component and has specific information tied to it.

Good talk to watch: https://www.youtube.com/watch?v=mVVNJKv9esE

![[area-web-separation-of-concerns.png]]
This has a similar idea.

In the past, we used to separate our websites in JS, CSS, HTML files.

But, in today's era of modern web applications, each component has its own set of those three components.

And, depending on how close that component is to the user (a `Button` component, which is very primitive, versus maybe something like a `SignInButton`), that component will be further to the right on the *Spectrum of Components*.