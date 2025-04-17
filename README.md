# mani
An ai version of man/tldr no one but me asked for. A simple tool to ask questions about the setting I need without having to read 80 pages of manual/ search for a good 5 minutes.
# API
> [!Important] 
> Subject to small changes
## Core Commands

| Command                         | Description                               | Example                                                |
| ------------------------------- | ----------------------------------------- | ------------------------------------------------------ |
| `mani <command>`                | Show enhanced documentation for a command | `mani grep`                                            |
| `mani ask <command> <question>` | Ask a specific question about a command   | `mani ask tar "how do I extract without overwriting?"` |
| `mani guide <command>`          | Generate a comprehensive markdown guide   | `mani guide ffmpeg`                                    |
| `mani config`                   | View and edit configuration               | `mani config set provider claude`                      |
| `mani update`                   | Update local documentation cache          | `mani update`                                          |

## Global Flags

| Flag | Description | Default | Example |
|------|-------------|---------|---------|
| `--provider, -p` | Select LLM provider | `claude` | `mani --provider ollama grep` |
| `--model, -m` | Specify model for selected provider | Provider-specific | `mani --model claude-3-haiku-20240307 grep` |
| `--output, -o` | Output format (terminal, markdown, json) | `terminal` | `mani --output markdown grep` |
| `--source, -s` | Documentation source (man, tldr, both) | `man` | `mani --source tldr ls` |
| `--cache, -c` | Use cached responses if available | `true` | `mani --no-cache grep` |
| `--timeout, -t` | Timeout for LLM requests in seconds | `30` | `mani --timeout 60 grep` |
| `--verbose, -v` | Enable verbose output | `false` | `mani --verbose grep` |

## Configuration Command Options

| Command | Description | Example |
|---------|-------------|---------|
| `mani config list` | List all configuration settings | `mani config list` |
| `mani config get <key>` | Get a specific configuration value | `mani config get provider` |
| `mani config set <key> <value>` | Set a configuration value | `mani config set provider ollama` |
| `mani config reset` | Reset configuration to defaults | `mani config reset` |

## Ask Command Flags

| Flag | Description | Default | Example |
|------|-------------|---------|---------|
| `--context, -C` | Number of lines of context to include | `5` | `mani ask --context 10 grep "how do I search recursively?"` |
| `--examples, -e` | Include usage examples in response | `true` | `mani ask --no-examples tar "what is the x flag?"` |

## Guide Command Flags

| Flag | Description | Default | Example |
|------|-------------|---------|---------|
| `--level, -l` | Detail level (basic, intermediate, advanced) | `intermediate` | `mani guide --level advanced vim` |
| `--sections, -S` | Sections to include (comma-separated) | `all` | `mani guide --sections "synopsis,options,examples" grep` |
| `--output-file, -f` | Save to specific file instead of default location | `~/.mani/guides/<command>.md` | `mani guide --output-file ~/docs/grep.md grep` |

## Provider-Specific Flags

| Flag             | Description                     | Applies To     | Example                                                          |
| ---------------- | ------------------------------- | -------------- | ---------------------------------------------------------------- |
| `--temperature`  | Control randomness in responses | All providers  | `mani --temperature 0.7 grep`                                    |
| `--local-url`    | URL for local model server      | Ollama         | `mani --local-url http://localhost:11434 --provider ollama grep` |
|
