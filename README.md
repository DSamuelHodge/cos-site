# CoS site

Hugo + Hextra. Local clone: `~/projects/cos-site` on Termux.

Preview: `hugo server --bind 127.0.0.1 --baseURL http://127.0.0.1:1313/`

CI (`.github/workflows/hugo.yaml`) builds Hugo Extended 0.165.0 on every push and PR. On `main` it also uploads a Pages artifact and deploys.

GitHub Pages URL (project site): https://dsamuelhodge.github.io/cos-site/

If Pages is not on yet: repo **Settings → Pages → Source: GitHub Actions**. The workflow also tries to enable Pages on the first `main` run. Private repos need GitHub Pro (or a public repo) for Pages.

Do not commit secrets, phones, or SMS bodies.
