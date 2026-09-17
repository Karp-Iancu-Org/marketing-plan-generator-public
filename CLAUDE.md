# Marketing Plan Generator

This project constructs a complete, execution-ready marketing plan for **any niche** from a PRD, applying the Acquisition.com/Mozi marketing-workshop lessons (Aug 2026). The output is **two coupled plans** — a paid advertising plan (folders 01–06) and an organic-social plan (folder 07) — that share avatars, capture systems, the monthly shoot, and the measurement join, plus optionally a matching pair of executive-brief PDFs.

**If the user has provided (or points you at) a niche PRD: read `GENERATOR.md` and follow it end to end.** It defines the whole workflow — PRD ingestion, the intake interview, avatar research, template instantiation, and the QA gate. Do not improvise a different structure.

## Folder map

| Path | What it is |
|---|---|
| `GENERATOR.md` | The orchestration playbook — the algorithm you follow |
| `INTAKE-QUESTIONNAIRE.md` | The full question set (§1–§9) with PRD-extraction hints and defaults |
| `lessons/` | The workshop corpus: 9 session breakdowns + `INDEX.md` (the deduped rulebook) + `README.md` (how to read them) |
| `lessons/transcripts/` | The raw workshop transcripts the breakdowns were distilled from — primary source, read when a breakdown needs verifying or expanding |
| `templates/` | One template per output document, with `{{PLACEHOLDER}}` sources and `<!-- MODEL: -->` variants (lead-gen / app / ecom) |

## Ground rules

- Ask the intake questions in batches via AskUserQuestion; never silently guess what the PRD doesn't say.
- Avatars are built from interview + external research (competitor reviews, app-store reviews, communities, Meta Ad Library) with every claim traceable to evidence — there is no customer-data-mining path in this generator.
- The avatar checkpoint (GENERATOR.md step 3) is mandatory before any downstream doc is generated.
- **Output goes to `niches/<niche-slug>/marketing-plan/` inside THIS project — never into the niche's own codebase.** `niches/` is already gitignored here, so plans stay local and never push; no per-build git setup is needed.
- **The niche's project is a source to read, not a target to write.** Take the offer, price, ICP, geography and voice specs from its PRD and prompt files; disregard its tech stack, schema and roadmap. Do not create files in it, do not modify its `.gitignore`, do not touch its git config.
- The lessons corpus stays here and is referenced, not copied.
- Calibrate quality from each template's QA checklist and the standalone, evidence, cross-reference, and invariant checks in `GENERATOR.md`; this public framework intentionally contains no completed niche plan.
