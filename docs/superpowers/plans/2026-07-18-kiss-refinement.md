# KISS Refinement Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Simplify the KISS skill's automatic trigger and concise-response instruction.

**Architecture:** Keep `kiss` model-invoked with one trigger branch and one positive body instruction. Do not change UI metadata or policy.

**Tech Stack:** Agent Skills Markdown.

## Global Constraints

- Preserve model invocation.
- Trigger on an explicit request for a brief explanation.
- Limit the explanation to two sentences.
- Include only context essential for accuracy or safety.

---

### Task 1: Refine the KISS instruction

**Files:**
- Modify: `skills/kiss/SKILL.md`
- Test: `skills/kiss/SKILL.md`

**Interfaces:**
- Consumes: An explicit request for a brief explanation.
- Produces: A direct explanation in at most two sentences, with only essential context.

- [x] **Step 1: Replace the skill content**

Write `skills/kiss/SKILL.md` as:

```markdown
---
name: kiss
description: "Brief explanations: use when the user explicitly requests a brief explanation."
---

# KISS

Give a brief, direct explanation in at most two sentences. Add only context essential for accuracy or safety.
```

- [x] **Step 2: Verify the refined requirements**

Run:

```bash
ruby -e 'require "yaml"; skill = File.read("skills/kiss/SKILL.md"); frontmatter = YAML.safe_load(skill.split("---", 3)[1]); abort unless frontmatter["name"] == "kiss" && frontmatter["description"] == "Brief explanations: use when the user explicitly requests a brief explanation." && skill.include?("at most two sentences") && skill.include?("essential for accuracy or safety"); puts "KISS refinement verified"'
```

Expected: `KISS refinement verified`

- [ ] **Step 3: Commit the refinement**

```bash
git add skills/kiss/SKILL.md
git commit -m "refactor: simplify kiss skill"
```
