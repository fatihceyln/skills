# Personal Agent Skills

## Installation Guide

The installer lists every available skill and lets you choose what to install and which agents to target.

```bash
npx skills add https://github.com/fatihceyln/skills.git
```

For a non-interactive global install:

```bash
npx skills add https://github.com/fatihceyln/skills.git -g -y
```

## KISS (Keep It Stupid Simple)

Give brief, direct explanations in at most two sentences.

Use when you explicitly want a short answer. Trigger with phrases like "brief explanation", "keep it short", or "kiss mode".

## Critical Verifier

Optimize for truth, not agreement. Treat claims as hypotheses to test instead of reflexively agreeing.

Use for factual questions, proposed diagnoses or conclusions, architecture and implementation claims, “am I right?” questions, disputed or high-stakes topics, and fact-checking or adversarial review.

The skill:

- Looks for the strongest credible counterargument and falsifying evidence
- Verifies substantive claims against code, docs, or authoritative sources before concluding
- Leads with a verdict: **Supported**, **Partly supported**, **Unsupported**, or **Unresolved**
- Separates verified facts, inferences, opinions, and unresolved uncertainty
