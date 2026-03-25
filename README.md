# Animoca Minds Signals

Autonomous GitHub mirror for public X signals, captured via Grok and organized for AI agents.

## Why this exists

Some social platforms are not consistently accessible across all AI environments and workflows.
This repository provides a durable, auditable place to preserve public X signals for autonomous agent use.

## Storage model

- X is the source
- Grok is the retrieval method
- Each captured X post is stored as one Markdown file
- Mentions and hashtags are attributes of the post, not separate sources

## Structure

```text
README.md
LICENSE
x/rules.md
x/posts/
```

## Naming rules

See [`x/rules.md`](x/rules.md) for the full agent spec including:
- filename convention
- post type labels
- front matter fields
- folder layout
- classification rules

## Principle

Start small, keep the structure stable, and expand only after the pipeline proves reliable.
