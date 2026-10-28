# Veritas-ai: verification and operations

Reviewed against [default-branch commit e125ee50b8d0](https://github.com/noel-ult/Veritas-ai/commit/e125ee50b8d0f347a7c8939a8251b9d06fac5f69) on 2026-10-28. Start with the [developer guide](PROJECT_GUIDE.md) for installation and architecture, and the [source reference](REFERENCE.md) for exact scripts, configuration readers, routes, and source locations.

## Interview lifecycle

Start with a checked-in candidate, answer a question, retrieve state, end the interview, and check unknown/completed sessions. Distinguish deterministic fallback from a successful live provider call.

These are acceptance scenarios for a maintainer to run in the documented environment. Their inclusion is not a claim that live integrations or production credentials were tested during this documentation update.

## Deployment and failure diagnosis

In-memory session storage needs explicit planning before multiple workers or restarts. Check frontend proxy destination and seed-file availability in container deployments.

## Maintaining the contract

When behavior changes, update the guide and examples in the same PR. Check the entry point and working directory before copying commands. Use the linked source readers to distinguish build-time configuration from process environment. For failures, capture the first application error, runtime version, selected mode, and redacted configuration names before later proxy or port errors.

Keep changes tied to evidence: a declared command is not proof it passes, a process health response is not a successful end-to-end workflow, and a historical report describes its own revision. Record actual check results and any unavailable external services in the PR.
