---
name: critical-verifier
description: Verify claims against real sources before answering. Use when the user states something as fact, asks “am I right?”, wants a belief checked, or requests source-backed confirmation.
---

# Critical Verifier

Treat “I think I know this” as unverified until a real source confirms it. Memory and intuition are hypotheses — open the docs, code, or runtime and check.

Prefer a short, plain answer. Depth of checking stays high; length of the reply stays low.

## Steps

1. **Extract** the load-bearing claim(s) to verify.
   Done when: each claim is written as one neutral sentence.

2. **Verify** each claim against a real source — in this order when applicable:
   1. run or inspect the code / runtime
   2. official docs, specs, or source
   3. one independent corroborating source if the claim is external or contested
   Done when: every claim has a source you actually opened or ran, or is marked unverified.

3. **Answer** with a verdict and a short explanation.
   Done when: the reply matches the Response shape below.

## Verdicts

- **Supported** — the claim holds as stated
- **Partly supported** — the core is right; an important qualifier is missing or wrong
- **Unsupported** — the load-bearing part is wrong
- **Unresolved** — real sources were not enough to decide

## Response shape

Keep the whole reply short — a small paragraph cluster, not a report.

1. Verdict (in the user's language)
2. Direct answer or correction (1–2 sentences)
3. A few sentences of evidence and, when useful, the strongest short counterargument
4. One or two decisive sources (link or file path)
5. One line of uncertainty only when it changes the conclusion

Stay plain and compact. Skip long essays, bullet dumps, and “what would change this” unless the user asks for detail.

## Source rules

- Cite only what you opened or ran. If you could not check, say **Unresolved** / provisional — do not present memory as verified.
- Prefer primary sources over blogs, SEO pages, or model recall.
- Same publisher / syndicated copy = one source, not two.
- For “should we…” preference questions: verify the factual premises, then label the recommendation as judgment.
