# website

Public marketing site and the primary family-facing entry point (learn about
Babbl, buy a Babbl Box, start family sign-up).

## Recommended stack
**Next.js + TypeScript**, deployed static/SSR (e.g. Vercel). Rationale: SEO and
content-heavy marketing pages, fast iteration, shared TS types with other web
repos. Tailwind for styling.

## Audience
Family members (the buyer). Reassuring, plain-language, accessible (older
secondary readers too).

## Proposed structure
```
app/            # routes (Next.js app router)
components/
content/        # marketing copy (MDX)
public/         # static assets
lib/
```

## Integrations
- Sign-up / lead capture → `cloud-api`
- Commerce (hardware purchase + subscription) — TBD provider
- Analytics + consent (GDPR)

**Status:** placeholder. Confirm stack, then `git init`.
