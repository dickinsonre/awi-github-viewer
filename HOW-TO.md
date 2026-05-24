# Publishing a Single-File App to GitHub — How-To

This is the playbook for taking one of my single-file HTML/React apps (the kind
I vibe-code and usually drop on Netlify first) and giving it a proper GitHub
home: a clean repo, GitHub Pages hosting, a real README, and discoverability.

It's written so I (or Claude) can repeat it cold. It's the exact path that
worked for `awi-github-viewer`.

## What I end up with

- A **public GitHub repo** with the app as `index.html` at the root
- **GitHub Pages** turned on → a `https://dickinsonre.github.io/<repo>/` URL
- A **README** that actually describes the app
- An **MIT license**
- A **description + topics** so it shows up well on my profile
- The original **Netlify URL still live**, now linked as the "demo" in the README

GitHub Pages and Netlify both stay up. Pages is the GitHub-native link; Netlify
is the original. Having both is fine and costs nothing.

## The steps

### 1. Get the file as `index.html`

If the app is on Netlify, grab the source: open the site → View Page Source →
save as `index.html`. If I built it from a folder, I already have the file.

The filename matters: it **must** be `index.html` so GitHub Pages serves it
with no setup. Browser downloads often come as `Whatever-map (1).html` — rename
it. The space and `(1)` make ugly URLs.

### 2. Create the repo on github.com

- Name it something short (`awi-github-viewer`)
- **Public**
- **Add README: On**, **MIT License: yes**, **.gitignore: None**
  (a one-file static app doesn't need a gitignore)

Because README + LICENSE get pre-created, the repo isn't empty. Easiest way to
add my file is the browser: **Add file → Upload files**, drop in `index.html`,
commit. (If I push from the command line instead, I have to `git pull` first or
the push gets rejected.)

### 3. Replace the placeholder README

GitHub made a stub README. I overwrite it with the real one — either edit it in
the browser and paste, or upload my own `README.md`. The README should say what
the app does, link the live demo up top, and (for anything sitting on top of an
Autodesk/Innovyze repo) include the line that it's **not an official Autodesk or
Innovyze product**. That keeps the independent-tool framing clean for Expert
Elite.

### 4. Turn on GitHub Pages

**Settings → Pages → Deploy from a branch → main → / (root) → Save.** Live in
about a minute. Since the file is `index.html`, that's all there is to it.

### 5. Fill in description + topics

In the repo sidebar, click the gear next to **About**:

- **Description** (keep under ~120 chars): e.g.
  *"Searchable, single-file viewer and full index of the Autodesk Water
  innovyze/Open-Source-Support repo"*
- **Topics**: pick from
  `swmm`, `infoworks-icm`, `autodesk-water`, `innovyze`, `epanet`, `ruby`,
  `hydraulic-modeling`, `stormwater` — trim to what fits the app

Done.

## What I learned from the first one (awi-github-viewer)

- **Read the file, don't guess.** The README has to match what the app really
  does. The viewer embeds its whole file tree as a data blob and fetches
  individual files live from `raw.githubusercontent.com` — that's worth saying
  in the README (the index is a snapshot; the previews are live).
- **Watch for API rate limits.** Anything hitting `api.github.com`
  unauthenticated is capped at 60 requests/hour per IP. Note it in the README so
  it doesn't look like a bug.
- **Gist is the wrong tool for an interactive app.** A gist serves HTML as
  plain text; rendering it means routing through htmlpreview, which can break
  external fetches. Pages is the real home. A gist is only good as a
  copy-pasteable source snapshot.

## The Claude shortcut

There's a skill (`publish-html-to-github`) that encodes all of this. Next time I
just say something like *"put this on GitHub with Pages and a README"* and hand
over the file or the Netlify link, and Claude runs the whole sequence — reads
the file, writes the README in my voice, gives me the description and topics,
and walks me through the repo settings.
