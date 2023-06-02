
This initial command creates your SST app using their standard monorepo structure:

```bash
$ pnpm create sst my-t3-sst-app
$ cd my-t3-sst-app
$ pnpm i
```

Now, let's create our T3 app. We'll name it `web` and put it on the packages folder.

```bash
$ cd packages
$ pnpm create t3-app@latest
$ 
```