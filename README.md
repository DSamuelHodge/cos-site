# Derrick Hodge

Hugo + Hextra site. Local clone: `~/projects/cos-site` on Termux.

- **Life** — People, Operations, Focus, Education, Goals, Routines
- **Work** — Projects, Tasks, Commitments, Workflows. Projects and tasks use **Kaneo** field names (`data/schemas/`).
- **Notes** — Decisions, shareable **Feed**, and **Briefings** (weekday + weekly RSS)

Cadence lives in `data/cadence.yaml`. Briefings RSS: `/notes/briefings/index.xml`.

Every page has `schema`, `kind`, `title`, `description`. New pages: `hugo new --kind briefing|goal|workflow|routine|project|task|…`.

Preview: `hugo server --bind 127.0.0.1 --baseURL http://127.0.0.1:1313/`

CI (`.github/workflows/hugo.yaml`) builds Hugo Extended 0.165.0 on every push and PR. On `main` it deploys GitHub Pages.

Live: https://dsamuelhodge.github.io/cos-site/

JSON: `/index.json` and per-section `index.json`. RSS: `/index.xml` and `/notes/feed/index.xml`.

Agent issue forms: `.github/ISSUE_TEMPLATE/project.yml` and `task.yml`.

Do not commit secrets, phones, or SMS bodies.
