# CLAUDE.md — [CLIENT / PROJECT NAME]

> Project facts and rules for Claude Code. Keep this file tight — under ~200 lines.
> CLAUDE.md = *what to do* and *project context*. settings.json = *what Claude is allowed to do*.
> Fill every [BRACKETED] placeholder before starting. Delete guidance lines once filled.

## Project

- **Client:** [client name]
- **Project type:** [custom website | wordpress | landing page | ecommerce-woocommerce | ecommerce-shopify]
- **Deliverable:** [e.g. 1 landing page | 12-page site redesign | Shopify store]
- **Status:** [brief / in build / QA / staging review / live]
- **Live URL:** [domain] · **Staging URL:** [staging domain]

## Tech stack

- **Stack:** [Next.js 14 + Tailwind | PHP + Tailwind CSS 4 + JS | WordPress | Shopify]
- **Boilerplate / base:** [tw-landing-boilerplate | fresh Next.js | base theme name]
- **Hosting:** [host name + whether it supports Node]
- **Repo:** [git URL]
- **Deploy method:** [Vercel preview→prod | cPanel zip upload | etc.]

## How we build here

This project follows the **`aiims-web-build`** skill. Claude Code must:

1. Run intake before any code (the skill enforces this).
2. Build section by section, mobile-first, perfect responsiveness on all devices.
3. No AI slop — pull inspiration, design custom. Never ship a generic template.
4. Never hallucinate — if unsure about a path, API, brand detail, or the brief, STOP and ask.
5. Run the pre-launch QA checklist on staging before anything goes live.
6. Close out every project: em-dash sweep, handoff list, improvement suggestions.

Do not override the `aiims-web-build` skill or the boilerplate's own CLAUDE.md — follow them.

## Brand

- **Primary color:** [hex] · **Secondary:** [hex] · **Accent:** [hex]
- **Fonts:** [heading font] / [body font]
- **Logo files:** [path or "client to supply — see handoff"]
- **Tone of voice:** [e.g. confident, plain-English, no jargon]
- **Copy rules:** No em dashes. No AI filler ("elevate", "unleash", "in today's fast-paced world"). Australian English spelling.

## Integrations

- **Forms go to:** [email address | HubSpot | other]
- **Tracking:** [GTM ID] · [GA4 ID] · [Meta Pixel ID]
- **Other:** [booking tool, chat widget, etc.]

## Conventions

- **Branch naming:** [e.g. feature/<section>]
- **Commit style:** [e.g. conventional commits]
- **File/folder structure:** [anything non-obvious about this repo]
- **Component/section naming:** [project convention]

## Do / Don't

- **Do:** [project-specific must-dos]
- **Don't:** [project-specific landmines — e.g. "don't touch /legacy", "client hates carousels"]

## Open questions / decisions pending

- [anything unresolved — keep this current so nothing gets silently guessed]
