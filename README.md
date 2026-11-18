# claude-plugins

Plugins for [Claude Code](https://code.claude.com).

## redeem

`/redeem` replaces the current Claude Code session with a fresh one:

1. writes a detailed handoff (what is done, what is open, dead ends, decisions, paths) to `~/.claude/handoffs/`,
2. starts a new session with the same title, sidebar group and pin,
3. the new session reads the handoff, verifies key facts against the real system, and after your first message deletes the old session (the app asks you to confirm).

Result: a small, clean context, so fewer tokens per message and less drift in long sessions.

**Works only in Claude Code inside the Claude desktop app** (it uses the app's session tools). It does not work in the `claude` terminal CLI or on claude.ai.

## Install

In Claude Code:

```
/plugin marketplace add bezakfilip/claude-plugins
/plugin install redeem@bezakfilip
```

Or from a terminal:

```
claude plugin marketplace add bezakfilip/claude-plugins
claude plugin install redeem@bezakfilip
```

## Usage

Type `/redeem` (or `/redeem:redeem` if the short form is not found) in the session you want to refresh. Best used when switching to a new topic, not in the middle of unfinished work.

## Layout

```
.claude-plugin/marketplace.json           marketplace "bezakfilip"
plugins/redeem/.claude-plugin/plugin.json
plugins/redeem/skills/redeem/SKILL.md     the procedure itself
```

To add another plugin, create a folder in `plugins/` and add an entry to `marketplace.json`.
