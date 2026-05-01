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

## Terminology

Use these terms consistently. Don't invent synonyms.

- **Stream** — a leased live-video session. Opened via `POST /streams`, inspected via `GET /streams/{id}`, renewed via `POST /streams/{id}/keepalive`, deleted via `DELETE /streams/{id}`. Capitalised when referring to the entity; lowercase in compound nouns ("stream id", "stream lifecycle").
- **`stream_id`** — UUID returned by `POST /streams`. Use this exact spelling in code and prose; not "streamId" or "stream ID".
- **`frame_index`** — integer index into a Stream's retained frames. `frame_index=-1` means the most recent frame. `0` is the first retained frame.
- **`start_offset_ms` / `end_offset_ms`** — millisecond offsets used to reference a segment. Negative values are relative to the live edge (`-5000` = 5 seconds ago). Omit `end_offset_ms` to mean "now".
- **Lease** — the keepalive window for a Stream. Default 5 minutes idle; renewed by `/keepalive`.
- **Keepalive** — the act of renewing a Stream's lease. Also returns a fresh LiveKit token for reconnects.
- **Model id** — `provider/model-name` format, e.g. `google/gemma-4-E4B-it`. Pass verbatim as the `model` field on `/chat/completions`.
- **LiveKit room** — the WebRTC publish target returned by `POST /streams`, consisting of a `wss://` URL and a short-lived JWT token.

## Voice

- Active voice, second person.
- One idea per sentence. Cut hedges ("you can", "we recommend", "feel free to").
- Concrete numbers over adjectives. "5 minutes" not "a short while".
- Inline backticks for entities, endpoints, and field names: `Stream`, `/streams`, `frame_index`.
- Sentence case headings.
- No emoji. No marketing fluff.
- Page `description` frontmatter: one sentence, ≤140 characters, ends with a period. Used verbatim in `llms.txt`.
- ASCII quotes (`'` and `"`), not smart quotes — LLMs and copy-paste consumers reproduce them verbatim.
- Don't wrap URLs in angle brackets inside code blocks (`<https://...>` breaks copy-paste).

## Canonical URLs

- Base URL: `https://api.overshoot.ai/v1beta`
- Stream media reference: `ovs://streams/{stream_id}?<anchor>` (a reference identifier the server parses, not a fetchable URL)
- Dashboard: `https://platform.overshoot.ai`

Use these consistently. Don't mix `dev-api` or `/v1` into customer-facing pages.

## What not to document

- Internal-only endpoints (`/spectate`, `/feedback`, `/info`, `/config/prompt`).
- Stream behavior beyond what the public API guarantees.
- Implementation details of the inference router.
- Anything related to internal admin tooling, the dev portal, or backend microservice architecture.

## When in doubt

If a term, limit, or behaviour isn't already documented in `chat-completion.mdx`, `the-stream.mdx`, `models.mdx`, `quickstart.mdx`, or `api-reference/openapi.yaml`, leave a `<!-- TODO: confirm with Zakaria -->` HTML comment instead of guessing.

## Agent-readability

This site is consumed by agents through Mintlify's auto-generated `/llms.txt`, `/llms-full.txt`, per-page `.md` exports, and the contextual menu (`copy`, `chatgpt`, `claude`, `perplexity`, `cursor`, `vscode`). Keep `description` frontmatter tight, keep code blocks copy-pasteable, and use `<Visibility for="agents">` blocks for guidance that shouldn't appear in the human UI.
