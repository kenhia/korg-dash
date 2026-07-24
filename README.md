# korg-dash

Summary-data provider for an **infographic dashboard mode** in
[`kdeskdash`](https://github.com/kenhia/kdeskdash).

`korg-dash` queries [`korg`](https://github.com/kenhia/korg) — Ken's unified
work-items / kanban / planning system — and rolls the live data up into small,
glanceable summaries (counts, status breakdowns, planning-queue depth, recent
activity) that `kdeskdash` can render as an at-a-glance "infographic" screen.

> Status: **scaffold.** The project is initialized (harness, license, docs
> layout) but the infographic mode it feeds does not exist in `kdeskdash` yet.
> See [`sprints/planning/roadmap.md`](sprints/planning/roadmap.md).

## What it does

- Pull work items, cards, and planning data from `korg` (via its REST API /
  MCP endpoint).
- Aggregate into compact summary metrics suited to a small dashboard panel.
- Emit that summary in a shape `kdeskdash` can consume (the exact contract is
  TBD and will be defined with the `kdeskdash` infographic mode).

## Relationship to other tools

| Tool        | Role                                                              |
|-------------|------------------------------------------------------------------|
| `korg`      | System of record for work items, cards, planning, reading list.  |
| `korg-dash` | Reads `korg`, produces summary data. **This repo.**              |
| `kdeskdash` | RPi5 LVGL touch dashboard; will render the summaries.            |

## Development

This repo uses the [`kprojects`](https://github.com/kenhia/kprojects) minimal
harness. See [`CLAUDE.md`](CLAUDE.md) for conventions.

```sh
just            # list recipes
just check      # CI gates (wire up as the project grows)
```

Tooling: Python managed by `uv`, `ruff`, `ty` (astral toolchain); TDD preferred.

## License

MIT — see [`LICENSE`](LICENSE).
