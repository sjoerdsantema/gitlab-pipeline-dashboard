# GitLab Pipeline Dashboard

A lightweight, single-file dashboard for monitoring the latest pipeline status across GitLab projects. Open it locally in your browser, connect with a Personal Access Token, and watch pipelines across a group or hand-picked projects.

No build step, no backend, and no dependencies — just `index.html`.

## Features

- **Three ways to add projects**
  - **All in group** — load every project under a GitLab group (including subgroups)
  - **Pick projects** — browse a group and add only the projects you care about
  - **Single project** — monitor one project by full path
- **Live overview** — status badges, branch, latest commit title, and time since last update
- **Filtering** — search by name, namespace, or commit; filter by pipeline status or namespace
- **Summary stats** — counts for total, failed, running, and successful pipelines
- **Auto-refresh** — refreshes every 5 minutes with a visible countdown
- **Incremental dashboard** — add projects from multiple groups; remove individual projects or clear the whole board
- **Dark mode** — follows your system `prefers-color-scheme` setting
- **Responsive layout** — usable on desktop and mobile

## Requirements

- A [GitLab Personal Access Token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) with the **`read_api`** scope
- Access to the groups or projects you want to monitor
- A modern browser

The dashboard is configured for **GitLab.com** (`https://gitlab.com/api/v4`). For a self-hosted instance, change the `BASE` constant near the top of the script in `index.html`.

## Quick start

1. Clone or download this repository.

2. Open `index.html` in your browser:

   ```bash
   open index.html
   ```

   Or serve it locally if you prefer:

   ```bash
   python3 -m http.server 8080
   ```

   Then visit `http://localhost:8080`.

3. Choose a scope (**All in group**, **Pick projects**, or **Single project**).

4. Enter your GitLab group or project path (for example `my-org/my-group` or `my-org/my-group/my-app`).

5. Paste your Personal Access Token and click the primary action button.

6. Use **Refresh** to update immediately, or wait for the automatic 5-minute refresh.

## Usage tips

| Scope | Path field | Action |
|-------|------------|--------|
| All in group | Group path, e.g. `acme/platform` | Adds all projects in that group |
| Pick projects | Group path | Opens a checklist to add selected projects |
| Single project | Full project path, e.g. `acme/platform/api` | Adds one project |

- Failed pipelines are sorted to the top so problems stand out.
- Click the external-link icon on a row to open the pipeline (or project) in GitLab.
- Use **Setup** / **Show setup** in the header to change connection settings after the dashboard is loaded.
- Your token is kept only in the browser session for the open tab; it is not stored in the file or sent anywhere except GitLab’s API.

## Security

- Treat your PAT like a password. Do not commit it or share screenshots that include it.
- Use a token with the minimum scope needed (`read_api` is sufficient).
- Revoke the token in GitLab when you no longer need the dashboard.

## Project structure

```
gitlab-pipeline-dashboard/
└── index.html    # Entire app (HTML, CSS, and JavaScript)
```

## License

No license file is included yet. Add one if you plan to distribute or open-source this project.
