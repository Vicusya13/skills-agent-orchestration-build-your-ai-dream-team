# Project Pulse implementation plan

Plan produced by the **Planner** at the request of the **Orchestrator** for the Project Pulse dashboard described in `.github/project-pulse-brief.md`.

## Goal

A small static Project Pulse dashboard that shows each project's name, owner, status, recent activity and priority as polished project cards.

## Files and ownership

| File | Owner | Purpose |
|---|---|---|
| `app/project-data.json` | Coder | Top-level `projects` array with `name`, `owner`, `status`, `recentActivity`, `priority` |
| `app/index.html` | Coder (structure), Designer (hierarchy & accessibility) | Loads the data and renders the dashboard |
| `app/styles.css` | Designer | Layout, project cards, status badges, spacing, accessible colors |
| `.vscode/launch.json` | Coder | **Run Project Pulse Dashboard** configuration that serves `app/` and opens `index.html` |

## Phases

1. **Data model** (Coder) - create `app/project-data.json` with sample projects.
2. **Design** (Designer) - define the visual system and write `app/styles.css`.
3. **Implementation** (Coder) - build `app/index.html` to fetch the JSON and render cards.
4. **Run configuration** (Coder) - add `.vscode/launch.json`.
5. **Validation** (Orchestrator) - verify the result against the brief.

## Dependencies

- `app/index.html` depends on the field names in `app/project-data.json` and on the CSS class names agreed with the Designer (`.dashboard`, `.project-card`, status/priority badges).
- `.vscode/launch.json` depends on `app/index.html` existing.
- Validation depends on all four files being complete.

## Parallel work

- Phase 1 (data) and Phase 2 (design) have no dependencies on each other and run in **parallel** by the Coder and the Designer.
- Phase 3 starts once the data schema and class names are agreed; Phase 4 can run in parallel with Phase 3.

## Validation

- Dashboard opens from **Run Project Pulse Dashboard** and shows the UI, not a directory listing.
- Every project card shows name, owner, status, recent activity and priority.
- Status and priority are readable as text, not only by color (accessibility).
- Layout is responsive and works on narrow screens.
