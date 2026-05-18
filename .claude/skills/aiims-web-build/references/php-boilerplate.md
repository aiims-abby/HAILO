# PHP Boilerplate — tw-landing-boilerplate

Use this when the project is a **landing page or custom site on PHP shared hosting** (no Node support).

Repo: `https://github.com/KuyaLoy/tw-landing-boirlerplate`

## Table of contents
1. When to use it
2. First-time setup
3. The boilerplate already handles this — don't rebuild it
4. Where things go
5. Building a section
6. Forms
7. Extending to multi-page (custom site)
8. Deploy

## 1. When to use it

- Landing page on cPanel / Plesk / shared PHP hosting → yes.
- Custom (multi-page) site on PHP hosting → yes, extended (section 7).
- Host supports Node → do NOT use this; use Next.js instead.

## 2. First-time setup

1. Clone the repo, rename the folder to the project name.
2. `npm install` (build tooling only — the shipped site needs no Node).
3. Rename `.claude-template/` → `.claude/` so Claude Code loads its agents/skills.
4. **Read the project's `CLAUDE.md` and `README.md`.** They are authoritative for path conventions, CSS placement, and the form handler. This skill does not override them.
5. Fill `config/config.php` (site name, description, phone) and copy `.env.example` → `.env` (reCAPTCHA keys, `FORM_ADMIN_EMAIL`, `ALLOWED_HOSTS`).

## 3. The boilerplate already handles this — don't rebuild it

- **Images:** `imgx()` (raster → AVIF/WebP, auto width/height, lazy) and `svgx()` / `svg_inline()`. Always use these — never raw `<img>`.
- **Pathing:** `$basePath` auto-resolves subfolder/subdomain depth. Never hardcode paths.
- **Form security:** reCAPTCHA v3, honeypot, header-injection-safe values, `mail()` or SMTP transport. Don't hand-roll.
- **Config warnings:** missing critical config surfaces as a dev banner / prod HTML comment.
- **Cache busting:** `?v=<mtime>` on assets.

## 4. Where things go

- Page content → `partials/main.php`
- Brand colors → `assets/css/source/critical.css` `:root` variables
- Custom CSS (section 3 onward) → `assets/css/source/custom.css`
- Media-query overrides → `assets/css/source/responsive.css`
- Shared content variables → `data/global-content.php`
- Quick live fixes (no rebuild) → `assets/css/live-edit.css` / `assets/js/live-edit.js`

`@apply` works in all source CSS files except `fonts.css` and `live-edit.css`.

## 5. Building a section

Replace the welcome-page block in `partials/main.php` (between the `START WELCOME PAGE` / `END WELCOME PAGE` markers). Build one section at a time. Use Tailwind utilities with the boilerplate's brand tokens (`bg-primary`, `font-brand`, etc.). Use `imgx()`/`svgx()` for all media. Verify each section at all three breakpoints before moving on.

## 6. Forms

Point forms at `partials/form.php`:
```html
<form method="POST" action="<?= $basePath ?>partials/form">
  <!-- fields -->
  <input type="hidden" name="token" class="recaptchaResponse">
  <input type="hidden" name="honeypot">
</form>
```
If fields change, update `partials/form.php` (handler + email template) to match — preserve the security helpers (`header_safe()`, reCAPTCHA, honeypot).

For deliverability: `mail()` by default; set `SMTP_*` in `.env` to use the bundled PHPMailer. Recommend Resend/MailerSend/Brevo/SES when `mail()` lands in spam.

## 7. Extending to multi-page (custom site)

The boilerplate is single-page by default. For a custom site:
- Add page files at root (e.g. `about.php`, `services.php`), each including `header.php` → page partial → `footer.php`.
- Put each page's body in its own partial under `partials/` (e.g. `partials/about.php`).
- Build a shared nav partial and include it in `header.php`; drive links off `$basePath`.
- Keep one `thankyou.php` for form conversions.

## 8. Deploy

`npm run package` → produces `build/<project>.zip` → upload + extract in cPanel File Manager → create `.env` on server → smoke-test the form. This is a direct-upload workflow, not Git deploy. Then run the launch checklist (`launch-checklist.md`).
