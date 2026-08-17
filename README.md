## What This Repo Is

This repository defines how I expect to interact with AI systems: a set of **behavioral contracts,
thinking standards, and interaction rules** that govern how models should reason, critique, and
collaborate with me. It is an alignment layer between how models behave by default and how I want
to work.


## The Two Souls

Conversation and agency are different jobs with different failure modes, so they get different
contracts. Use one or both.

| File | Governs | Use it in |
|---|---|---|
| `chat/soul.md` | Reasoning, honesty, critique, tone | Chat clients, custom instructions, any conversation |
| `agent/soul.md` | Action: reading and writing files, running commands, changing systems | Coding agents, CLI agents, anything with tools |

### `chat/soul.md`

The constitution. Non-negotiable principles that apply to every interaction:

* Honesty over politeness
* Opinions over hedging
* Critical thinking over reassurance
* Momentum over analysis paralysis
* Human prose over machine tells

If a rule applies everywhere, it belongs here.

### `agent/soul.md`

The operating contract for agents that take real actions. It assumes `chat/soul.md` and adds what
agency requires:

* Verified claims over confident recall
* Whole scope, or an explicit statement of what was skipped
* Architecture over expedience
* Confirmation before anything irreversible
* Secrets never written where they can be read
* Faithful reporting of what happened

A chat model that is wrong wastes a minute. An agent that is wrong deletes something.


## How to Use This Repo

### Chat

Copy the contents of `chat/soul.md` into your client's custom instructions, so it governs every
conversation instead of the one you remember to paste it into.

| Client | Where |
|---|---|
| Claude | Click your initials, bottom left, then **Settings**, then the **Instructions for Claude** field |
| ChatGPT | **Settings**, then **Personalization**, then **Custom Instructions** (on iOS and Android, **Settings**, then **Customize ChatGPT**) |

For a client with no custom-instructions field, paste the file into the first message of the
conversation and add:

> "Use `soul.md` as governing interaction rules for this conversation."

### Agents

Paste both files into the agent's persistent instruction file (`CLAUDE.md`, `AGENTS.md`, a system
prompt, or the equivalent), `chat/soul.md` first.

In Claude Code, import the files rather than pasting them, so this repo stays the only copy. Give
it this:

> Clone https://github.com/Comma8/ai-specs to a permanent location. Then add the two soul files
> as `@` imports at the top of my user memory file at `~/.claude/CLAUDE.md`, chat first, agent
> second. Import them, do not inline the contents.

Every session then loads the current file, and a `git pull` is the whole update.

`agent/soul.md` is deliberately generic. It holds transferable principles, not project rules.
Anything specific to a codebase (its libraries, its build gate, its deploy chain) belongs in that
project's own instruction file, not here. Duplicating a project rule into this repo creates a second
source of truth, which is the exact drift these documents exist to prevent.

### Ongoing Conversations

If behavior drifts, a reminder is sufficient:

> "Operate under soul.md."


## What This Repo Is Not

* Not a personality prompt
* Not a safety framework
* Not a prompt marketplace
* Not documentation for end users
* Not project configuration

This repo exists to improve **thinking quality**, not tone compliance.


## Design Principles

* Signal over noise
* Depth over speed (unless speed materially matters)
* Alternatives over false dichotomies
* Historical context when it improves reasoning
* Explicit uncertainty over confident guessing


## Credits

The slop bans in both souls distill [stop-slop](https://github.com/hardikpandya/stop-slop) by
Hardik Pandya (MIT).


## Guiding Question

> Does this interaction make my thinking sharper, faster, or more honest?

If not, it is noise.
