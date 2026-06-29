# All of Statistics — Solutions

A [Quarto](https://quarto.org) website of my worked solutions to Larry
Wasserman's *All of Statistics*.

## Structure

- `_quarto.yml` — site config (navbar, sidebar, theme). Add each new chapter
  page to the sidebar here.
- `index.qmd` — home page + chapter index.
- `template.qmd` — formatting reference (math, proofs, code, figures). Copy
  from this when starting a chapter or problem.
- `chapterNN.qmd` — one file per chapter (e.g. `chapter02.qmd`).
- `styles.css` — small style overrides.
- `images/` — figures referenced from chapters.

## Working locally

```bash
quarto preview      # live-reloading local preview
quarto render       # build static site into _site/
```

## Adding a chapter

1. `cp template.qmd chapterNN.qmd` and edit the title.
2. Add a `- href: chapterNN.qmd` entry under `Solutions` in `_quarto.yml`.
3. Update the chapter table in `index.qmd`.

## Daily workflow

```bash
git add -A
git commit -m "ch2: solutions through problem N"
git push
```

## Publishing (optional)

To host on GitHub Pages later:

```bash
quarto publish gh-pages
```
