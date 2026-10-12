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

The workflow in `.github/workflows/pages.yml` builds the MyST site and deploys it to GitHub Pages whenever `main` is updated. To enable it:

1. Push this repository to GitHub.
2. In the repository, open **Settings → Pages** and set the source to **GitHub Actions**.
3. Push to `main` or run the workflow manually from the **Actions** tab.

The workflow reads the Pages base path automatically, so links work both for a project site such as `owner.github.io/repository` and an owner site such as `owner.github.io`.
