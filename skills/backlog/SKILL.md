---
name: backlog
description: Turns a software idea or a discussed feature into a backlog of short, vertical user stories, writes it to the project's .cursor/backlogs folder, and moves it to .cursor/stories once accepted. No acceptance criteria or implementation; that's /story's job.
disable-model-invocation: true
---

# Backlog

Your job is to help me split what I tell you into user stories. I bring the requirements; you order and slice them.

## Conversation

1. Listen to the idea or feature. If something is unclear, ask. One question at a time, with your suggested answer.
2. If it's a new project, let's discuss the stack. Only the stack, not the architecture or implementation.
3. Ask whether any of these expensive-to-change decisions apply. Only ask, don't design them:
   - Multi-tenant or multi-organization
   - Permissions or roles model
   - Offline or sync
   - Multi-language or multi-currency
4. Propose the backlog. I adjust it. Keep the file in `.cursor/backlogs` up to date while we adjust.
5. When I accept the backlog, move the file to `.cursor/stories`. Don't move it before I accept.

## Rules

- **Don't invent requirements.** Only split what I told you. If you see a gap, ask me; don't fill it.
- **Each story delivers value on its own** and cuts through every layer (data, backend, UI). Never split by layer.
- **No technical stories.** The actor is never the developer or the system. "Set up the database" or "create the user model" are not stories; that infrastructure gets built inside the first story that needs it.
- **Few stories.** 10–15 max. I'd rather add than cut.
- **One line per story.** No acceptance criteria, no technical details, no estimates or priorities.
- The first story is the smallest one usable end to end (walking skeleton).

## Output format

```markdown
## Context
<one or two lines: what it is and who it's for>
Stack: <what we agreed>
Expensive decisions: <the ones that apply, or "none">

## Backlog
1. As a <actor>, I want <action>, so that <benefit>.
2. As a <actor>, I want <action>, so that <benefit>. Requires: #1
```

Add `Requires: #N` only when a story makes no sense without another.

## Where to save it

Write that block to `.cursor/backlogs/<slug>.md` in the project. `<slug>` is a short kebab-case name of the idea (for example `invoice-reminders`). Create `.cursor/backlogs` if it doesn't exist. If a file with that name already exists, ask before overwriting.

When I accept the backlog, move `.cursor/backlogs/<slug>.md` to `.cursor/stories/<slug>.md`. Create `.cursor/stories` if it doesn't exist. If the destination already exists, ask before overwriting. The file leaves `.cursor/backlogs`.

Show the path each time it changes: the draft in `.cursor/backlogs`, then the accepted file in `.cursor/stories`.
