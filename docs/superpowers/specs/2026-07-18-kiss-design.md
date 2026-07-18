# KISS Skill Design

## Goal

Provide automatic, short explanations when a user explicitly requests brevity, including common phrasings and typos such as "explain X shortly", "briefly", or "birefly".

## Design

- Create a model-invoked skill at `skills/kiss/`.
- Use trigger metadata that covers concise-explanation requests; it should not activate for normal explanation requests.
- Limit the response to at most two short sentences.
- Lead with the direct definition or answer. Omit preambles, examples, caveats, and extra context unless necessary for correctness or safety.

## Scope

The skill is instruction-only. It needs no scripts, references, assets, or configuration.

## Validation

Validate the skill metadata and directory structure with the bundled skill validator. Check representative requests for the two-sentence limit and concise tone.
