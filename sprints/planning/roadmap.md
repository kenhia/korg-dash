# Roadmap

> The general plan for this project. Keep it current; detail lives in the
> sprint records.

`korg-dash` reads `korg` and produces summary data for a future "infographic"
dashboard mode in `kdeskdash`.

## Now

- Bootstrap the repo (done: harness, README, LICENSE, docs layout).
- Prove a read path against live `korg`: pick a first set of summary metrics
  (e.g. open work items by project/status, planning-queue depth, recent
  activity) and fetch them via korg's REST API / MCP endpoint. See
  korg `docs/usage.md` + `docs/api.md`.

## Next

- Define the `kdeskdash` infographic-mode data contract *with* kdeskdash
  (that mode does not exist yet) — settle the output shape korg-dash emits.
- Scaffold the Python package (`uv`), wire `just check`
  (`ruff` + `ty` + `pytest`), first tests around aggregation.

## Later / Ideas

- Caching / refresh cadence appropriate to an always-on RPi panel.
- Multiple summary "cards" (planning, throughput, reading list) selectable
  by kdeskdash.
