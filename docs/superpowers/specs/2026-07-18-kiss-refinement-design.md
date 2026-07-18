# KISS Refinement Design

## Goal

Make the `kiss` skill more predictable with less trigger and instruction text.

## Changes

- Keep `kiss` model-invoked because brief explanations must trigger automatically.
- Collapse the trigger to one branch: an explicit request for a brief explanation. Do not name the typo `birefly`; normal language understanding covers it.
- Use `brief` in both the description and instruction as the leading word.
- Replace the negative omission list with a positive instruction: give a brief, direct explanation in at most two sentences and add only context essential for accuracy or safety.

## Scope

Only `skills/kiss/SKILL.md` changes. The UI metadata and implicit-invocation policy stay unchanged.
