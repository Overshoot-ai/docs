# Documentation project instructions

## About this project

- Public docs for [Overshoot](https://overshoot.ai), a real-time vision API.
- Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter; configuration lives in `docs.json`.
- Run `mint dev` to preview locally; `mint broken-links` to verify links.

## Two audiences per page

Most pages are written once and rendered for two audiences via the [`<Visibility>`](https://www.mintlify.com/docs/components/visibility) component:

- `<Visibility for="humans">` — concise, scannable, opinionated. What a person needs to feel oriented.
- `<Visibility for="agents">` — exhaustive. Every field, every edge case, every value. No prose padding.

Content that serves both can sit outside any `Visibility` block. Use the wrappers only when the human and agent versions genuinely diverge.

## Voice

- Active voice, second person.
- One idea per sentence. Cut hedges ("you can", "we recommend", "feel free to").
- Concrete numbers over adjectives. "5 minutes" not "a short while".
- Inline backticks for entities, endpoints, and field names: `Stream`, `/streams`, `frame_index`.
- Sentence case headings.
- No emoji. No marketing fluff.

## Canonical URLs

- Base URL: `https://api.overshoot.ai/v1beta`
- Stream media URL: `https://api.overshoot.ai/v1beta/streams/{stream_id}/media?<anchor>`
- Dashboard: `https://platform.overshoot.ai`

Use these consistently. Don't mix `dev-api` or `/v1` into customer-facing pages.

## What not to document

- Internal-only endpoints (`/spectate`, `/feedback`, `/info`, `/config/prompt`).
- Stream behavior beyond what the public API guarantees.
- Implementation details of the inference router.
