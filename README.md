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

Verify things you think you know against real sources before answering. Keep the reply short and plain.

Use when you state something as fact, ask “am I right?”, or want source-backed confirmation.

### Example

**Prompt**

> The `URLSession.shared.dataTask` completion handler always runs on the main thread, right?

**Response** (Critical Verifier)

> **Unsupported**
>
> No — it runs on the session’s delegate queue, not the main thread. On `URLSession.shared` that queue is a background serial queue (`com.apple.NSURLSession-delegate`).
>
> A custom `URLSession` with `delegateQueue: .main` would run on main — that option is not available on the shared session.
>
> Source: [Apple — dataTask(with:completionHandler:)](https://developer.apple.com/documentation/foundation/urlsession/datatask(with:completionhandler:)-52wk8) (“executed on the delegate queue”); runtime check: `Thread.isMainThread == false`.
