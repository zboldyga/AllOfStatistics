# All of Statistics — Solutions

A [Quarto](https://quarto.org) website of my worked solutions to Larry
Wasserman's *All of Statistics*.

[View Solutions](https://zboldyga.github.io/AllOfStatistics/).

## Structure

- `_quarto.yml` — site config (navbar, sidebar, theme). Add each new chapter
  page to the sidebar here.
- `index.qmd` — home page + chapter index.
- `template.qmd` — formatting reference (math, proofs, code, figures). Copy
  from this when starting a chapter or problem.
- `chapterNN.qmd` — one file per chapter (e.g. `chapter02.qmd`).
- `styles.css` — small style overrides.
- `images/` — figures referenced from chapters.
- `requirements.txt` — Python packages (Jupyter + plotting) needed to execute
  code chunks at render time.
- `_site/` — generated output (git-ignored; rebuilt on every render).

## Working locally

Python code chunks (e.g. matplotlib figures) need Jupyter installed in the
active Python environment. Quarto recommends a project virtual environment;
see the [Virtual Environments](https://quarto.org/docs/projects/virtual-environments.html)
guide.

```bash
python3 -m venv .venv
source .venv/bin/activate          # Windows: .venv\Scripts\activate
pip install -r requirements.txt
quarto check                       # verify Quarto sees Python + Jupyter
quarto preview                     # live-reloading local preview
quarto render                      # build static site into _site/
```

If you use conda instead, install the same packages into the environment you
render from: `pip install -r requirements.txt` (or `conda install jupyter matplotlib pyyaml`).

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

## Publishing

Publishing is automated. The `.github/workflows/publish.yml` GitHub Action runs
on every push to `main` (and via manual dispatch). It:

1. checks out the repo and installs Quarto,
2. sets up Python and installs `requirements.txt` (so Jupyter can execute the
   code chunks),
3. renders the site to `_site/`, and
4. deploys `_site/` to GitHub Pages.

This uses the GitHub Pages **artifact** deployment, so a one-time repo setting is
required: **Settings → Pages → Build and deployment → Source = "GitHub
Actions"**. (Do not run `quarto publish gh-pages`; the branch-based method is
incompatible with the artifact deployment used here.)
