# Cobra Application Setup

Create project folder and initialize Go module

```bash
mkdir myproject && cd myproject
go mod init myproject
```

Install cobra-cli tool and initialize

```bash
go install github.com/spf13/cobra-cli@latest
cobra-cli init
```

Add commands

```bash
cobra-cli add ask
```

Run it

```bash
go run . --help
go run . ask --help
```
