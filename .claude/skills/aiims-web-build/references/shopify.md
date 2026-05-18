# Shopify

Use this when the project type is `ecommerce-shopify`.

## Before building — confirm with the user

1. **Theme approach** — customising an existing theme (Dawn or a premium theme) vs a fully custom theme? Most projects: start from a solid base theme and customise.
2. **Existing store or fresh?**
3. **Apps in scope** — reviews, upsell, subscriptions, etc. Keep the app stack lean; each app adds weight.
4. **Product source** — manual, CSV import, or a dropshipping supplier integration.

## How Shopify builds work

- Themes are **Liquid** + JSON templates + sections. The section kit maps directly to Shopify sections.
- Build/customise **sections**; expose content via the theme editor's section settings/blocks so the client can edit without code.
- Use the theme's existing design tokens (settings_schema / CSS variables) for brand colors and type — keep it consistent.

## Principles that still apply

- **Section thinking is native here** — Shopify is literally section-based. Build the standard kit (hero, features, testimonials, FAQ, CTA — see `section-templates.md`) as sections where they aren't already provided.
- **Responsiveness contract is identical.** Verify mobile/tablet/desktop on every template — product, collection, cart, homepage. Mobile is where most Shopify sales happen; treat it as primary.
- **Performance:** minimise apps and injected scripts; they are the main cause of slow Shopify stores.

## Standard templates to check

Homepage, collection, product, cart, search, 404, and the customer account pages. Each must be styled and responsive.

## QA

Run the launch checklist (`launch-checklist.md`). Shopify-specific notes:
- **Checkout** — Shopify hosts checkout; verify the path add-to-cart → checkout → test order → confirmation works, and that any checkout extensibility is configured.
- **Tracking** — GA4 / Meta Pixel via Shopify's customer-events / web pixels; verify purchase events fire.
- **Domain & email** — confirm domain connected and notification emails send from the right address.
