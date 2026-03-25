# X Storage Rules

This file defines how X content must be stored in this repository.
Agents must follow these rules exactly.

## Core rules

- Store one Markdown file per captured X post.
- Do not combine multiple unrelated posts into one file.
- Mentions and hashtags are attributes of the post, not separate sources.
- The source is always `x`.
- Prefer append-only behavior.
- If two captures refer to the same post ID, update the existing file instead of creating a duplicate.

## Folder layout

Store posts by publish date:

```text
x/posts/YYYY/MM/DD/
```

Example:

```text
x/posts/2026/03/25/
```

## Filename convention

```text
x-YYYYMMDD-HHMMSS-@handle-type-postid.md
```

Example:

```text
x-20260325-160912-@animocabrands-original-1903512345678901234.md
```

## Allowed types

- `original`
- `reply`
- `retweet`
- `quote`
- `thread-reply`

## Type definitions

- `original`: a normal standalone post, including the first post of a thread
- `reply`: a post replying to another post from a different author or conversation
- `retweet`: a repost without added commentary
- `quote`: a post quoting another post with added commentary
- `thread-reply`: a follow-up post by the same author in the same thread

## Classification order

Use this order when deciding the type:

1. If the post is a repost without added text → `retweet`
2. Else if the post quotes another post → `quote`
3. Else if the post is a follow-up by the same author in the same thread → `thread-reply`
4. Else if the post replies to another post → `reply`
5. Else → `original`

## Filename rules

- Use lowercase only where applicable.
- Use hyphens as separators.
- Do not use spaces.
- Keep the `@` in the handle segment.
- Always include the source post ID at the end before `.md`.
- Do not include hashtags, mentions, or titles in the filename.

## Required front matter

Every file must begin with YAML front matter:

```yaml
***
source: x
retrieved_via: grok
type: original
post_id: "1903512345678901234"
author_handle: "animocabrands"
author_name: "Animoca Brands"
published_at: "2026-03-25T16:09:12Z"
conversation_id: "1903512345678901234"
reply_to_post_id:
quoted_post_id:
retweeted_post_id:
url: "https://x.com/animocabrands/status/1903512345678901234"
hashtags: []
mentions: []
***
```

## Body format

After the front matter, store the post content in plain Markdown:

```md
Post text goes here.
```

Optional agent notes may follow:

```md
## Notes

- Optional extracted links
- Optional agent summary
```

## Examples

```text
x/posts/2026/03/25/x-20260325-160912-@animocabrands-original-1903512345678901234.md
x/posts/2026/03/25/x-20260325-161015-@animocabrands-reply-1903512987654321098.md
x/posts/2026/03/25/x-20260325-161122-@animocabrands-retweet-1903513555555555555.md
x/posts/2026/03/25/x-20260325-161430-@animocabrands-quote-1903514777777777777.md
x/posts/2026/03/25/x-20260325-170145-@animocabrands-thread-reply-1903520666666666666.md
```
