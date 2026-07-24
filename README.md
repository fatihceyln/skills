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

Ask a complex question; get a fast answer in **at most two sentences**. No essays, no bullet lists, no “it depends” chapters — just the core point.

Use when you explicitly want a short answer. Trigger with phrases like "brief explanation", "keep it short", or "kiss mode".

### Example

**Prompt**

> kiss mode: Walk me through how a browser loads a webpage — DNS lookup, TCP/TLS, HTTP request, parsing, rendering, and where a CDN fits into that path.

**Response** (KISS)

> The browser resolves the host, opens a secure connection, fetches the document and its assets, then parses HTML/CSS/JS into a renderable tree and paints pixels. A CDN shortens that path by answering the fetch from an edge node close to the user instead of the origin server.

## Verify

Verify things you think you know against real sources before answering. Keep the reply short and plain.

Use when you state something as fact, ask “am I right?”, or want source-backed confirmation.

### Example

**Prompt**

> The `URLSession.shared.dataTask` completion handler always runs on the main thread, right?

**Response** (Verify)

> **False**
>
> No — it runs on the session’s delegate queue, not the main thread. On `URLSession.shared` that queue is a background serial queue (`com.apple.NSURLSession-delegate`).
>
> A custom `URLSession` with `delegateQueue: .main` would run on main — that option is not available on the shared session.
>
> Source: [Apple — dataTask(with:completionHandler:)](https://developer.apple.com/documentation/foundation/urlsession/datatask(with:completionhandler:)-52wk8) (“executed on the delegate queue”); runtime check: `Thread.isMainThread == false`.
