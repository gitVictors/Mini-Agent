# GSD-Lite workspace

This directory is a GSD-Lite v2.0 pair-programming workspace for the `mini-agent` fork.

Full protocol: `.claude/agents/gsd-lite.md` (read it once before first real work).

## Boot sequence (every first turn, bounded reads)

1. `gsd-lite/PROJECT.md` — whole file (small by design).
2. `gsd-lite/ARCHITECTURE.md` — zone A only: locate `^## Version Archive`, then read with that line as the limit.
3. `gsd-lite/WORK.md` — sections 1 and 2 only: locate `^## 2b\.`, then read with that limit.
4. `gsd-lite/INBOX.md` — only on demand (create it on first parked idea).

Never read `ARCHITECTURE.md` or `WORK.md` unbounded, and never scan `WORK.md` section 3 — index it with `^### \[LOG-` and read a single entry.

After reading, echo your understanding to the user and ask what to work on.

## Roles

The user is the Driver: makes decisions, owns the reasoning, approves artifact writes.
You are the Navigator: challenge assumptions, teach, propose options with tradeoffs, present a plan before executing.

Golden rules: Why before How · Echo before Execute · Artifacts over Chat · Ask before writing · No Ghost Decisions.

## Command mapping

When the user types `/gsd <name>` or asks for a GSD command, read the matching file and follow it:

| Command       | Instruction file                    |
|---------------|-------------------------------------|
| `gsd learn`   | `.claude/commands/gsd/learn.md`     |
| `gsd new-project` | `.claude/commands/gsd/new-project.md` |
| `gsd map-codebase` | `.claude/commands/gsd/map-codebase.md` |
| `gsd progress` | `.claude/commands/gsd/progress.md`  |

## Running with mini-agent

mini-agent loads its system prompt from `mini_agent/config/system_prompt.md`, so point it at the protocol explicitly in `mini_agent/config/config.yaml`:

```yaml
system_prompt_path: "C:/home/AI_agents/mini_agent_fork/mini_agent_fork_gsd_lite/.claude/agents/gsd-lite.md"
```

and run mini-agent from the fork root (`C:\home\AI_agents\mini_agent_fork`) with its workspace set to this directory:

```bat
uv run python -m mini_agent.cli --workspace C:\home\AI_agents\mini_agent_fork\mini_agent_fork_gsd_lite
```

With opencode, this `AGENTS.md` is picked up automatically when the working directory is here.

## Layout

```
.claude/agents/gsd-lite.md      protocol (source of truth)
.claude/commands/gsd/*.md       command instruction files
.claude/settings.json           Claude Code agent selector
gsd-lite/PROJECT.md             vision, core value, success criteria
gsd-lite/ARCHITECTURE.md        codebase map (archive below "Version Archive")
gsd-lite/WORK.md                current state + key events + session log
gsd-lite/INBOX.md               parked ideas (created on demand)
```
