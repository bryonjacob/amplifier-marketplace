# Amplifier Hooks Architecture

This document describes the Claude Code hook system provided by the Amplifier `amp` plugin.

## 📁 Directory Structure

```
plugins/amp/
├── hooks/
│   ├── hooks.json           # Hook manifest
│   ├── session_start.py     # Memory retrieval at session start
│   ├── stop.py              # Memory extraction on stop
│   ├── post_tool_use.py     # Claim validation + quality checks
│   ├── code_change.sh       # Auto quality checks on code changes
│   ├── notification.py      # Desktop notifications
│   ├── precompact.py        # Transcript preservation
│   ├── subagent_logger.py   # Subagent usage tracking
│   ├── hook_logger.py       # Shared logging utility
│   ├── memory_cli.py        # Memory management CLI
│   └── statusline_example.sh # Custom status line example
└── logs/                     # Hook execution logs
```

## 🏗️ Architecture Overview

### Hook System

The `hooks/hooks.json` manifest defines all hooks available in the amp plugin:

- **SessionStart**: Memory retrieval when conversation starts
- **Stop/SubagentStop**: Memory extraction when conversation ends
- **PreToolUse**: Log subagent invocations before execution
- **PostToolUse**: Validate claims and run quality checks after actions
- **Notification**: Send desktop notifications for important events
- **PreCompact**: Export conversation transcript before compaction

### Memory System Integration

The hooks integrate tightly with Amplifier's memory system:

- `session_start.py` - Retrieves relevant memories from past conversations
- `stop.py` - Extracts key learnings, decisions, and solutions
- `post_tool_use.py` - Validates assistant claims against stored memories

Memory system is opt-in via `MEMORY_SYSTEM_ENABLED=true` environment variable.

### Quality Automation

The `code_change.sh` hook automatically runs quality checks after code changes:

- Detects git worktrees and handles virtual environment conflicts
- Runs `make check` for linting, formatting, and type checking
- Provides immediate feedback on code quality issues

### Logging

All hooks use `hook_logger.py` for consistent logging:

- Logs to `plugins/amp/logs/{hook_name}_YYYYMMDD.log`
- Automatic log rotation after 7 days
- Multi-level logging (INFO, DEBUG, WARN, ERROR)
- Dual output to file and stderr for debugging

## 🔧 How It Works

### Event Flow

1. **On Session Start**:
   - `session_start.py` hook triggers
   - Searches memories for relevant context
   - Provides context to conversation

2. **On Code Change** (Write/Edit):
   - `code_change.sh` hook triggers
   - Runs `make check` in correct environment
   - Reports quality issues

3. **On Tool Use**:
   - `post_tool_use.py` hook triggers
   - Validates claims against memories
   - Detects potential contradictions

4. **On Stop**:
   - `precompact.py` exports full transcript to `.data/transcripts/`
   - `stop.py` extracts memories from conversation
   - Stores learnings for future sessions

5. **On Notification Events**:
   - `notification.py` sends cross-platform desktop notifications
   - Provides immediate feedback on important events

### Subagent Tracking

The `subagent_logger.py` hook logs all subagent invocations:

- Logs to `.data/subagent-logs/YYYYMMDD.jsonl`
- Tracks which agents are used and when
- Helps analyze agent usage patterns

## 🎯 Design Principles

1. **Opt-in by Default**: Memory system requires explicit enablement
2. **Fail Gracefully**: Hooks don't break workflows if they error
3. **Cross-Platform**: Works on Mac, Linux, Windows, WSL
4. **Minimal Overhead**: Fast execution, async where possible
5. **Observable**: Comprehensive logging for debugging

## 📚 Related Documentation

- [Memory System](../../../../docs/MEMORY_SYSTEM.md)
- [Hook Logs](./logs.md)
- [Claude Code Hooks Reference](../../../../ai_context/claude_code/CLAUDE_CODE_HOOKS_REFERENCE.md)
