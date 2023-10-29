if we're building for Linux, we need to add this piece of code to tell the Go compiler:
```
//go:build linux
// +build linux
```

it must be before the `package`.

we had to do that specifically for the Docker project.

also had to add this setting to the VS Code settings json so it stops complaning:

`"go.toolsEnvVars": {"GOOS" : "linux"},`
