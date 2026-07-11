# blog.priyadipsau.in

Minimal, typography-first technical blog. Astro, static output, math via
KaTeX (build-time), code via Shiki (build-time), zero client JS beyond a
tiny theme-toggle script. Separate repo from [priyadipsau.in](https://priyadipsau.in) — no shared code, only linked via RSS.

## Commands

| Command | Action |
| :-- | :-- |
| `pnpm install` | Install dependencies |
| `pnpm dev` | Local dev server at `localhost:4321` |
| `pnpm build` | Build to `./dist/` |
| `pnpm preview` | Preview the production build locally |
| `pnpm check` | Typecheck (`astro check`) |

## Publishing a post

See [WRITING.md](./WRITING.md).

## Stack

Astro · TypeScript (strict) · remark-math + rehype-katex (KaTeX) · Shiki
(dual light/dark themes) · `@astrojs/rss` · `@astrojs/sitemap`. Deployed on
Cloudflare Pages.
