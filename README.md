# SouthPay documentation

The source for [docs.southpay.io](https://docs.southpay.io) — the developer
documentation for the SouthPay crypto payments API.

Built with [Mintlify](https://mintlify.com). Pages are MDX with YAML
frontmatter; navigation and theming live in `docs.json`.

## Local development

```bash
npm i -g mint
mint dev
```

The preview runs at `http://localhost:3000`. It reads `docs.json` from the
directory you run it in, so run it from the repository root.

## Before you open a pull request

```bash
mint broken-links
```

This validates `docs.json`, parses every MDX file and checks internal links.
It must pass.

Beyond that, three rules catch most problems:

- Every page needs `title` and `description` frontmatter. Descriptions are meta
  descriptions — under 160 characters and specific.
- Every code fence needs a language.
- Document what the API does, not what it should do. Verify against the source
  rather than against another page.

`AGENTS.md` covers terminology and style. `CONTRIBUTING.md` covers the
workflow.

## Branches

`main` is the release branch — pushing to it deploys to docs.southpay.io.
Work lands on `dev` first and is merged to `main` as a deliberate release.

## Structure

| Path | Contents |
| --- | --- |
| `docs.json` | Navigation, theming, redirects, SEO |
| `*.mdx` | Guides |
| `api-reference/` | Endpoint reference |
| `agentic/` | Agentic commerce guides |
| `integrations/` | Third-party integration guides |
| `logo/`, `images/` | Brand assets |
| `style.css` | Custom styling loaded by Mintlify |

## Support

Documentation issues: open an issue on this repository.
API and account questions: [support@southpay.io](mailto:support@southpay.io).
