# MedCurated website redesign

The reference implementation of the MedCurated marketing website, created on 8 October 2026.

- Live reference: https://medcurated-redesign.vercel.app/
- Original website being replaced: https://www.medcurated.com/
- Migration instructions: [AI_AGENT_PROMPT.md](AI_AGENT_PROMPT.md)

## Source

`site/index.html`, `site/style.css`, and `site/app.js` are the current redesigned site. They are plain HTML, CSS and JavaScript with no package installation or build step. Google Fonts supplies DM Sans and Manrope; system sans-serif fonts are the fallback.

This repository contains the redesign, not the original website's codebase. Give the original codebase and this repository to the implementation agent. The original site's backend, forms, analytics, legal pages and integrations must be inspected and preserved as appropriate during migration.

## Preview locally

From the repository root:

```sh
python3 -m http.server 4318 --directory site
```

Open http://localhost:4318.

## Deployment

`vercel.json` serves `site/` as a static site. No environment variables are required for this reference. The existing Vercel deployment was uploaded using the CLI; this new repository is not automatically connected to that Vercel project.

## Known boundaries

- The clinical records, dialogue and architecture are illustrative. There is no AI inference, recording, clinical data processing or EHR connection in this marketing-site code.
- The demo CTA currently opens the original MedCurated website at `https://www.medcurated.com/#cta`. When migrating into the original site, wire the CTA to its real booking flow instead of retaining this link, which could become self-referential.
- No customer testimonials, fabricated metrics, customer logos, compliance certifications or made-up integration lists are included.
- Current copy describes an AI documentation layer for existing HIS/EHR systems. It does not position the product as a replacement EHR. Product owners should confirm factual capabilities before launch on the original domain.
- No production secrets, Vercel tokens, Sites credentials or real patient data are included.

## Visual direction

Navy and white; muted blue accents; readable clinical examples; compact opening; direct product descriptions. The enterprise audience evaluates capabilities, integration, deployment and governance. Do not add consumer-style social proof or generic AI slogans.
