# Contributing

This is the public docs site for [Overshoot](https://overshoot.ai). It's open so you can suggest fixes — typos, broken links, unclear explanations, missing examples.

## Quick edits

Click the pencil icon at the top of any page on docs.overshoot.ai to edit on GitHub and open a PR.

## Local development

```bash
npm i -g mint
mint dev
```

Preview at `http://localhost:3000`. Run `mint broken-links` before opening a PR.

## Writing style

See [`AGENTS.md`](./AGENTS.md) — it covers voice, the human/agent visibility split, and canonical URL conventions. The short version:

- Active voice, second person.
- One idea per sentence.
- Concrete numbers, not adjectives.
- No emoji, no hedges, no "we recommend".

If your change touches API behavior, update [`api-reference/openapi.yaml`](./api-reference/openapi.yaml) too — it drives the reference pages.
