# Public Job-Search Agent Settings

A documentation-only starting point for a separated, human-gated job-search agent team.

This repository is intended to make the team design understandable and reusable without publishing private job-search data or executable automation.

## What this project contains

The repository contains two kinds of human-readable settings for each role:

- `SOUL.md` — the role's responsibilities, boundaries, evidence rules, and handoff behavior.
- `profile.yaml` — a small public description of the role and its team grouping.

The team is divided into these bounded roles:

- **`job-scout-web` — Source Scout**
  - Reads approved public job sources and records listing evidence.
  - Verifies promising roles against official employer pages where possible.
  - Does not score jobs, tailor documents, contact employers, or apply.

- **`job-normalizer` — Normalizer**
  - Converts raw listing evidence into a consistent local format.
  - Preserves source identity, timestamps, stable IDs, and duplicate relationships.
  - Does not browse for applications or make fit judgments.

- **`job-assessor` — Fit Assessor**
  - Scores normalized roles against a locally supplied candidate profile and criteria.
  - Records evidence, strengths, risks, unknowns, and one recommendation.
  - Does not invent candidate facts or create application documents.

- **`job-coordinator` — Coordinator and Tracker**
  - Coordinates the other roles and maintains the human-facing status of the search.
  - Reports new listings, blockers, decisions, and approval state.
  - Does not browse, submit applications, contact employers, or infer approval from silence.

- **`cv-tailor` — Document Generator**
  - Creates final CV and cover-letter packages only for an explicitly approved exact role.
  - Preserves the master CV and records material gaps and unknowns.
  - Never submits applications or contacts employers.

## What this project deliberately excludes

This public repository does **not** include:

- application code or deterministic workflows
- candidate profiles, CVs, accomplishments, or personal information
- job databases, raw listings, normalized records, or reports
- generated application documents
- credentials, tokens, passwords, browser state, cookies, or local Hermes configuration
- executable scripts, deployment settings, or provider secrets

The files use `<JOB_SEARCH_ROOT>` or general local-workspace language rather than a real user's filesystem path.

## How to start using it

These settings are documentation, not a runnable package. To use them with an agent platform:

1. Create a private local job-search workspace.
2. Create one separate agent/profile for each role listed above.
3. Copy the matching `SOUL.md` into each profile as its role instruction.
4. Use the `profile.yaml` description as the profile metadata; do not treat it as a complete runtime configuration.
5. Keep candidate data, job records, reports, application files, credentials, and browser sessions outside this public repository.
6. Configure each agent with only the tools it needs. In particular:
   - Scout: approved read-only retrieval tools.
   - Normalizer: local file/database tools, not browsing.
   - Assessor: local evidence and narrowly scoped verification tools.
   - Coordinator: coordination and tracker tools, not browsing or submission tools.
   - CV Tailor: local document tools, not submission or employer-contact tools.
7. Define your own approved sources, freshness rule, candidate criteria, storage paths, and human approval policy privately.
8. Run a small read-only test with synthetic or non-sensitive data before connecting real candidate records or authenticated sources.
9. Review every role boundary and output before allowing the team to process real data.

## Operating principle

Keep the pipeline human-gated:

```text
Scout → Normalizer → Assessor → Coordinator → user decision → CV Tailor
```

Discovery and assessment are not permission to apply. External communication, application submission, account changes, credentials, and live-data changes remain separate actions requiring explicit authorization.

## Security note

Anyone can copy a public repository. Treat this repository as public documentation. Never add private profile files, `.env` files, databases, reports, application packages, browser profiles, or credentials. If private material is ever committed, rotate affected credentials and remove the material from the complete Git history—not only from the latest revision.
