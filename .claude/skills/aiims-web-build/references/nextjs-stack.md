# Next.js Stack — modern builds

Use this when the host supports Node: **landing pages and custom websites on a modern stack**.

## Stack

- **Next.js 14** (App Router) + **Tailwind CSS**
- TypeScript by default
- Deploy target: Vercel (default) unless the project specifies otherwise

Do not substitute another framework. If the user wants something else, confirm explicitly first.

## Table of contents
1. Project setup
2. Structure
3. Building sections as components
4. Responsiveness in Next.js + Tailwind
5. Forms & integrations
6. Images & performance
7. Deploy

## 1. Project setup

```bash
npx create-next-app@14 <project> --typescript --tailwind --app --eslint
```

Set up brand tokens in `tailwind.config.ts` (`theme.extend.colors`, fonts) and/or CSS variables in `globals.css`. All brand colors go through tokens — never scatter hex values.

## 2. Structure

```
app/
  layout.tsx        ← root layout, fonts, metadata
  page.tsx          ← homepage, assembles sections
  (routes)/         ← additional pages for custom sites
components/
  sections/         ← one file per section (Hero, FeaturesGrid, FAQ, ...)
  ui/               ← shared primitives (Button, Container, ...)
lib/                ← helpers, integrations
```

A page is an assembly of section components. A landing page is one `page.tsx`; a custom site adds routes.

## 3. Building sections as components

Each section in the standard kit (see `section-templates.md`) becomes a component in `components/sections/`. Build one at a time, in document order. Props-driven so content is easy to swap. Verify each at all three breakpoints before moving to the next.

## 4. Responsiveness in Next.js + Tailwind

- **Mobile-first always.** Base classes = mobile; layer `sm:` `md:` `lg:` for larger screens. Never desktop-first with `max-*:`.
- Breakpoints map to the contract: mobile ≤640px (`base`), tablet 641–1024px (`md:`), desktop ≥1025px (`lg:`).
- Use `Container` / `max-w-*` so text lines never run edge-to-edge on desktop.
- Test the known failure points (overflow, long headings, fixed-width media, sticky header overlap).

## 5. Forms & integrations

- Forms: a Server Action or an API route (`app/api/.../route.ts`) — never an HTML `<form>` posting to nothing.
- CRM push (HubSpot), booking (Cal.com), email — wire via API route or server action; keep secrets in env vars, never client-side.
- Spam protection: honeypot + a captcha/turnstile for public lead forms.
- After submit, route to a thank-you page/state so conversion tracking fires.

## 6. Images & performance

- Use `next/image` for all raster images — automatic sizing, lazy loading, modern formats.
- Mark above-the-fold hero images `priority`.
- Use `next/font` for fonts (no layout shift, self-hosted).

## 7. Deploy

Deploy to Vercel. Use a preview deployment as the staging environment for client review. Set env vars in the Vercel project. Then run the launch checklist (`launch-checklist.md`) against the preview URL before promoting to production.
