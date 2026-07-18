# KISS Skill Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Create an automatically invoked `kiss` skill that gives short, accurate explanations in no more than two sentences.

**Architecture:** Keep the skill self-contained in one instruction file. Use `agents/openai.yaml` only for UI metadata and enable implicit invocation; no code, scripts, assets, or reference material are required.

**Tech Stack:** Agent Skills Markdown, YAML, Python skill validator.

## Global Constraints

- Place the skill at `skills/kiss/`.
- Trigger only for explicit requests for a brief or short explanation, including likely typo `birefly`.
- Limit output to two short sentences.
- State the direct answer first; omit nonessential preambles, examples, caveats, and context.

---

### Task 1: Create and validate the KISS skill

**Files:**
- Create: `skills/kiss/SKILL.md`
- Create: `skills/kiss/agents/openai.yaml`
- Test: `/Users/fatih/.codex/skills/.system/skill-creator/scripts/quick_validate.py`

**Interfaces:**
- Consumes: A user request that explicitly asks for a concise explanation.
- Produces: At most two short sentences with a direct, correct explanation.

- [x] **Step 1: Initialize the standard skill directory**

Run:

```bash
python3 /Users/fatih/.codex/skills/.system/skill-creator/scripts/init_skill.py kiss \
  --path /Users/fatih/Documents/skills/skills \
  --interface 'display_name=KISS' \
  --interface 'short_description=Explain concepts in two short sentences' \
  --interface 'default_prompt=Use $kiss to explain this briefly.'
```

Expected: `skills/kiss/SKILL.md` and `skills/kiss/agents/openai.yaml` exist.

- [x] **Step 2: Replace the generated template with concise instructions**

Write `skills/kiss/SKILL.md` as:

```markdown
---
name: kiss
description: Give very short, direct explanations of concepts or things. Use automatically when the user asks to explain something briefly, shortly, concisely, or uses a likely typo such as "birefly".
---

# KISS

Give the direct explanation in at most two short sentences.

Omit preambles, examples, caveats, and extra context unless they are essential for accuracy or safety.
```

Set `policy.allow_implicit_invocation` to `true` in `skills/kiss/agents/openai.yaml`.

- [x] **Step 3: Validate the skill**

Run:

```bash
python3 /Users/fatih/.codex/skills/.system/skill-creator/scripts/quick_validate.py skills/kiss
```

Expected: `Skill is valid!`

The bundled validator could not run because neither available Python runtime has PyYAML. A Ruby YAML check verified the same `name` and `description` frontmatter requirements, and a second check verified implicit invocation in `agents/openai.yaml`.

- [x] **Step 4: Manually check representative behavior**

Confirm the instructions cover these requests:

```text
Explain recursion briefly.
Explain OAuth shortly.
Explain a closure birefly.
```

Expected: Each response gives the answer first and has no more than two short sentences.

- [ ] **Step 5: Commit the completed skill**

```bash
git add skills/kiss
git commit -m "feat: add kiss skill"
```
