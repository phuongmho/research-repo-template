# Agent Instructions (`AGENTS.md`)

Read [`README.md`](README.md) before modifying code or running tasks.

## 1. Never Write Outputs Inside `code/`

`code/` is strictly for executable source code. **Never save generated results, figures, tables, logs, intermediate artifacts, or datasets inside `code/` or any subfolder of `code/`** (for example, do not write to `code/<category>/<task>/output/` or `code/<category>/<task>/results/`), even when executing a script or package located in `code/`.

Always route generated files to the corresponding top-level destination based on the code package's purpose, mirroring `code/<category>/<task>/` under `output/results/<category>/<task>/<specification>/`:

| Code package location | Where to write outputs |
|---|---|
| `code/reduced_form/<task>/` | `output/results/reduced_form/<task>/<specification>/` |
| `code/structural_esti/<model>/` | `output/results/structural_esti/<model>/<specification>/` |
| `code/counterfactuals/<scenario>/` | `output/results/counterfactuals/<scenario>/<specification>/` |
| `code/explore/<question>/` | `output/results/explore/<question>/<specification>/` |
| `code/paper_assets/` | `output/paper_assets/figures/` and `output/paper_assets/tables/` |
| Intermediate objects / caches | `output/artifacts/<category>/<task>/` |
| `code/data_prep/<task>/` | `processed_data/` (or `processed_data/for_structural_model/`) |

## 2. Path Resolution and Execution Rules

1. **Run from the repository root:** Assume scripts are launched from the repository root (`project/`) unless [`README.md`](README.md) explicitly states otherwise. Resolve paths relative to the repository root (or via `pathlib.Path(__file__).resolve().parents[...]` anchored to the repo root) so that output paths always target top-level `output/` or `processed_data/` regardless of the working directory.
2. **Create output directories automatically:** Ensure scripts create their target subfolder under `output/` (e.g., `mkdir -p` / `Path.mkdir(parents=True, exist_ok=True)`) before writing files.
3. **Preserve `raw_data/` as read-only:** Never modify or overwrite files in `raw_data/`.
4. **Do not overwrite selected paper results during exploration:** Write new specifications or exploratory runs to their own `<specification>/` subfolder under `output/results/<category>/<task>/` and check [`docs/current.md`](docs/current.md) for the currently selected runs.
5. **Keep documentation and provenance in sync:**
   - Substantive research notes, model specifications, and exploration write-ups belong in `docs/` (`docs/models/<model>/`, `docs/plans/`, `docs/explore/<question>/`, `docs/meetings/`), not inside `code/` or `output/`.
   - When adding or changing a task's inputs, outputs, or entry command, update [`README.md`](README.md) (and any task `README.md` if present).
   - If you add a new structural folder under `output/`, `raw_data/`, `processed_data/`, `literature/`, or `overleaf/` that should be preserved in Git, place a `.gitkeep` file inside it (since `.gitignore` ignores payloads in those folders except `.gitkeep` and data `README.md` files).
