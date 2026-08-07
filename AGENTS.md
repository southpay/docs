# Documentation project instructions

## About this project

This is the public documentation for the SouthPay crypto payments API,
built on [Mintlify](https://mintlify.com). Pages are MDX with YAML
frontmatter. Navigation, theming and redirects live in `docs.json`.

Run `mint dev` to preview and `mint broken-links` to validate. Both must be
run from the repository root.

## Source of truth

Document what the API does, not what it should do. The implementation is the
authority — verify against it rather than against another documentation page.
Several pages have been confidently wrong in the past because a claim was
copied forward instead of checked.

Never invent a field name, status, error code, asset id, header or URL. If you
cannot verify something, leave it out and say so.

## Terminology

- The brand is **SouthPay**, with a capital P.
- Wire identifiers keep their own casing regardless of brand style: the API
  sends `Southpay-Signature`, reads `X-Southpay-Account`, and the legacy embed
  script exposes `window.Southpay`. Never "correct" these.
- "Payment intent", not "charge" or "invoice".
- "Store", not "account" or "merchant account". A merchant owns stores.
- "Test mode" and "live mode", not "sandbox" and "production".
- "Ledger" in lowercase means internal double-entry accounting. There is no
  Ledger product in these docs.

## Style preferences

- Active voice, second person, present tense.
- Sentence case for headings.
- One idea per sentence.
- Bold for UI elements: click **Settings**.
- Code formatting for file names, commands, paths, fields and code references.
- Every code fence declares a language. Use `typescript`, not `ts`.
- Every page has `title` and `description` frontmatter. Descriptions are meta
  descriptions: under 160 characters, specific, no boilerplate.
- Cut "simply", "just", "easily", "seamlessly", "powerful", "robust",
  "leverage", "utilize". Reference docs are read by someone mid-integration
  with a bug.
- Reserve `<Warning>` for "this will lose money or break production". Overused
  callouts train readers to skip them.
- Use `<Columns>`, not the deprecated `<CardGroup>`.
- API reference pages use `<ParamField>`, `<ResponseField>` and
  `<Expandable>`.
- Horizontal rules between every section are visual noise. Separate with
  headings.

## Content boundaries

These pages are public. Do not publish:

- **Third-party vendor names.** Not the object storage provider, the swap
  provider, the authorization provider, the custody provider or the hosting
  provider. Describe the capability, not the supplier.
- **Internal implementation.** No class, model, serializer, job or service
  names. No ORM or framework identification. No internal repository or file
  paths. No queue, worker or database internals.
- **Internal feature flag identifiers.** Document the *behaviour* — that a
  capability is off by default, that only SouthPay staff can enable it, that
  there is no API or dashboard toggle, and the exact status and error code
  returned until then. The flag's internal name helps nobody outside the
  company.
- **Staff-only endpoints.** Nothing under `admin/` or `platform_admin/`.
- **Unfixed security issues**, or the internal cause of a known bug. Document
  the observable behaviour and leave it there.

One exception: values the API actually returns in responses stay documented
even when they look internal, because integrators receive them and may need to
match on them. Keep the value, drop any prose framing it as internal
machinery. If a returned value should not be public, the fix belongs in the
API, not in the docs.

Dashboard-only endpoints are not public API. Where a reader genuinely needs
one — payout destinations are a prerequisite for payouts — say what it is and
that it is configured in the dashboard. Never imply an API key call will work.

## Brand assets

`logo/` and `images/` must contain SouthPay assets only. This repository was
generated from the Mintlify starter kit, and starter assets have shipped to
production before. Check what an image actually depicts before referencing it.
