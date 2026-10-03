# Northwestern xaringan slide template

A reusable R Markdown and xaringan repository for Northwestern-branded presentations. `index.Rmd` contains editable placeholders, working examples, presenter notes, both official Northwestern color palettes, and layout patterns adapted from [Andrew Heiss's xaringan decks](https://github.com/andrewheiss).

After GitHub Pages is enabled, the rendered example is available at <https://hhadah.github.io/slides/>.

## Start a new deck

The GitHub repository is intended to be used as a template.

1. Open <https://github.com/hhadah/slides> and click **Use this template**.
2. Name the new repository for the talk or course.
3. Clone it and open the `.Rproj` file.
4. Edit the title, subtitle, author, and date at the top of `index.Rmd`.
5. Replace or delete the guide slides.
6. Render `index.html` before each push.

For a local copy without GitHub, duplicate this directory and remove its `.git` directory before running `git init` in the copy.

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

Save `index.Rmd` to refresh the preview. Stop the preview with `servr::daemon_stop()`.

Build the shareable file from a shell:

```sh
Rscript -e 'rmarkdown::render("index.Rmd")'
```

The deck is self-contained, so `index.html` includes its CSS, JavaScript, and generated figures. MathJax loads online when a slide contains an equation. Commit both `index.Rmd` and `index.html`.

## What to edit

- `index.Rmd` contains slide content, R code, and the color vectors used by plots.
- `assets/northwestern-primary.css` controls the title slide, section dividers, typography, tables, spacing, and primary purple palette.
- `assets/northwestern-secondary.css` adds the official bright and dark secondary colors, chart utilities, and callout boxes.
- `assets/fonts.css` uses system fonts and does not require a font download.
- `assets/animations.css` provides the optional `animated fadeIn` section transition and respects reduced-motion settings.
- `assets/images/` holds local photos, diagrams, and screenshots.

Keep custom presentation rules at the end of the relevant CSS file. Do not edit xaringan's generated HTML.

## Common slide patterns

Start a slide with a heading:

```markdown
---

## Put the conclusion in the title

- Evidence
- Implication
```

Add a primary section divider:

```markdown
---
class: center, middle, section-primary

# Section title

## One-sentence roadmap
```

Build a Heiss-style roadmap with stacked boxes:

```markdown
---
class: title, title-inverse

# Talk roadmap

.box-purple.medium.sp-after-half[01&nbsp;&nbsp;Research question]

.box-teal.medium.sp-after-half[02&nbsp;&nbsp;Data and design]

.box-gold.medium[03&nbsp;&nbsp;Main result]
```

Use a color-coded section divider. The slide stays Northwestern Purple while the bottom rule changes:

```markdown
---
class: center, middle, section-title, section-title-teal, animated, fadeIn

# Section title

## One-sentence roadmap
```

Available section accents are `green`, `teal`, `blue`, `gold`, and `coral`. Replace `teal` in `section-title-teal` with the chosen accent.

Set one statement in large type:

```markdown
---
class: middle, statement-slide

.box-inv-purple.huge[
One claim. Large type. Nothing competing with it.
]
```

Use `.pull-left-3[]`, `.pull-middle-3[]`, and `.pull-right-3[]` for a three-part visual sequence.

Create two columns:

```markdown
.pull-left[
Left content
]

.pull-right[
Right content
]
```

Add speaker notes after three question marks:

```markdown
???
Only the presenter sees these notes in presenter mode.
```

Use a secondary accent without making it the slide's dominant color:

```markdown
.callout-blue[
**Comparison group**

Short explanation.
]
```

## Color system

Northwestern Purple is `#4E2A84`. The primary CSS includes Purple 10 through Purple 160, plus Northwestern's rich-black tints. Use white for most slide backgrounds and Purple 100 as the anchor.

The secondary CSS includes six bright colors and six dark colors. Northwestern recommends these colors for distinctions in charts, graphs, callouts, and controls. Use them sparingly.

The setup chunk in `index.Rmd` defines matching R vectors:

```r
nu_primary["purple"]
nu_secondary[c("dark_teal", "dark_orange")]
```

Official references:

- [Northwestern primary palette](https://www.northwestern.edu/brand/visual-identity/color-palettes/)
- [Northwestern secondary palette](https://www.northwestern.edu/brand/visual-identity/color-palettes/secondary-palette/)

## Images, citations, and equations

Put image files in `assets/images/` and use relative paths:

```markdown
![](assets/images/figure-name.png)
```

Add a source at the bottom of a slide:

```markdown
.footnote[Source: Author, title, year, URL.]
```

Use normal LaTeX delimiters for math:

```latex
$$Y_i = \alpha + \beta D_i + \varepsilon_i$$
```

## Present and export

Useful keys during a talk:

- `h` or `?` opens xaringan help.
- `p` opens presenter mode.
- `c` clones the deck into a second window.
- `b` blacks out the slide.
- `m` mirrors the slide.

Open `index.html` in Chrome or Chromium and print to PDF for a static backup. Enable background graphics in the print dialog so section colors appear.

## Publish with GitHub Pages

The committed `index.html` can be served from the root of the `main` branch. For a repository created from this template:

1. Push the rendered `index.html`.
2. Open **Settings > Pages** on GitHub.
3. Choose **Deploy from a branch**.
4. Select `main` and `/ (root)`.

The deck will appear at `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/` after GitHub finishes the first deployment.
