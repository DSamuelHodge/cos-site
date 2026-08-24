# Derrick Hodge

Hugo + Hextra site. Local clone: `~/projects/cos-site` on Termux.

- **Life** — People, Operations, Focus, Education
- **Work** — Projects, Tasks, Commitments (GitHub issues dispatch agents; Kaneo and Linear ingest the same schema)
- **Notes** — synthesis and decisions

Preview: `hugo server --bind 127.0.0.1 --baseURL http://127.0.0.1:1313/`

CI (`.github/workflows/hugo.yaml`) builds Hugo Extended 0.165.0 on every push and PR. On `main` it deploys GitHub Pages.

Live: https://dsamuelhodge.github.io/cos-site/

Agent issue forms: `.github/ISSUE_TEMPLATE/project.yml` and `task.yml`.

Do not commit secrets, phones, or SMS bodies.
