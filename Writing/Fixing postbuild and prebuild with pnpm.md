I was trying to use https://github.com/trpc/examples-next-prisma-starter to start a new project, and noticed it used `yarn`. Since I wanted to use `pnpm`, I just tried doing that instead.

However, when deploying to render, I noticed that the `prebuild` script was not being executed.

That led me to [this issue](https://github.com/pnpm/pnpm/issues/2891) on the PNPM repository. Apparently, that is to be expected. [Yarn 2 is even deprecating pre/post scripts](https://yarnpkg.com/advanced/lifecycle-scripts).

> Note that we don't support every single lifecycle script originally present in npm. This is a deliberate decision based on the observation that too many lifecycle scripts make it difficult to know which one to use in which circumstances, leading to confusion and mistakes. We are open to add the missing ones on a case-by-case basis if compelling use cases are provided.

To fix it this and enable `prebuild` and others, just create a new `.npmrc` file with the following content:

```
enable-pre-post-scripts=true
```

All good now!