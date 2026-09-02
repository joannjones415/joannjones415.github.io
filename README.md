# Personal site

Static HTML and CSS. No build step, no dependencies, nothing to install.
Open `index.html` in a browser to see changes; refresh to update.

```
index.html                  the whole page — all your content lives here
style.css                   all styling; the dials are at the top
fonts/                      Computer Modern (CMU), three weights, ~143 KB total
images/photo.jpg            your portrait
cv.pdf                      your CV — the nav and header link to it
```

Replace `cv.pdf` whenever you update it; the filename is all the links know
about, so nothing else needs changing.

## Filling it in

Everything you need to edit in `index.html` is marked with an `EDIT`
comment. The sections appear in the same order as they do on the page:

| Section | What to change |
|---|---|
| Head | Page title and the description search engines show |
| Header | Name, department / institution / city, contact links, bio |
| Research | One `<li>` per topic — titles only |
| Publications | One `.paper` block per paper, grouped into `.year-block` per year |
| Talks & Posters | One `<li>` per entry: title, venue, format and date |
| Code | One `<li>` per repository |
| Teaching & Outreach | One `<li>` per entry: role, detail line, dates |

Two patterns worth knowing:

- **Adding a paper** — copy a whole `<div class="paper"> … </div>` block.
  Wrap your own name in `<strong>` inside `.authors`. Delete any link chip
  you don't have a URL for.
- **Adding a year** — copy a whole `<div class="year-block"> … </div>`.
  The big faint numeral on the right is the year marker. Newest first.

## Changing the look

Open `style.css` and edit the `:root` block near the top. Every colour,
type size, and width on the page is a named variable there:

```css
--accent:      #9c8fd6;   /* periwinkle — links, chips, repo names    */
--accent-2:    #63a89c;   /* mint-teal — the dotted section dividers  */
--size-name:   44px;      /* your name in the header                  */
--size-section: 30px;     /* RESEARCH / PUBLICATIONS / … headings     */
--page-width:  820px;     /* how wide the text column runs            */
--photo-width: 210px;     /* portrait size                            */
```

Nothing below that block needs touching for ordinary changes.

The colours are sampled from the header photo — the deep indigo behind the
nebula, the cream of its bright core, the periwinkle haze, and the mint-teal
of the star clusters. If you swap the photo for one with a different cast,
resample and replace those five hex values and the whole page follows.

## Fonts

The three files in `fonts/` are Computer Modern Unicode — `cmunrm` (Roman),
`cmunbx` (Bold), `cmuntt` (Typewriter) — subset to Latin, Latin-1, Latin
Extended-A, Greek, punctuation, sub/superscripts, arrows and math
operators, then converted to woff2. They are served from this repo, so the
page doesn't depend on any font CDN staying up.

Computer Modern is public domain / SIL OFL (GUST Font License for the
Latin Modern siblings) and fine to redistribute this way.

## Publishing to GitHub Pages

1. On GitHub, create a repository named exactly `joannjones415.github.io`.
   Leave it empty — no README, no .gitignore.
2. From inside this folder, push these files to `main`:

```bash
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/joannjones415/joannjones415.github.io.git
git push -u origin main
```

3. In the repository, go to **Settings → Pages** and set the source to
   **Deploy from a branch**, branch `main`, folder `/ (root)`.
4. The site appears at `https://joannjones415.github.io` within a minute or two.

Every later change is `git add`, `git commit`, `git push` — Pages redeploys
on its own.

### A custom domain, later

Add a file named `CNAME` containing just the domain (e.g. `joannjones.com`),
point a CNAME DNS record at `joannjones415.github.io`, and enable HTTPS under
Settings → Pages.

## Checking your work

- Narrow the browser window to phone width — the header stacks and the year
  numerals move above their papers.
- Click every link. The only placeholder left in the file is inside the
  commented-out repository template in the Code section.
