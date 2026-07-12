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
6. When ready, set `draft: false`, then commit and push to `main`. GitHub
   Actions rebuilds and redeploys to GitHub Pages automatically — nothing
   else to do.

Draft posts (`draft: true`) still build a page (so you can preview the exact
URL) but are excluded from the index and `/rss.xml` until you flip the flag.

No local setup needed to write — you can create/edit the `.md` file straight
from the GitHub web editor (or press `.` on the repo to open github.dev),
and commit directly from the browser. It triggers the same deploy.

## KaTeX gotcha: backslash + punctuation

In a few command sequences, the backslash gets silently eaten by Markdown's
own escaping before KaTeX ever sees it — specifically whenever a backslash is
**immediately followed by punctuation** (not a letter). This breaks `\{`,
`\}`, `\|`, `\;`, `\,`, and `\\[` (a row-break with an optional spacing
argument, e.g. `\\[2ex]`). A command like `\left(` is fine, because the
backslash there is followed by the letters "left", not punctuation directly.

Symptoms: a piece of literal `\[...]`-looking text appears inline instead of
rendering, or KaTeX throws "Missing or unrecognized delimiter for \left".

Workarounds (use the letter-named command instead of the punctuation form):

| Instead of | Use |
| :-- | :-- |
| `\{` `\}` | `\lbrace` `\rbrace` |
| `\|...\|` (norm) | `\lVert...\rVert` |
| `\middle\|` / bare `\;` `\,` | `\mid`, or just drop the spacing |
| `\\[2ex]` (piecewise/cases with extra spacing) | split into separate `$$...$$` blocks instead of one `cases` environment, or drop the `[2ex]` |

Plain `\\` on its own (row breaks in `aligned`/`pmatrix`, not followed by a
punctuation character) is unaffected — that one's safe as-is.
