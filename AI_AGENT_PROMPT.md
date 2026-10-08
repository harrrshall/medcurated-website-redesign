# Copy-paste prompt: migrate the original MedCurated website to the approved redesign

You are working in my original MedCurated website codebase. Implement the redesigned website using the reference code below. Do the implementation, validate it, and give me a complete reviewable result; do not stop at suggestions or a plan.

## References and source of truth

- Original website: https://www.medcurated.com/
- Approved redesigned website: https://medcurated-redesign.vercel.app/
- Reference repository: https://github.com/harrrshall/medcurated-website-redesign
- Reference files: `site/index.html`, `site/style.css`, `site/app.js`.

Use the supplied reference files as the visual, content and interaction source of truth. The live reference is supplementary and may change later. If the private reference repository is inaccessible, ask me for the three files or a repository ZIP; do not invent a replacement design.

My goal is to convert the original site into the current redesign while preserving the existing codebase's useful functionality and infrastructure. Port the reference into the existing stack. Do not replace the whole application with static HTML if the original uses a framework and working backend features.

## Audience and positioning

MedCurated sells to enterprise hospital teams in India: clinical leadership, IT, administrators and procurement.

The current approved positioning is an AI documentation layer for an existing HIS/EHR, with OPD note drafting and discharge-summary drafting. The clinician reviews and signs the output. Hospital hardware and private cloud are deployment options described in the source material.

Do not reposition it as a complete replacement EHR. If the original implementation reveals a material conflict with this positioning, flag the specific conflict and ask for a product decision before inventing claims.

Enterprise credibility should come from clear capabilities, defined integrations, deployment information, data controls and a useful demo. Do not add testimonials, customer logo walls, ratings, consumer-style social proof, or a testimonial section.

## Implementation approach

1. Read the existing repository instructions and identify its framework, homepage entry point, styles, navigation, assets and demo-booking implementation.
2. Inspect the three reference files and, when accessible, the rendered live redesign.
3. Identify the original site's working forms, booking endpoints, analytics, consent behavior, legal routes, metadata and external links. Preserve those capabilities unless the redesign explicitly replaces their presentation.
4. Implement the new homepage in the existing architecture. Reuse established components and dependencies where practical. Avoid unnecessary framework migrations or added libraries.
5. Preserve unrelated routes and application functionality. Replace the old homepage's outdated marketing content and decorative elements with the reference implementation.
6. Keep real credentials in existing environment-variable mechanisms. Do not copy `.env` files, Vercel credentials, deployment IDs, account IDs or private infrastructure metadata from another checkout.

## Visual requirements

Match the supplied redesign instead of creating another interpretation:

- White primary background and deep navy text/buttons.
- Main colours: navy `#14264b`, blue `#476bba`, ink `#182a48`, secondary text `#627086`, border `#dce3ee`, light surface `#f2f5fa`.
- DM Sans for body text and Manrope for headings, with system sans-serif fallbacks. Preserve readable loading behavior; use the existing framework's font tooling if appropriate.
- A compact, two-column desktop hero with the headline on the left and a large clinical-note example on the right.
- The hero headline is: “Clinical notes, ready for your review.” Preserve the reference hierarchy and responsive wrapping.
- Keep the opening close to the navigation. Do not reintroduce the large blank area above the hero.
- Modest corners, subtle borders, restrained shadows and generous but purposeful spacing.
- Use the dark navy deployment section and its simple data-flow diagram.
- Do not add gradients, floating AI decorations, stock doctor imagery, ECG landscape art, glassmorphism or gratuitous scroll animation.
- Do not add the “CLINICAL AI. BUILT FOR INDIA.” strapline or its square marker.
- Do not add numbered section eyebrows such as “01 / THE PLATFORM” or “02 / THE WORKFLOW”. The numbers on actual sequential workflow steps may remain.
- Keep section headlines descriptive and readable; avoid forced line breaks that break narrow layouts.
- Do not restore the inactive mock tabs inside the hero chart or the video-play icon beside the interactive walkthrough link.

## Content requirements

Use the current wording in the supplied reference as the baseline. Preserve its factual scope and plain-language style. Minor edits are allowed only to resolve grammar, layout or verified facts from the original codebase; do not perform another wholesale rewrite.

Copy should explain what the product does, what the clinician does, and what the hospital needs to evaluate. Avoid abstract slogans, repetition and “not X, but Y” framing.

Do not restore these original claims or themes without documented approval and evidence:

- 2.1 hours saved per clinician, 74% signed without edits, 92% same-day closure or inference latency below 400 ms.
- 40+ hospital partners, 12 exclusive partnerships or 8.2 million encounters.
- “A clinical data moat”, “reads like a senior resident”, “the chart closes itself”.
- “Data-sharing risk disappears”, “no third-party APIs, ever”, “no trace of your data”, or other unconditional security guarantees.
- Model-weight ownership, training-data rights, certification status or integrations inferred from marketing acronyms.

Do not invent statistics, guarantees, company addresses, customer names, security certifications, prices, supported-language lists or completed integrations. Preserve existing verified legal and corporate information where available.

Keep the distinction between production inference data and training data clear. Do not claim that local inference automatically settles retention, support access, telemetry or training questions.

## Homepage structure

Preserve the reference's current order:

1. Header: MedCurated identity, Platform, Workflows, Deployment, FAQs, and demo CTA.
2. Hero: direct product headline, short explanation, demo CTA, interactive-workflow link and fictional clinical-note example.
3. Compact capability strip.
4. OPD notes and discharge summaries: two concrete feature descriptions.
5. Interactive workflow: OPD and discharge tabs with three stages.
6. Hindi/English consultation example, clearly illustrative.
7. Deployment: on-premise/private cloud explanation, data-flow diagram, infrastructure, EHR access and data controls.
8. EHR integration: workflow mapping, integration scoping and clinician evaluation.
9. Practical FAQs.
10. Demo invitation and footer.

Retain the useful anchor IDs `top`, `platform`, `workflows`, `deployment`, `integrations`, `questions`, and `demo` where possible. The original website uses `#cta`; preserve old inbound links by supporting that anchor or mapping it to the real demo section. Handle old `#privacy` and `#data` links thoughtfully rather than leaving them broken or pointing to unrelated information. An actual privacy policy must remain a policy page, not merely a deployment marketing section.

## Functional requirements

### Walkthrough

Port both the markup and the behavior in `site/app.js`:

- OPD consultation and discharge-summary tabs switch the content.
- Selecting a tab resets its sequence to the first stage.
- Each of the three step buttons selects its corresponding panel.
- “Next step” advances through the stages; “Start again” returns to the first.
- Links from the feature cards select the correct workflow before navigating to it.
- Tab states, controlled-panel relationships and keyboard navigation remain accessible.
- The displayed clinical records and dialogue stay fictional and clearly labeled.
- Never imply that clicking through the illustration records audio, calls an AI model, saves a patient record or signs clinical documentation.
- Review states must not suggest a sample draft is already approved.

### Navigation and FAQs

- Internal links must resolve correctly and account for the sticky header.
- Mobile navigation opens and closes, updates its accessible name and expanded state, and closes after selecting a link.
- FAQs work with mouse, keyboard and touch.
- Preserve visible keyboard focus and skip navigation.
- Respect reduced-motion preferences.

### Demo booking — important migration requirement

The standalone reference links its final CTA to `https://www.medcurated.com/#cta` because it was hosted separately from the original site. Do not blindly retain that link when migrating onto the original domain: it could send visitors back to the same page instead of booking.

Inspect and reuse the original site's real demo form, calendar flow or booking endpoint. Connect the new CTA styling to that working flow. Preserve validation, submission states, error handling, consent and success behavior. Do not claim a demo request succeeded unless the backend confirms it. Do not send test requests to real staff without authorization.

If the original form has no functioning backend, report the missing connection clearly and retain an honest working contact route if one exists. Do not fabricate an email address or silently discard submissions.

Update the reference's “Opens the existing MedCurated website” note when booking is integrated locally. Keep the useful “No patient data needed” message.

## Readability, performance and responsive behavior

- Keep normal body text at least 16px where practical, clinical-example text at least 14px, and secondary metadata at least 12px.
- Use sufficient contrast for secondary text and borders. Do not shrink critical labels to fit.
- Check desktop and narrow screens around 390px and 320px; prevent horizontal page overflow.
- Check 200% text enlargement and keyboard navigation.
- Keep the clinical example readable on mobile. Stack sections and diagram elements using the reference's responsive behavior.
- Avoid extra animation frameworks, heavy assets or dependencies for this small marketing page.
- Avoid CSS font `@import` waterfalls; use font links with preconnects or the framework's font loader.
- Ensure the page remains informative if external fonts fail.
- Do not report a performance score or accessibility certification unless actually measured.

## Verification and delivery

Run checks appropriate to the existing stack, including its build and relevant existing tests. Do not add a large testing framework solely for this content migration.

Verify:

- The rendered page matches the reference's composition, colour, typography, content hierarchy and section order.
- No removed slogans, numbered section labels, fabricated metrics or testimonials were reintroduced.
- Both walkthrough tabs, all steps, restart, keyboard controls, feature links, mobile menu and FAQs work.
- All internal anchors and retained legal links are valid.
- The demo CTA reaches the real booking flow without a loop or fake success message.
- The page has no missing assets, blocking runtime errors or horizontal overflow.
- Title, description, favicon and canonical URL match the actual deployment destination. Do not make the Vercel reference URL canonical on the original domain.
- Existing analytics, legal pages, backend integrations and unrelated routes remain intact.

Provide a concise final summary of what changed, how it was verified, and any factual or integration items that still require my input. Include desktop and mobile screenshots if your environment supports them. Follow the original project's deployment workflow; do not replace production DNS, change account access or publish to a different hosting account without explicit authorization.

## Confidentiality and publication boundary

Keep this migration limited to website source and approved public-facing content. Do not commit, upload, paste into prompts, or expose in browser code any secrets, authentication tokens, environment files, private keys, internal endpoints, infrastructure identifiers, private customer or employee details, real patient records, production logs, database exports, contracts or unpublished business information.

Treat private repository access as a delivery mechanism, not permission to include sensitive information. Use fictional records in all examples. Keep implementation guidance in repository documentation rather than displaying it to website visitors. Before committing or publishing, inspect the exact changed files for sensitive content, including source maps and generated assets. If a fact is internal or its publication status is unclear, omit it and ask the owner rather than publish it. Do not change repository visibility or grant access without explicit authorization.
