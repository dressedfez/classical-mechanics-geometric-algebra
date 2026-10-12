# Classical Mechanics with Geometric Algebra

A web-first book draft written in MyST Markdown.

## Preview locally

With MyST installed, run:

```sh
myst start
```

## Build the static website

```sh
myst build --html
```

The generated website is written to `_build/html/`.

## Publish with GitHub Pages

This project lives in a public GitHub repository. The workflow in `.github/workflows/pages.yml` builds the book on pushes and pull requests. It does not publish the draft automatically.

When you are ready to publish, enable **Settings → Pages → Build and deployment → GitHub Actions**. Then open **Actions → Build and publish MyST book → Run workflow** on `main` and set **Publish the book to GitHub Pages**. The workflow reads the Pages base path automatically. The source repository and the published website are public.
