---
name: aiims-web-build
description: The AIIMS Group web development workflow. Use this skill at the START of ANY website, landing page, or web build task — and any time the user mentions building, redesigning, or shipping a site, landing page, WordPress theme, custom site, or ecommerce store (WooCommerce or Shopify). It establishes the project type, locks in the correct tech stack and boilerplate, enforces flawless responsiveness, builds reusable section templates, scans past work to move faster, and runs the pre-launch QA checklist before anything goes live. Trigger this even when the user just says "build me a page", "start a new project", "redo this site", or names a client and a deliverable — do not start writing code until this skill's intake step is done.
---

# AIIMS Web Build

This skill is the standard operating procedure for every web build at AIIMS Group. Its job is to make sure that before a single line of code is written, the project type is known, the right stack is chosen, and past work is reused — and that before anything ships, it has passed QA.

The skill does not replace `frontend-design` (aesthetic quality) or the boilerplate's own `CLAUDE.md` (project-internal rules). It sits *above* them: it routes the project to the right setup and enforces the process.

## The non-negotiables

These apply to every build regardless of type:

1. **Never start coding before intake is complete.** Always ask the four intake questions and get answers first — every project, no exceptions. See "Step 1".
2. **Never hallucinate — stop and ask if unsure.** Do not invent file paths, API behaviour, client details, brand colors, content, or how a host/plugin/integration works. If you don't know something or the brief is ambiguous, STOP and ask the user a specific question. A wrong guess that gets built on is far more expensive than a question. Guessing is never acceptable; asking always is.
3. **No AI slop — ever.** Every build must look genuinely, custom-designed. Generic AI aesthetics are a failure condition, not a style choice. See "Step 3" and "Build quality".
4. **Perfect responsiveness is not optional.** Every component, every section, every page works on mobile (≤640px), tablet (641–1024px), and desktop (≥1025px). This is verified, not assumed. See "Step 5".
5. **Build in sections, not whole pages.** One section at a time → tighter markup, reusable templates. See "Step 4".
6. **Reuse before you rebuild.** Scan past work first. See "Step 2".
7. **Nothing goes live without the launch checklist.** See "Step 6".
8. **Every project ends with a close-out.** Handoff list, content sweep, and improvement suggestions. See "Step 7".

## Step 1 — Intake (always ask, every project)

Before anything else, ALWAYS ask these four questions — even if the conversation seems to already imply some answers. Do not skip them and do not infer. A wrong assumption about hosting or project type causes a full rebuild, so the 30 seconds it takes to confirm is always worth it. If the user did mention something (e.g. "a Shopify store"), still ask — but you can pre-fill that answer and let them confirm rather than starting blank.

1. **Project type** — one of: `custom website`, `wordpress`, `landing page`, `ecommerce-woocommerce`, `ecommerce-shopify`.
2. **Hosting environment** — what server/host will this live on? This decides the stack (see routing table). For landing pages and custom sites especially: does the host support Node/modern frameworks, or is it traditional PHP shared hosting?
3. **Source of truth for design** — Figma file/frame, existing site to redesign, written brief, or build-from-scratch.
4. **Forms & integrations** — does it need a contact form, CRM push (HubSpot), booking (Cal.com), tracking (GTM/GA4/Meta Pixel)?

Ask all four as one concise batch — tappable options or a short numbered list, never a wall of prose. The user prefers to select, not type. Wait for the answers before doing anything else. Do not begin Step 2 or write any code until all four are answered.

### Stack routing table

| Project type | Default stack | Boilerplate / base |
|---|---|---|
| Landing page — host supports Node | Next.js 14 + Tailwind | fresh Next.js + Tailwind setup |
| Landing page — PHP shared host | PHP + Tailwind CSS 4 + JS | **`github.com/KuyaLoy/tw-landing-boirlerplate`** |
| Custom website — host supports Node | Next.js 14 + Tailwind | fresh Next.js + Tailwind setup |
| Custom website — PHP shared host | PHP + Tailwind CSS 4 + JS | the tw-landing boilerplate, extended to multi-page |
| WordPress | WordPress theme/build | per project — confirm theme/builder with user |
| Ecommerce — WooCommerce | WordPress + WooCommerce | per project |
| Ecommerce — Shopify | Shopify (Liquid / theme) | per project |

**Rule for modern stack: always Next.js 14 + Tailwind.** Do not substitute another framework unless the user explicitly asks.

**Rule for PHP: always the tw-landing boilerplate.** It ships with WebP/AVIF image helpers, a secure form handler (reCAPTCHA v3, honeypot, header-injection-safe), `$basePath` auto-pathing, and its own `CLAUDE.md`. Do not hand-roll a PHP landing page. After cloning it, read its `CLAUDE.md` and `README.md` and follow them — they own path conventions, CSS placement, and the form handler.

Once the stack is decided, read the matching reference file before building:
- PHP boilerplate builds → `references/php-boilerplate.md`
- Next.js builds → `references/nextjs-stack.md`
- WordPress / WooCommerce → `references/wordpress-woo.md`
- Shopify → `references/shopify.md`

## Step 2 — Scan past work

Before building, look for prior art so you match established patterns and move faster. Two sources:

1. **Past Claude Code sessions / project history.** If a project history or transcript search is available, look for how AIIMS has built similar things — same client, same vertical (trades, dental, solar, finance, hospitality), or same component. Reuse naming conventions, file structure, and proven section patterns. Do not reinvent decisions that were already made well.
2. **The section template library.** `assets/section-templates/` ships starter templates (see Step 3). Check there before writing a hero, features grid, testimonials block, FAQ, or CTA from scratch.

If you find a close past build, briefly tell the user what you're reusing and why ("matching the Everclear landing page structure — hero + 3-feature grid + form, same as last time") so they can correct you fast if the context is wrong.

## Step 3 — Section templates

AIIMS sites are assembled from a consistent kit of sections. The skill ships starter templates in `assets/section-templates/`; each project extends them rather than starting blank.

Standard section kit: `hero`, `logo-strip`, `features-grid`, `feature-split` (alternating image/text), `testimonials`, `stats-band`, `process-steps`, `pricing`, `faq-accordion`, `cta-band`, `contact-form`, `footer`.

How to use them:
- Each starter template is stack-agnostic guidance + reference markup. Read `references/section-templates.md` for the catalogue and the responsive contract each section must honour.
- When you build a section for a real project, adapt the template to the brand and the chosen stack, then — if it's a notably good or novel pattern — save the project-specific version back so the library improves over time.
- Never ship a section that hasn't passed the responsiveness contract in Step 5's checklist.

### Build quality — no AI slop

A starter template is a *skeleton*, not the finished product. Shipping a section that looks like a generic template is a failure. Every section must be custom-designed and memorable.

Before building any section, gather inspiration. Look at how the best in the industry execute that section type — sites like **21st.dev**, **Awwwards**, **Godly**, **Land-book**, **Mobbin**, **Refero**, **SaaS Landing Page**, **Lapa Ninja**, or the live sites of strong agencies. Find 2–3 references for the section you're about to build, identify *what specifically* makes them good (the layout tension, the type treatment, the motion, the use of space), then design something original that captures that quality for this brand. Do not copy a reference — synthesise from several into something custom.

Failure conditions — a section is AI slop and must be redone if it has:
- Generic fonts (Inter, Roboto, Arial, system stacks) used without intent.
- Cliché palettes — especially purple gradients on white.
- Predictable, evenly-spaced, centered-everything layouts with no compositional tension.
- Solid flat backgrounds everywhere with no atmosphere, depth, or texture.
- Cookie-cutter card grids that could belong to any site.

What good looks like: a clear, bold aesthetic direction; distinctive typography; intentional color with real accent contrast; considered spacing and asymmetry; high-impact motion at key moments; details (texture, depth, custom shapes) that make it feel designed for *this* client and no one else.

Defer to the `frontend-design` skill for the depth of aesthetic execution — load it and use it. This skill's job is to make the anti-slop bar non-negotiable; `frontend-design` is how you clear it.

## Step 4 — Build, section by section

Build one section at a time, in document order: hero → next section → … → footer. After each section:
- Verify it against the three breakpoints (see "Responsiveness").
- Keep the markup semantic and accessible (real headings, alt text, labelled form fields, focus states).
- Use the project's brand tokens (CSS variables / Tailwind theme), never hardcoded hex values scattered through markup.

For Figma-sourced builds, build the frame for one section, implement it, verify, then move to the next frame. Aim for ~95% pixel fidelity — snap Figma's odd values to the nearest scale step rather than chasing exact pixels.

Defer to `frontend-design` for aesthetic decisions (typography, color, motion, composition). This skill governs *process and structure*; `frontend-design` governs *how it looks*.

## Step 5 — Responsiveness

Responsiveness is a verified deliverable, not a hope. The contract:

- **Mobile (≤640px):** single-column, tap targets ≥44px, no horizontal scroll, text ≥16px body, images scale within viewport, nav collapses to a working menu.
- **Tablet (641–1024px):** layouts reflow sensibly — 2-up grids where 3-up is too tight, no awkward dead space.
- **Desktop (≥1025px):** intended full layout, content max-width contained, no edge-to-edge text lines.

Verify, don't assume. For each section and the assembled page:
- Mentally (or with dev tools / a script) walk all three breakpoints.
- Check the known failure points: long words/headings, overflowing buttons, fixed-width images, tables, horizontal scroll, sticky headers overlapping content, forms on small screens.
- Tailwind: build mobile-first (`base` = mobile, then `sm:` `md:` `lg:` overrides). Never desktop-first with `max-*:` patches.

If anything breaks at any breakpoint, it is not done.

## Step 6 — Pre-launch QA checklist

Nothing is "ready" until this passes. This is the AIIMS landing-page launch process, generalised. Run it on staging before requesting client approval. For each item, report PASS / FAIL / N/A with a note.

1. **Hosting compatibility** — confirmed the host supports the stack used (Node/Next.js vs PHP). If mismatched, the stack was wrong — fix before proceeding.
2. **Responsive testing** — desktop, tablet, mobile all verified per the Step 5 contract.
3. **Form testing** — every form submits; submissions arrive at the correct email/CRM/platform. Email auth checked (SPF, DKIM, DMARC) to avoid spam filtering. Flag if client SMTP credentials are needed.
4. **Tracking & analytics** — GTM, GA4, Meta Pixel, and any conversion scripts installed and firing. Thank-you page fires the conversion event.
5. **SEO checks** — page title, meta description, image ALT tags, OG image, thank-you page, and any required redirects all present and correct.
6. **Performance audit** — run a PageSpeed/Lighthouse audit; review Performance, Accessibility, Best Practices, SEO. Address regressions.
7. **Final staging review** — all changes tested and approved on staging.

Only after every applicable item passes and the client has approved is the build ready to push live.

The full annotated checklist — including how to interpret each item for non-launch-page project types — is in `references/launch-checklist.md`. Read it before running QA.

## Step 7 — Project close-out

Every project ends here. After QA passes, before you consider the work delivered, do three things and present them to the user together.

### 7a. Content sweep — em dashes and AI tells

Sweep all copy in the build — every page, partial, component, content file — for em dashes (`—`). Em dashes are an AI-writing tell and AIIMS copy should not contain them. Replace each with the punctuation the sentence actually needs: a comma, a colon, parentheses, a full stop, or a restructured sentence. Do not blindly swap `—` for `-`; choose what reads correctly.

While sweeping, also catch other AI tells in copy: "elevate", "unleash", "in today's fast-paced world", "look no further", "nestled", over-hedged phrasing, and robotically uniform sentence rhythm. Fix what you find. Report what was swept.

### 7b. Handoff list — what the user needs to do

List everything the project needs from the user or client that you could not do yourself. Be specific and actionable. Common items:
- **Assets to source** — real photography, logo files, brand fonts, product images (flag every placeholder still in the build and where it is).
- **Credentials & access** — SMTP details, CRM/HubSpot keys, GA4/GTM/Pixel IDs, domain/DNS access, hosting login.
- **Content gaps** — copy still using placeholder/lorem text, missing legal pages, missing testimonials.
- **Decisions pending** — anything you flagged with a question during the build that's still open.
- **Deploy actions** — DNS changes, SSL, domain connection, anything only the account owner can do.

Present this as a clear checklist the user can action. If there's nothing outstanding, say so explicitly.

### 7c. Improvement suggestions

Always end with suggestions on how to make the build better — things beyond the brief that would genuinely improve the result. Think about: conversion (stronger CTA placement, social proof, trust signals), performance, SEO depth, accessibility wins, content that's thin, sections that could be added, A/B test ideas, or follow-up work worth quoting the client for. Offer 3–6 concrete, specific suggestions — not vague platitudes. The user decides what to act on; your job is to surface the opportunities.

## Quick reference — what to do when

| Situation | Do this |
|---|---|
| User asks to build/redesign anything web | Start at Step 1 — always ask the 4 intake questions before any code |
| Project type seems obvious from context | Still ask — pre-fill the likely answer, let the user confirm |
| Unsure about anything — a path, an API, a brand detail | Stop and ask a specific question. Never guess or hallucinate |
| PHP landing page | Clone tw-landing boilerplate, read its CLAUDE.md, read `references/php-boilerplate.md` |
| Modern stack | Next.js 14 + Tailwind, read `references/nextjs-stack.md` |
| Need a hero/features/FAQ/etc. | Pull 2–3 inspo references (21st.dev, Awwwards, etc.), then design custom — no slop |
| Section built | Verify 3 breakpoints before moving on |
| About to go live | Run Step 6 checklist on staging — no exceptions |
| Build done, QA passed | Run Step 7 close-out: em-dash sweep, handoff list, improvement suggestions |
