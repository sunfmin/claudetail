# watchtail

Watch/tail [Claude Code](https://claude.ai/code) JSONL session logs in human-readable format.

Shows all message details including model info, token usage, tool calls with full inputs, tool results, thinking blocks, hook summaries, progress events, and session metadata.

If run outside a Claude Code project directory, watchtail lists your projects and lets you pick one interactively.

## Install

```bash
curl -fsSL https://raw.githubusercontent.com/sunfmin/watchtail/main/watchtail -o /usr/local/bin/watchtail && chmod +x /usr/local/bin/watchtail
```

Or clone and link:

```bash
git clone https://github.com/sunfmin/watchtail.git
cp watchtail/watchtail /usr/local/bin/
```

Requires Python 3.7+ (no external dependencies).

## Usage

```
watchtail [OPTIONS] [DIRECTORY]
```

### Options

| Flag | Description |
|------|-------------|
| `-n NUM` | Number of recent messages to show (default: all) |
| `-f` | Follow mode - keep watching for new content |
| `-p GLOB` | File glob pattern (default: `*.jsonl`) |
| `-s SESSION` | Only show a specific session (substring match) |
| `--compact` | Truncate long content |
| `--no-color` | Disable colors |

### Examples

```bash
# Run anywhere - pick a project interactively
watchtail

# Follow a project's sessions live
watchtail -f ~/.claude/projects/-Users-me-myproject

# Match project by name substring
watchtail myproject

# Last 20 messages from a specific session
watchtail -n 20 -s 14fe559d

# Follow mode
watchtail -f
```

### What it shows

- **User messages** with permission mode and working directory
- **Assistant messages** with model name, stop reason, and token usage (input/output/cache)
- **Tool calls** with full input parameters
- **Tool results** with error status
- **Thinking blocks**
- **Turn duration** and session slug
- **Hook progress and summaries**
- **Queue operations**
- **File history snapshots**
- **Session metadata** (version, git branch, cwd)

## License

MIT
