
This guide assumes that you already have an AWS account. If you don't have an AWS account, let me link to to [this guide from SST](https://sst.dev/chapters/create-an-aws-account.html) to help you set up.

This initial command creates your SST app using their standard monorepo structure:

```bash
$ pnpm create sst my-t3-sst-app
$ cd my-t3-sst-app
$ pnpm i
$ pnpm dev
```

Once `pnpm dev` finished running, you'll have your environment set up on AWS (without any tears!).






Now, let's create our T3 app. We'll name it `web` and put it on the packages folder.

```bash
$ cd packages
$ pnpm create t3-app@latest
```

Here's a screenshot showing the answers to the command:

![[CleanShot 2023-06-01 at 22.59.03.png]]

I just selected everything and named the project `web`.

Now, let's go back 