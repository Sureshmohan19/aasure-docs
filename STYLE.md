# Aasure docs — style & templates

Modeled on Stripe's docs. **This file is the reusable template** — copy an archetype
below when adding a page. It is not part of the site (not in `docs.json` navigation).

## Two systems

- **Guides** — conceptual + how-to pages, written in MDX. Most pages live here.
- **API Reference** — auto-rendered from the live OpenAPI spec (`docs.json` → `openapi`
  → `https://biz.aasure.app/api/v1/openapi.json`). **Don't hand-write endpoint pages**;
  add the resource's endpoints to the API Reference tab and Mintlify renders the params,
  request/response, and playground from the spec.

Single version (v1) for now. The nav is structured so a Mintlify version dropdown drops
in later without moving pages.

## Conventions

- **Frontmatter** — every page has `title` + a one-sentence `description` (shows in search and nav).
- **Voice** — second person, present tense; imperative for steps. Short sentences, no marketing fluff.
- **Code** — request examples use `<CodeGroup>` with **cURL → TypeScript → Python**, in that order.
  Use the real endpoint and the `aas_live_…` / `YOUR_BUSINESS_ID` placeholders.
- **Callouts** — `<Note>` for asides, `<Warning>` for footguns / irreversible actions, `<Tip>` for
  best practice. One idea per callout; don't stack them.
- **Params & fields** — tables (name · type · required · description), or `<ParamField>` in API contexts.
- **Cross-links** — end a concept/feature page with a "Next steps" `<CardGroup>`.
- **URLs are contracts** — don't move or rename a published page. The API's error
  `documentation_url` points at `/errors/*`; relocating a page breaks live links. Add, don't relocate.

---

## Archetype — Concept page

````mdx
---
title: Idempotency
description: One sentence: what this is and why the reader cares.
---

Short intro paragraph — what it is, when it matters.

## How it works

Prose + a table or `<CodeGroup>` where useful.

<Warning>
  Call out the one thing that bites people.
</Warning>

## Next steps

<CardGroup cols={2}>
  <Card title="Related page" icon="book" href="/related" />
  <Card title="API reference" icon="code" href="/api-reference/..." />
</CardGroup>
````

## Archetype — Guide (how-to)

````mdx
---
title: Create your first booking
description: One sentence describing the outcome.
---

One line on what you'll build and the prerequisite (e.g. an API key).

<Steps>
  <Step title="Do the first thing">
    Prose, then the request:

    <CodeGroup>
    ```bash cURL
    curl ...
    ```
    ```typescript TypeScript
    ...
    ```
    ```python Python
    ...
    ```
    </CodeGroup>

    What a success response looks like.
  </Step>
  <Step title="Do the next thing">
    …
  </Step>
</Steps>

## Next steps
<CardGroup cols={2}>…</CardGroup>
````

## Archetype — Feature overview

````mdx
---
title: Bookings
description: One sentence on what the feature does.
---

What the feature is, in two sentences.

## Key concepts

| Concept | What it means |
|---|---|
| … | … |

## Common tasks

<CardGroup cols={2}>
  <Card title="Create a booking" icon="plus" href="/features/bookings#create" />
</CardGroup>

## API

Link to the relevant API Reference endpoints.
````

## Archetype — API reference

Auto-generated. Add the resource's endpoints under the **API Reference** tab in `docs.json`;
Mintlify renders everything from the OpenAPI spec. No MDX per endpoint.
