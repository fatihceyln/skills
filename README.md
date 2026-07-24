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

### Example

**Prompt**

> kiss mode: What does `defer` do in Swift?

**Response** (KISS)

> `defer` schedules code to run when the current scope ends, even if the function returns early. Use it for cleanup such as closing resources or releasing locks.

## Critical Verifier

Optimize for truth, not agreement. Treat claims as hypotheses to test instead of reflexively agreeing.

Use for factual questions, proposed diagnoses or conclusions, architecture and implementation claims, “am I right?” questions, disputed or high-stakes topics, and fact-checking or adversarial review.

The skill:

- Looks for the strongest credible counterargument and falsifying evidence
- Verifies substantive claims against code, docs, or authoritative sources before concluding
- Leads with a verdict: **Supported**, **Partly supported**, **Unsupported**, or **Unresolved**
- Separates verified facts, inferences, opinions, and unresolved uncertainty

### Example

**Prompt**

> The `URLSession.shared.dataTask` completion handler always runs on the main thread, right?

**Response** (Critical Verifier)

> **Unsupported**
>
> No — the `URLSession.shared` completion handler does not run on the main thread; it runs on the session’s delegate queue.
>
> Strongest counterargument: if you create your own `URLSession` with `delegateQueue: .main`, the handler will run on the main queue. That does not apply to the shared session, where you cannot supply a custom queue.
>
> Evidence:
> - Apple docs: the completion handler runs on the delegate queue ([dataTask(with:completionHandler:)](https://developer.apple.com/documentation/foundation/urlsession/datatask(with:completionhandler:)-52wk8)).
> - Apple docs: if `delegateQueue` is `nil`, the session creates its own serial operation queue ([init(configuration:delegate:delegateQueue:)](https://developer.apple.com/documentation/foundation/urlsession/init(configuration:delegate:delegatequeue:))).
> - Runtime (2026-07-24, macOS): inside `URLSession.shared.dataTask`, `Thread.isMainThread == false`, queue label `com.apple.NSURLSession-delegate`.
>
> If you need a UI update, hop to the main queue explicitly inside the handler. What would change the conclusion: a custom session with `delegateQueue: .main`.
