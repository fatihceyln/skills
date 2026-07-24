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

> kiss mode: Swift'te `defer` ne işe yarar?

**Response** (KISS)

> `defer`, bulunduğu scope bittiğinde (fonksiyon erken `return` olsa bile) çalışacak kodu erteler. Kaynak kapatma, kilit bırakma gibi temizlik işleri için kullanılır.

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

> `URLSession.shared.dataTask` completion handler'ı her zaman main thread'de çalışır, değil mi?

**Response** (Critical Verifier)

> **Desteklenmiyor**
>
> Hayır — `URLSession.shared` completion handler'ı main thread'de çalışmaz; session'ın delegate queue'sunda çalışır.
>
> En güçlü karşı argüman: kendi oluşturduğun bir `URLSession`'a `delegateQueue: .main` verirsen handler main'de çalışır. Bu, shared session için geçerli değildir; shared session'da özel queue veremezsin.
>
> Kanıt:
> - Apple docs: completion handler "delegate queue" üzerinde çalışır ([dataTask(with:completionHandler:)](https://developer.apple.com/documentation/foundation/urlsession/datatask(with:completionhandler:)-52wk8)).
> - Apple docs: `delegateQueue` `nil` ise session kendi serial operation queue'sunu oluşturur ([init(configuration:delegate:delegateQueue:)](https://developer.apple.com/documentation/foundation/urlsession/init(configuration:delegate:delegatequeue:))).
> - Runtime (2026-07-24, macOS): `URLSession.shared.dataTask` içinde `Thread.isMainThread == false`, queue label `com.apple.NSURLSession-delegate`.
>
> UI güncellemesi gerekiyorsa handler içinde açıkça main queue'ya hop etmen gerekir. Sonucu değiştirir: custom session + `delegateQueue: .main`.
