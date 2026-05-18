# WordPress & WooCommerce

Use this when the project type is `wordpress` or `ecommerce-woocommerce`.

## Before building — confirm with the user

WordPress projects vary too much to assume. Confirm:
1. **Build approach** — custom theme, child theme of an existing theme, or a page builder (Elementor / Bricks / Gutenberg blocks)? Confirm which.
2. **Existing site or fresh?** — migration/redesign vs new install.
3. **Hosting** — managed WP host vs generic. Affects staging and deploy.
4. **WooCommerce specifics** (ecommerce only) — payment gateways, shipping zones, tax, product import source.

Do not start until the build approach is settled — it changes everything downstream.

## Principles that still apply

- **Section thinking holds.** Whether via blocks, builder templates, or theme template parts, build the page as the standard section kit (hero, features, testimonials, FAQ, CTA, etc. — see `section-templates.md`).
- **Responsiveness contract is identical.** Verify mobile/tablet/desktop on every template. Page builders make it easy to leave broken mobile layouts — check, don't assume.
- **Reuse:** save good builder templates / block patterns as reusable patterns so future pages start faster.
- **Brand tokens:** define colors/typography once (theme.json for block themes, builder global styles otherwise) — never per-element overrides.

## Custom theme builds

- Child theme over hacking a parent theme directly.
- Template hierarchy: `header.php`, `footer.php`, `front-page.php`, `page-*.php`, template parts for sections.
- Enqueue assets properly (`wp_enqueue_*`), don't inline `<script>`/`<link>`.
- Keep content editable — register the right fields/blocks so the client can update copy without a developer.

## WooCommerce

- Standard pages: shop, product, cart, checkout, account — confirm each is styled and responsive.
- Test the full purchase path on staging: add to cart → checkout → payment (test mode) → order confirmation email.
- Conversion tracking must fire on the order-received page.
- Confirm shipping zones, tax, and payment gateways with the client before launch.

## QA

Run the launch checklist (`launch-checklist.md`). For WooCommerce, "Form testing" extends to the full checkout flow, and "Tracking" includes purchase/conversion events on order completion.
