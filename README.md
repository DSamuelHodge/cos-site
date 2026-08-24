# Derrick Hodge

Hugo + Hextra site. Local clone: `~/projects/cos-site` on Termux.

- **Life** — People, Operations, Focus, Education (`kind`: person, ops, focus, education)
- **Work** — Projects, Tasks, Commitments. Projects and tasks use **Kaneo** field names (`data/schemas/`). GitHub issue forms dispatch agents.
- **Notes** — Decisions and a shareable **Feed** (RSS at `/notes/feed/index.xml`)

Every page has `schema`, `kind`, `title`, `description`. New pages: `hugo new --kind project work/projects/slug.md` (and `task`, `decision`, `feed`, `person`, `commitment`).

Preview: `hugo server --bind 127.0.0.1 --baseURL http://127.0.0.1:1313/`

CI (`.github/workflows/hugo.yaml`) builds Hugo Extended 0.165.0 on every push and PR. On `main` it deploys GitHub Pages.

Live: https://dsamuelhodge.github.io/cos-site/

JSON: `/index.json` and per-section `index.json`. RSS: `/index.xml` and `/notes/feed/index.xml`.

Agent issue forms: `.github/ISSUE_TEMPLATE/project.yml` and `task.yml`.

Do not commit secrets, phones, or SMS bodies.
