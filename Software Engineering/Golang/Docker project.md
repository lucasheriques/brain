
# Stage 6 - Process isolation

whats the difference between:

```go

	cmd.Env = []string{"PID1=-[ns-process]- # "}

	cmd.SysProcAttr = &syscall.SysProcAttr{
		Cloneflags: syscall.CLONE_NEWPID,
	}
```

```go
func isolateProcess() error {
	// Unshare
	if err := syscall.Unshare(syscall.CLONE_NEWNS | syscall.CLONE_NEWUTS | syscall.CLONE_NEWPID); err != nil {
		return fmt.Errorf("cannot unshare, error: %v", err)
	}
	return nil
1
}
```


# What is a container

it's an isolated process running in a host that cannot interact with files or process on the host.