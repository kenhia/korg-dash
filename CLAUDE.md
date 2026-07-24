<!-- kproject:begin — managed by kprojects/install.sh; do not edit inside this block -->
## kproject conventions

This project uses the kproject minimal harness
(`~/src/ai-agents/kprojects`). Keep context small; prefer doing over
ceremony.

### Layout

- `sprints/` — the project's evolution, one record per PR-sized unit of
  work (a "sprint")
  - `planning/` — planning docs; at minimum `roadmap.md` (the general plan)
  - `review/` — more formal reviews as the project matures
  - sprint records: `###-<short-name>.md` for small projects, or a
    `###-<short-name>/` directory of files for larger/more formal ones
  - a sprint record is one informal narrative: goal, decisions, what
    shipped, follow-ups — written during the sprint, not after
- `docs/` — project documentation, architecture, usage
- `.scratch/` — git-ignored scratch space for user or agent ephemera;
  use it instead of /tmp
- `justfile` — dev recipes; default recipe is `@just --list`; `just check`
  runs the CI gates; `just deploy` (or variants) if the project deploys
- `.env` — git-ignored; tokens and environment vars

### Workflow

- One sprint ≈ one PR. Sprint proposals and work items are managed in
  `korg`; durable cross-project knowledge goes in `klams`.
- If the korg or klams MCP tools are unavailable in your session, say so
  up front — don't silently work around missing infrastructure.
- TDD preferred: write the failing test first when practical.

### Tooling preferences

- Python managed by `uv`; lint/format with `ruff`; typecheck with `ty`
  (astral toolchain)
- License is MIT unless specifically directed otherwise
<!-- kproject:end -->

## Project

`korg-dash` queries [`korg`](https://github.com/kenhia/korg) (Ken's unified
work-items / kanban / planning system, the system of record) and produces
compact **summary data** for an "infographic" dashboard mode in `kdeskdash`
(kai:`~/src/tools/kdeskdash`). That kdeskdash mode does **not exist yet** — the
data contract between the two is still to be defined.

### Status

Scaffold only: harness, README, LICENSE, docs layout. No application code yet.
Start from `sprints/planning/roadmap.md`.

### How korg-dash talks to korg

- `korg` runs as the live system of record; query it through its **REST API**
  or **MCP endpoint** (do not read korg's database directly).
- Contracts live in the korg repo (kai:`~/src/tools/korg/docs`):
  `usage.md` (web UI, REST API, MCP endpoint) and `api.md` (normative
  agent-facing tool catalogue + collection-read envelope). Read those before
  writing query code.
- korg's own project id is **11**; this project (`korg-dash`) is a separate
  korg project. Work items and sprint proposals for korg-dash are tracked in
  korg.

### Conventions

- Python via `uv`; `ruff` + `ty`; TDD preferred (see managed block above).
- Keep the aggregation logic thin and the korg query surface swappable —
  the kdeskdash-facing output shape will change once that mode is designed.
