# awi-github-viewer
# AWI GitHub Viewer

A single-file HTML viewer that maps and previews the entire [`innovyze/Open-Source-Support`](https://github.com/innovyze/Open-Source-Support) repository — the public collection of Ruby, SQL, Python, and VBScript tooling for Autodesk Water Infrastructure products (InfoWorks ICM, ICM SWMM, InfoAsset Manager, ICMLive, WS Pro, InfoWater Pro, and XPSWMM).

The repo holds well over a thousand files spread across hundreds of nested folders. Browsing that on GitHub is slow. This viewer flattens the whole thing into one searchable, navigable index you can open in a browser — no install, no build, no server.

**Live demo:** https://awi-innovyze-github-viewer.netlify.app/

## What it does

- **Full file tree** — every folder and file in the repository, expandable and collapsible in one view.
- **Browse by product** — files grouped by Autodesk Water product so you can jump straight to the ICM Ruby scripts, the InfoWater Pro tools, and so on.
- **Inline preview** — click any file to read it without leaving the page. Source files render as text, `readme.md` files render as formatted Markdown, and `image.png` screenshots display inline.
- **Search** — filter the tree by filename or path as you type.
- **Direct GitHub links** — every entry links out to its source on `github.com` so you can open, fork, or copy the original.
- **Export** — dump the current index to CSV or Markdown for offline reference or for pasting into other docs.
- **Stats at a glance** — running counts of total files, folders, Ruby scripts, and SQL queries.

## How it works

The file tree is baked into the page as a static data blob, so the index loads instantly with no API calls. When you click a file to preview it, the viewer fetches that single file's contents on demand from `raw.githubusercontent.com`. Source links point at the corresponding `github.com/innovyze/Open-Source-Support` path.

Because previews come straight from the live repo, you're always reading the current `main` version of each file — but the *tree* reflects whatever was present when the page was last regenerated. Regenerate the page to pick up newly added scripts (see below).

## Running it

It's one self-contained HTML file. Three ways to use it:

1. **Open locally** — download the `.html` file and double-click it. Inline previews need an internet connection (they fetch from GitHub), but the tree and search work offline.
2. **GitHub Pages** — commit the file as `index.html` at the repo root, then enable Pages under **Settings → Pages → Deploy from a branch → main → / (root)**.
3. **Any static host** — Netlify, Vercel, S3, a plain web server. There's nothing to configure.

## A note on rate limits

Inline previews are unauthenticated requests to GitHub's raw file endpoint. If you click through a large number of files very quickly, GitHub may briefly rate-limit your IP. Waiting a minute clears it. This is a GitHub limit, not a bug in the viewer.

## Regenerating the index

The embedded tree is a snapshot. When `innovyze/Open-Source-Support` adds or removes scripts, the viewer's tree will be stale until the page is rebuilt from a fresh crawl of the repository. The previews themselves always reflect live content.

## Credits

Built by [Robert Dickinson](https://github.com/Dickinsonre) as an independent navigation aid for the Autodesk Water open-source community.

The underlying scripts and content belong to [`innovyze/Open-Source-Support`](https://github.com/innovyze/Open-Source-Support) and remain under that repository's license. This viewer is not an official Autodesk or Innovyze product.

## License

Released under the MIT License. See [`LICENSE`](LICENSE) for details.
