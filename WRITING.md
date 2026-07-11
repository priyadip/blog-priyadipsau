# Publishing a post

1. Create `src/content/blog/<slug>.md` (copy `hello-world.md` as a starting point).
2. Fill in the frontmatter:
   ```yaml
   ---
   title: "Your title"
   description: "One sentence for the index page, RSS, and SEO."
   publishDate: 2026-07-12
   tags: ["ml", "interpretability"]
   draft: true
   ---
   ```
3. Write the post in Markdown. Inline math: `$...$`. Display math: `$$...$$`
   (KaTeX, rendered at build time). Code: fenced blocks with a language tag,
   e.g. ` ```python `.
4. Images go in `public/images/<slug>/` and are referenced as
   `/images/<slug>/name.png`.
5. Preview locally with `pnpm dev`.
6. When ready, set `draft: false`, then commit and push to `main`. Cloudflare
   Pages rebuilds and redeploys automatically — nothing else to do.

Draft posts (`draft: true`) still build a page (so you can preview the exact
URL) but are excluded from the index and `/rss.xml` until you flip the flag.
