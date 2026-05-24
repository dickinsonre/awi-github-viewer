# README Template

A skeleton for documenting a single-file HTML/React app published to GitHub. Fill each section from what the source file actually does (Step 1 of the skill), not from assumptions.

## Section order

1. **Title** — the app name as a heading.
2. **One-liner + context** — one sentence on what it is, then 1–2 sentences on the friction it removes. Name the real-world thing it sits on top of (a repo, a dataset, a SWMM concept) and link it.
3. **Live demo** — the Netlify (or Pages) URL, bolded label, near the top.
4. **What it does** — a bulleted list of *actual* features. Pull these from the source: search, inline preview, export buttons, grouping/filtering, stats. Bold the feature name, then a plain sentence.
5. **How it works** — only if non-obvious. Cover embedded-snapshot vs live-fetch behavior, what's static vs what's fetched at runtime, and anything about freshness.
6. **Running it** — open locally / GitHub Pages / any static host. Keep it to "it's one self-contained file, here are three ways."
7. **Rate limit / caveat note** — if the app hits `api.github.com` or any rate-limited endpoint, say so plainly: it's a platform limit, not a bug.
8. **Regenerating / updating** — if data is embedded as a snapshot, explain it goes stale and how it's refreshed.
9. **Credits** — credit Bob; if it sits on someone else's repo/data, add the "not an official Autodesk or Innovyze product" disclaimer and point at the upstream license.
10. **License** — MIT, link to `LICENSE`.

## Voice

Plain and direct. No "seamless," "powerful," "robust," "leverage," "in today's fast-paced world." No em-dash-heavy breathless phrasing. State what it does and why. Apply the `stop-slop` and `bob-dickinson-voice` skills.

---

## Worked example — the awi-github-viewer README

This is the README that shipped for the repo viewer. Use it as a calibration reference for length and tone.

```markdown
# AWI GitHub Viewer

A single-file HTML viewer that maps and previews the entire
[`innovyze/Open-Source-Support`](https://github.com/innovyze/Open-Source-Support)
repository — the public collection of Ruby, SQL, Python, and VBScript tooling
for Autodesk Water Infrastructure products (InfoWorks ICM, ICM SWMM,
InfoAsset Manager, ICMLive, WS Pro, InfoWater Pro, and XPSWMM).

The repo holds well over a thousand files spread across hundreds of nested
folders. Browsing that on GitHub is slow. This viewer flattens the whole thing
into one searchable, navigable index you can open in a browser — no install,
no build, no server.

**Live demo:** https://awi-innovyze-github-viewer.netlify.app/

## What it does

- **Full file tree** — every folder and file, expandable and collapsible.
- **Browse by product** — files grouped by Autodesk Water product.
- **Inline preview** — click any file to read it: source renders as text,
  readme.md as formatted Markdown, image.png inline.
- **Search** — filter the tree by filename or path as you type.
- **Direct GitHub links** — every entry links to its source on github.com.
- **Export** — dump the index to CSV or Markdown.
- **Stats** — running counts of files, folders, Ruby scripts, SQL queries.

## How it works

The file tree is baked into the page as a static data blob, so the index loads
instantly with no API calls. When you click a file to preview it, the viewer
fetches that single file's contents on demand from raw.githubusercontent.com.

Because previews come straight from the live repo, you're always reading the
current main version of each file — but the tree reflects whatever was present
when the page was last regenerated.

## Running it

It's one self-contained HTML file. Three ways to use it:

1. **Open locally** — download and double-click. Previews need internet;
   tree and search work offline.
2. **GitHub Pages** — commit as index.html at the repo root, then enable Pages
   under Settings → Pages → Deploy from a branch → main → / (root).
3. **Any static host** — Netlify, Vercel, S3, a plain web server.

## A note on rate limits

Inline previews are unauthenticated requests to GitHub's raw file endpoint.
Clicking through many files very quickly may briefly rate-limit your IP.
Waiting a minute clears it. This is a GitHub limit, not a bug.

## Regenerating the index

The embedded tree is a snapshot. When the upstream repo adds or removes
scripts, the tree is stale until the page is rebuilt from a fresh crawl.
Previews always reflect live content.

## Credits

Built by [Robert Dickinson](https://github.com/Dickinsonre) as an independent
navigation aid for the Autodesk Water open-source community.

The underlying scripts belong to innovyze/Open-Source-Support under that repo's
license. This viewer is not an official Autodesk or Innovyze product.

## License

Released under the MIT License. See LICENSE for details.
```
