# Research repository template

**Author:** Phuong Ho

**Version:** 2026-10-19

**Reusable repository template for reproducible empirical & structural research, with task-based code layout, Dropbox/Overleaf rules, and AI agent instructions.**

A starter layout for research projects: organize code by task, preserve data provenance, and keep generated results separate from source files. Adapt the example names and remove components your project does not need.

When using this template, replace this introduction with your **project title, research question, authors, data sources, methods, and current status**. Fill in the setup details below and update [current decisions](docs/current.md).

# Contents

## Layout

```text
project/
├── README.md                         # Project overview, setup, and sharing
├── notes_organize_repo.md            # Organization rules/notes for users
├── AGENTS.md                         # Instructions for AI coding agents
├── CLAUDE.md                         # Imports AGENTS.md for Claude Code
├── .gitignore                       # Shared Git exclusions
├── code/                            # Executable source, grouped by task
│   ├── data_prep/
│   │   ├── clean_s1/                 # Clean a source dataset
│   │   └── make_m1/                  # Construct the main dataset
│   ├── reduced_form/descriptive/     # Descriptive or reduced-form analysis
│   ├── structural_esti/baseline/     # Model routines and estimation
│   ├── counterfactuals/baseline/      # Scenarios using saved estimates
│   ├── explore/sample_check/         # Provisional investigation
│   └── paper_assets/                 # Figure, table, and numeric exporters
├── raw_data/                        # Original inputs; Dropbox
├── processed_data/                  # Derived datasets; Dropbox
│   └── for_structural_model/        # Estimator-ready inputs
├── literature/                      # Reading collection; Dropbox
├── docs/                            # Internal research documents
│   ├── current.md                   # Current choices and selected runs
│   ├── models/baseline/             # Model specification and estimation plan
│   ├── plans/                       # Plans spanning multiple tasks
│   ├── explore/sample_check/        # Exploratory questions, findings, and next steps
│   └── meetings/                    # Shared notes and decisions
├── papers/                          # Local manuscript and slide sources
│   └── sections/                    # Manuscript sections
├── overleaf/                        # Optional shared manuscript workspace
├── output/                          # All generated results; Dropbox
│   ├── artifacts/                   # Intermediate objects and caches
│   ├── results/                     # Mirrors code/: <category>/<task>/<specification>/
│   │   ├── reduced_form/descriptive/
│   │   ├── structural_esti/baseline/
│   │   ├── counterfactuals/baseline/
│   │   └── explore/sample_check/
│   └── paper_assets/
│       ├── figures/                 # Selected manuscript figures
│       └── tables/                  # Selected manuscript tables
└── archive/                         # Selected retired reference material
    ├── code/
    └── docs/
```

The task folders are examples, with `.gitkeep` placeholders rather than executable analysis. See [organization rules](notes_organize_repo.md).

## Sharing strategy

| Material | Shared through | Git policy |
|---|---|---|
| `code/`, `docs/`, authored `papers/` sources, selected `archive/` material, environment specifications | GitHub | Track |
| `raw_data/`, `processed_data/` payloads | Dropbox | Ignore data; track `.gitkeep` placeholders and any data `README.md` files |
| `output/` figures, tables, and run records | Dropbox | Ignore files; track `.gitkeep` placeholders for the folder structure |
| `literature/` | Dropbox | Track `.gitkeep` placeholders only |
| `overleaf/` | Overleaf | Track `.gitkeep` placeholders only in this repository |
| Environments, local configuration, caches, compiled papers | Each collaborator's machine | Ignore |

Keep Dropbox-backed folders available at the paths above, using local links or documented path configuration. Keep machine-specific paths out of committed source. Folder names do not configure Dropbox or Overleaf synchronization.

GitHub collaborators can read committed local drafts. Record the authoritative manuscript and Overleaf transfer procedure in [`docs/current.md`](docs/current.md). Share only data you have permission to distribute.

## Set up a project

1. Copy this template into your project. Rename example tasks and remove unused components.
2. Record the GitHub repository, Dropbox location/access contact, and optional Overleaf project here.
3. Obtain the Dropbox files and expose them at the documented paths. Git preserves the `raw_data/`, `processed_data/`, `output/`, `literature/`, and `overleaf/` folder structure through `.gitkeep` placeholders and ignores data/output payloads inside. Add a `.gitkeep` to each new folder you want to preserve.

4. Record required software/versions and commit the appropriate dependency specification. Document environment setup and exact execution commands below. Launch analysis from the repository root unless documented otherwise.
5. Fill in data provenance and [current decisions](docs/current.md). Review [`.gitignore`](.gitignore) before committing; ignore rules do not untrack existing files.

**Project setup details:** GitHub: [URL]; Dropbox/access: [location/contact]; Overleaf: [URL or unused]; software/setup: [instructions].