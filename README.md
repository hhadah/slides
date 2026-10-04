# Northwestern xaringan slide template

A reusable R Markdown and xaringan repository for Northwestern-branded presentations. The visual system adapts layout patterns from [Andrew Heiss's xaringan decks](https://github.com/andrewheiss) to Northwestern's official primary and secondary colors.

- [Rendered starter deck](https://hhadah.github.io/slides/)
- [Component guide](https://hhadah.github.io/slides/guide.html)
- [GitHub template repository](https://github.com/hhadah/slides)

## Start a new deck

This repository is a GitHub template.

1. Open <https://github.com/hhadah/slides> and click **Use this template**.
2. Name the new repository for the talk or course.
3. Clone it and open `slides.Rproj`.
4. Edit the title, subtitle, and date at the top of `index.Rmd`.
5. Edit presenter details once in `_profile.yml`.
6. Replace the five starter slides. Copy additional layouts from `guide.Rmd` when needed.
7. Render `index.html` before each push.

For a local copy without GitHub, duplicate this directory and remove its `.git` directory before running `git init` in the copy.

## Repository structure

- `index.Rmd` is the lean starter deck served by GitHub Pages.
- `guide.Rmd` is the complete layout, color, and syntax gallery.
- `_profile.yml` is the single source for the author, institution, and contact details used by both decks.
- `assets/northwestern-primary.css` controls typography, spacing, primary colors, research layouts, tables, and print behavior.
- `assets/northwestern-secondary.css` adds the official bright and dark secondary colors.
- `assets/fonts.css` loads the bundled Source Sans 3 variable font without a network request.
- `assets/colors.R` defines Northwestern color vectors for R figures. It does not install or define a `ggplot2` theme.
- `assets/images/` holds local photos, diagrams, screenshots, and the full-bleed placeholder.
- `assets/brand/` is the slot for an approved Northwestern wordmark.

Do not edit generated HTML. Put custom rules at the end of the relevant CSS file.

## Install once

Install R, Pandoc, and two R packages:

```r
install.packages(c("rmarkdown", "xaringan"))
```

RStudio includes Pandoc. From another editor, confirm that `pandoc` is on `PATH`.

## Preview and render

Run a live preview from the R console:

```r
xaringan::inf_mr("index.Rmd")
```

Save `index.Rmd` to refresh the preview. Stop it with `servr::daemon_stop()`.

Build the starter deck from a shell:

```sh
Rscript -e 'rmarkdown::render("index.Rmd")'
```

Build both decks:

```sh
Rscript -e 'rmarkdown::render("index.Rmd"); rmarkdown::render("guide.Rmd")'
```

The HTML files contain their CSS, JavaScript, fonts, and generated figures. MathJax loads online when a slide contains an equation. Commit the R Markdown sources and rendered HTML files.

## Presenter profile

Change personal details in `_profile.yml`:

```yaml
author: "Hussain Hadah"
institution: "Northwestern University"
email: "hhadah@tulane.edu"
```

The title, footer, and final contact slide read this file. The current email is the Tulane address copied from the earlier slide deck. Replace it in `_profile.yml` if a different address is now preferred.

## Available layouts

The starter uses five slides: title, roadmap, section divider, main estimate, and contact.

`guide.Rmd` also includes:

- Three-part visual story
- Statement and takeaway slides
- Two-column text and image layouts
- Full-bleed image
- Headline number
- Quote with citation
- Research timeline
- Identification equation and assumptions
- Main estimate with confidence interval
- Tables, equations, palettes, and appendix divider

Each slide block begins after a line containing three hyphens. Copy the complete block into `index.Rmd`.

## Optional approved wordmark

The repository uses a text label by default and does not recreate or distribute a Northwestern trademark.

To add an approved wordmark:

1. Put it at `assets/brand/northwestern-wordmark.svg`.
2. Replace the text inside `.brand-wordmark-slot[]` with:

```html
<img src="assets/brand/northwestern-wordmark.svg"
     alt="Northwestern University">
```

Use a white approved wordmark on the purple title background.

## Color system

Northwestern Purple is `#4E2A84`. Most content slides use a white background, with purple as the anchor.

The secondary CSS includes six bright colors and six dark colors. Northwestern recommends these colors for distinctions in charts, graphs, callouts, and controls. Use them sparingly.

The setup chunk sources matching R vectors from `assets/colors.R`:

```r
nu_primary["purple"]
nu_secondary[c("dark_teal", "dark_orange")]
```

Official references:

- [Northwestern primary palette](https://www.northwestern.edu/brand/visual-identity/color-palettes/)
- [Northwestern secondary palette](https://www.northwestern.edu/brand/visual-identity/color-palettes/secondary-palette/)

## Images, sources, and equations

Put images in `assets/images/` and use descriptive alt text:

```markdown
![Map showing the treatment and comparison regions](assets/images/map.png)
```

Add a source at the bottom of a slide:

```markdown
.footnote[Source: Author, title, year, URL.]
```

Use normal LaTeX delimiters for math:

```latex
$$Y_i = \alpha + \beta D_i + \varepsilon_i$$
```

## Accessibility checklist

Before presenting or publishing:

- Make each slide heading state its claim.
- Give informative images descriptive alt text.
- Do not use color as the only group cue.
- Check text, links, tables, and figures for sufficient contrast.
- Navigate the deck with the keyboard and confirm that link focus is visible.
- Export a PDF and check that text and figures remain readable.
- Keep evidence out of decorative background images because they cannot carry useful alt text.

## Present and export

Useful keys during a talk:

- `h` or `?` opens xaringan help.
- `p` opens presenter mode.
- `c` clones the deck into a second window.
- `b` blacks out the slide.
- `m` mirrors the slide.

Open `index.html` in Chrome or Chromium and print to PDF for a static backup. Enable background graphics in the print dialog.

## Publish with GitHub Pages

GitHub Pages serves `index.html` from the root of `main` at <https://hhadah.github.io/slides/>. Repositories created from this template need their own Pages setting:

1. Push the rendered `index.html`.
2. Open **Settings > Pages** on GitHub.
3. Choose **Deploy from a branch**.
4. Select `main` and `/ (root)`.

The deck will appear at `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/` after the first deployment finishes.

## Bundled font license

Source Sans 3 is Copyright 2010-2024 Adobe and distributed under the SIL Open Font License 1.1. The license is stored at `assets/fonts/LICENSE.md`.
