# Documentation site

The site publishes `README.md`, `SECURITY.md`, and `docs/` from the repository root. Hugo and the Hextra theme build it. `hugo.yaml` mounts those files, so the site keeps no copy of them.

## Reference: layout

| Path | Role |
| :--- | :--- |
| `hugo.yaml` | Mounts the published files, sets their titles and order, and sets the menu. |
| `hugo.version` | Pins the Hugo version. |
| `go.mod`, `go.sum` | Pin the theme version. |
| `content/docs/_index.md` | Lists the documents. |
| `assets/css/custom.css` | Hides the title heading inside each mounted file. |
| `layouts/_partials/gvx/resolve.html` | Maps each Markdown link to a page, an asset, or a repository file. |
| `layouts/_markup/` | Applies the resolver to links and images. |
| `public/` | Build output. Git ignores it. |

## Reference: link resolution

A relative link selects its target in this order:

1. The page that Hugo mounted from that path.
2. The asset that Hugo mounted from that path.
3. The file in the repository at the commit in `params.repoRef`.

The build fails in three cases:

- A link to a Markdown file names no page.
- A link has an anchor that names no heading of its page.
- An image names no asset.

`params.repoOnlyMarkdown` lists the Markdown files that the site does not publish.

## Reference: dependencies

`hugo.version` selects the Hugo binary and `go.mod` selects the theme. CI and a local build use the same two versions.

> [!WARNING]
> Do not run `go mod tidy` in this directory. It removes the theme, because no Go file imports it. Run `hugo mod tidy` instead.

## Reference: deployment

`../.github/workflows/site.yml` builds the site for each pull request that changes its inputs. It publishes the `main` branch to GitHub Pages. A manual run publishes another branch only with the `deploy` option. GitHub Pages must use GitHub Actions as its source.

## Procedure: build the site

> [!IMPORTANT]
> Run every command in this directory.

1. Install Hugo: `go install "github.com/gohugoio/hugo@$(cat hugo.version)"`.
2. Build the site: `hugo --gc --minify`.
3. Open `public/index.html`.

## Procedure: preview the site

1. Start the server: `hugo server`.
2. Open `http://localhost:1313/gvx/` in a browser.
