# claudetail

Tail [Claude Code](https://claude.ai/code) session logs in real-time.

Ever stare at Claude Code wondering if it's still working or just stuck? Claude Code doesn't show much progress info — you can't tell if it's thinking, running tools, or doing nothing.

`claudetail -f` gives you a live view of everything happening under the hood: what tools it's calling, what files it's reading/writing, token usage, thinking blocks, and more.

Auto-detects the Claude project for your current working directory. If run outside a project, lists your projects and lets you pick one interactively.

## Install

```bash
curl -fsSL https://raw.githubusercontent.com/sunfmin/claudetail/main/claudetail -o ~/.local/bin/claudetail && chmod +x ~/.local/bin/claudetail
```

Or clone and link:

```bash
git clone https://github.com/sunfmin/claudetail.git
mkdir -p ~/.local/bin
cp claudetail/claudetail ~/.local/bin/
```

Make sure `~/.local/bin` is in your `PATH`.

Requires Python 3.7+ (no external dependencies).

## Usage

```
claudetail [OPTIONS] [DIRECTORY]
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
claudetail

# Follow a project's sessions live
claudetail -f ~/.claude/projects/-Users-me-myproject

# Match project by name substring
claudetail myproject

# Last 20 messages from a specific session
claudetail -n 20 -s 14fe559d

# Follow mode
claudetail -f
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
