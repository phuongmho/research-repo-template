# Repository organization rules

See the [README](README.md#layout) for the folder tree and [sharing strategy](README.md#sharing-strategy). Use these rules when adding or moving files.

1. **Organize code by research task.** Use `code/data_prep/`, `reduced_form/`, `structural_esti/`, `counterfactuals/`, `explore/`, and `paper_assets/`. Within each, group a coherent task, topic, or model. Keep its reusable functions and checks nearby. Avoid a repository-wide language layer such as `code/python/`.

2. **Separate source, data, and generated files.** Preserve original inputs in `raw_data/`; write derived datasets to `processed_data/`. Put generated results in `output/`. Keep executable source in `code/`, substantive research reasoning in `docs/`, and authored manuscripts/slides in `papers/`. A file's purpose determines its home: a model note belongs in `docs/models/`; an exported table belongs in `output/paper_assets/tables/`.

3. **Make each maintained task runnable.** Its README should state purpose, entry command, inputs, outputs, software, and checks. Resolve paths from one declared project root; keep personal paths in ignored local configuration. Document stage order and commit dependency specifications. Exporting figures or compiling a paper should not require rerunning estimation.

4. **Identify datasets and preserve provenance.** Use stable, documented names: for example, `s1` for a source family and `m1` for a constructed main dataset. Record sources, releases/dates, producer scripts, variable definitions, units, keys, and sample restrictions in the data READMEs. Preserve input versions needed for selected results.

5. **Give each model and specification its own directory.** Mirror the `code/` hierarchy under `output/results/<category>/<task>/<specification>/` (for example, `output/results/reduced_form/descriptive/<specification>/` or `output/results/structural_esti/baseline/<specification>/`); preserve selected paper results during exploration. Save the code revision, configuration, input versions/hashes, environment, seed where relevant, and validation status with the specification's results. Counterfactuals should identify a saved baseline estimate and reuse its model routines.

6. **Generate paper assets through code.** Exporters live in `code/paper_assets/`; selected figures/tables live in `output/paper_assets/`; manuscript sources live in `papers/`. Record which generator and saved run produced each selected exhibit. Correct generated numbers at their source and rebuild.

7. **Keep current choices easy to find.** Update `docs/current.md` with the current specification, selected runs, governing plan, development target, and authoritative manuscript. Distinguish a model's role (main, comparison, exploratory, retired) from its validation status. Use stable package names; record changes in role rather than renaming packages whenever preferences change.

8. **Keep writing workflows explicit.** Track local `.tex`/`.bib` sources in `papers/`; ignore compiled PDFs and build files. If using Overleaf, keep `overleaf/` self-contained and identify the authoritative version. Reconcile coauthor edits before transferring selected sources and generated assets; folder placement alone does not synchronize them.

9. **Close explorations and archive selectively.** Put experimental code in `code/explore/<question>/`, findings in `docs/explore/<question>/`, and results in `output/results/explore/<question>/<specification>/`. Record whether to promote, retain, continue, or retire the work. For archived material, record the reason, replacement, source revision, and execution status. Check callers, imports, paths, and TeX inputs before moving files.

Use descriptive lowercase names with underscores; reserve numbering for useful order. Keep conventional names such as `README.md` and language extensions such as `.R`. Replace example names with meaningful project names and remove unused folders. Git preserves committed source history; historical reruns also need the separately stored inputs, results, and environment.
