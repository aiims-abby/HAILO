# Pre-Launch QA Checklist — annotated

Run this on **staging** before requesting client approval. Report each item PASS / FAIL / N/A with a one-line note. Nothing ships until every applicable item passes and the client has approved.

This is the AIIMS landing-page launch process, generalised to all project types.

## 1. Hosting compatibility

Confirm the host actually supports the stack that was built. Node/Next.js needs a Node-capable host; PHP boilerplate needs PHP 7.4+ with Apache mod_rewrite. If there's a mismatch, the stack was chosen wrong at intake — fix it before going further, don't paper over it.

## 2. Responsive testing

Verify the site on desktop, tablet, and mobile against the responsive contract (see `section-templates.md`). Walk every template/page, not just the homepage. Check the known failure points. A layout that "probably works" is a FAIL until verified.

## 3. Form testing

- Every form submits successfully.
- Submissions arrive at the correct destination — email inbox, CRM (HubSpot), or platform.
- Email authentication: check SPF, DKIM, DMARC on the sending domain so submissions don't get marked as spam or blocked.
- If delivery fails or lands in spam, the client's SMTP credentials may be needed — flag this to the user.
- **WooCommerce/Shopify:** this extends to the full checkout flow — add to cart → checkout → test order → confirmation email.

## 4. Tracking & analytics

Confirm all required tracking is installed and firing: GTM, GA4, Meta Pixel, and any other conversion scripts. Verify the conversion event fires on the thank-you page (or order-received page for ecommerce). A pixel that's installed but not firing is a FAIL.

## 5. SEO checks

Verify: page title, meta description, image ALT tags, OG/social-share image, the thank-you page, and any required redirects. For multi-page sites, check titles/descriptions are unique and correct per page.

## 6. Performance audit

Run a PageSpeed / Lighthouse audit (LiteSpeed where applicable). Review and address: Performance, Accessibility, Best Practices, SEO. Note scores; fix regressions before launch.

## 7. Final staging review

Confirm everything has been tested and approved on staging — no untested changes, no "will fix after launch" items outstanding.

## Per-project-type notes

- **Landing page** — the checklist applies as-is; this is the original process.
- **Custom website** — run items 2, 5 across *every* page; check internal links and navigation.
- **WordPress** — confirm the client can edit content; check that no debug/dev plugins ship to production.
- **WooCommerce / Shopify** — items 3 and 4 extend to the full purchase path and purchase/conversion events; confirm payment gateways, shipping, and tax with the client.

## Sign-off

Only when every applicable item is PASS and the client has approved on staging is the build **ready to push live**.
