# Section Templates — starter library

This folder holds reusable section starters for AIIMS web builds. It ships with the standard kit and is meant to **grow over time** — when a project produces a good or novel section, save a copy here.

See `references/section-templates.md` for the catalogue, the responsive contract, and how to use these.

## Standard kit (sections to keep starters for)

hero · logo-strip · features-grid · feature-split · testimonials · stats-band · process-steps · pricing · faq-accordion · cta-band · contact-form · footer

## Conventions

- Starters are stack-agnostic reference markup + notes. Adapt to the project's stack (PHP partial, Next.js component, Liquid section, WP block).
- Name files `<section>.<stack>.<ext>` when saving stack-specific versions, e.g. `hero.nextjs.tsx`, `faq-accordion.php`.
- Every saved template must already pass the responsive contract.
- Use brand tokens / CSS variables — no hardcoded hex.

## hero.example.html

A minimal, mobile-first hero starter is included as `hero.example.html` to show the expected pattern. Treat it as a reference, not a final design — `frontend-design` governs the actual aesthetic.
