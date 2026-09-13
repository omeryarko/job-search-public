# Public Job-Search Agent Settings

This repository contains only human-readable role instructions and profile descriptions for a separated job-search agent team.

It intentionally excludes:

- application code and deterministic workflows
- candidate profiles, CVs, accomplishments, and personal data
- job databases, raw listings, normalized records, and reports
- credentials, tokens, browser state, cookies, and local Hermes configuration
- executable scripts and deployment configuration

The settings describe bounded roles:

- `job-scout-web`: read-only source discovery
- `job-normalizer`: evidence normalization and deduplication
- `job-assessor`: evidence-based fit assessment
- `job-coordinator`: coordination and tracker ownership
- `cv-tailor`: document generation only after exact-role approval

Paths are written as placeholders (`<JOB_SEARCH_ROOT>`) and must be adapted locally. These files are documentation, not a runnable agent package.
