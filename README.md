# Overshoot Docs

Public documentation for [Overshoot](https://overshoot.ai). Built on [Mintlify](https://mintlify.com).

## Develop locally

```bash
npm i -g mint
mint dev
```

Serves at `http://localhost:3000`.

## Project layout

```
docs/
├── docs.json                # Site config: nav, theme, logo, footer
├── intro.mdx                # Top of "Guides" tab
├── quickstart.mdx
├── the-stream.mdx
├── chat-completion.mdx
├── models.mdx
├── best-practices.mdx
├── api-reference/
│   ├── introduction.mdx
│   ├── openapi.yaml         # Drives the API reference pages
│   └── *.mdx                # Per-endpoint pages (frontmatter only)
├── logo/                    # Wordmarks (light / dark)
├── favicon.svg
└── AGENTS.md                # Style guide for contributors and AI agents
```

## Writing

See [`AGENTS.md`](./AGENTS.md) for voice, the human/agent split via `<Visibility>`, and canonical URLs.

## Publishing

Pushes to the default branch deploy automatically via the Mintlify GitHub app.
