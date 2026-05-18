# Section Templates — catalogue & responsive contract

AIIMS sites are assembled from a consistent section kit. This file is the catalogue. Starter markup lives in `assets/section-templates/`. Adapt to brand + stack; never ship a section that fails the responsive contract below.

## The standard section kit

| Section | Purpose | Key responsive behaviour |
|---|---|---|
| `hero` | First impression, headline + primary CTA | Mobile: stacked, headline scales down, CTA full-width-ish, hero image below or as background. Desktop: side-by-side or contained centered. |
| `logo-strip` | Trust — client/partner logos | Mobile: 2–3 per row or horizontal scroll. Desktop: single row, evenly spaced. |
| `features-grid` | 3–6 feature cards | Mobile: 1 column. Tablet: 2 columns. Desktop: 3 (or 3+) columns. |
| `feature-split` | Alternating image/text rows | Mobile: image always above text, every row. Desktop: alternate left/right. |
| `testimonials` | Social proof | Mobile: 1 per view, swipeable. Desktop: 2–3 across or a slider. |
| `stats-band` | Headline numbers | Mobile: 2 per row stacked. Desktop: single row. |
| `process-steps` | How it works, numbered | Mobile: vertical list. Desktop: horizontal stepper. |
| `pricing` | Plan/tier cards | Mobile: 1 column, highlighted plan first. Desktop: side-by-side. |
| `faq-accordion` | Expandable Q&A | Same pattern all sizes; tap targets ≥44px; one-column always. |
| `cta-band` | Mid/end conversion push | Headline + CTA; CTA never overflows on mobile. |
| `contact-form` | Lead capture | Mobile: single column fields, large inputs. Labelled, accessible. |
| `footer` | Nav, contact, legal | Mobile: stacked column groups. Desktop: multi-column row. |

## Responsive contract — every section must pass

- **Mobile (≤640px):** single-column unless explicitly a 2-up; no horizontal scroll; tap targets ≥44px; body text ≥16px; media scales within viewport.
- **Tablet (641–1024px):** sensible reflow — 2-up where 3-up is cramped; no dead space.
- **Desktop (≥1025px):** intended layout; content max-width contained; no edge-to-edge text lines.

Always build **mobile-first**: base styles = mobile, layer up for larger screens. Never desktop-first with `max-*:` patches.

## Known failure points to check on every section

Long words/headings overflowing · buttons wider than their container · fixed-width images · tables on mobile · sticky header overlapping content on scroll · form fields too small to tap · grid items not collapsing.

## How to use the library

1. Before building any section, check `assets/section-templates/` for a starter.
2. **Gather inspiration** — look at 2–3 strong references for that section type (21st.dev, Awwwards, Godly, Land-book, Mobbin, Lapa Ninja, strong agency sites). Identify what makes them good, then design something custom — never ship the bare starter, never copy a reference. A generic-looking section is AI slop and must be redone.
3. Adapt to the project's brand tokens and chosen stack (PHP partial, Next.js component, Liquid section, WP block/template part).
4. Verify the responsive contract.
5. If the project produced a notably good or novel variant, save it back to the library so future builds start ahead.

## Accessibility baseline (applies to all sections)

Real semantic headings in order · `alt` text on all meaningful images · form fields with associated `<label>`s · visible focus states · sufficient color contrast · interactive elements reachable by keyboard.
