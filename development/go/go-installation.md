# Go Installation

To install the Go tools, use the following command:

```bash
sudo dnf install golang
```

The go and gofmt binaries will become available on the system.

Go code lives in a workspace which is defined by the GOPATH environment variable. 
A common choice among developers, and the default value of GOPATH starting from the Go 1.8 release, is to use $HOME/go:

```bash
mkdir -p $HOME/go
echo 'export GOPATH=$HOME/go' >> $HOME/.bashrc
source $HOME/.bashrc
```

Check that GOPATH is set correctly with this command:

```bash
go env GOPATH
```
