# Classical Mechanics with Geometric Algebra

A web-first book draft written in MyST Markdown.

## Preview locally

With MyST installed, run:

```sh
myst start
```

## Build the static website

```sh
myst build --typst
myst build --html
```

The generated website is written to `_build/html/` and includes the freshly built PDF linked from the start page.

## Build a PDF

With Typst and MyST installed, run:

```sh
myst build --typst
```

The PDF is written to `_build/exports/classical-mechanics-with-geometric-algebra.pdf`. The export includes the introduction and chapters that currently have full drafts; the remaining chapters are still represented by the book outline. The local Typst template is based on the MIT-licensed [MyST plain Typst book template](https://github.com/myst-templates/plain_typst_book) and keeps the PDF numbering consistent with the headings in the manuscript.

## Publish with GitHub Pages

This project lives in a public GitHub repository. The workflow in `.github/workflows/pages.yml` builds the book on pushes and pull requests. It does not publish the draft automatically.

When you are ready to publish, enable **Settings → Pages → Build and deployment → GitHub Actions**. Then open **Actions → Build and publish MyST book → Run workflow** on `main` and set **Publish the book to GitHub Pages**. The workflow reads the Pages base path automatically. The source repository and the published website are public.
