# AI-Study-Coach-: verification and operations

Reviewed against [default-branch commit 70758a61bc2d](https://github.com/noel-ult/AI-Study-Coach-/commit/70758a61bc2dfb83714352a8e5a0f92f8edb41de) on 2026-10-28. Start with the [developer guide](PROJECT_GUIDE.md) for installation and architecture, and the [source reference](REFERENCE.md) for exact scripts, configuration readers, routes, and source locations.

## Supabase study sessions

Exercise health, signup/login, a study session, AI behavior, and group resource ownership with isolated accounts. Legacy SQLite tests are not current Supabase coverage.

These are acceptance scenarios for a maintainer to run in the documented environment. Their inclusion is not a claim that live integrations or production credentials were tested during this documentation update.

## Deployment and failure diagnosis

Set DATABASE_URL as well as the required Supabase server credentials. Review SQL as migrations against the actual schema; never execute all historical fixes as a batch.

## Maintaining the contract

When behavior changes, update the guide and examples in the same PR. Check the entry point and working directory before copying commands. Use the linked source readers to distinguish build-time configuration from process environment. For failures, capture the first application error, runtime version, selected mode, and redacted configuration names before later proxy or port errors.

Keep changes tied to evidence: a declared command is not proof it passes, a process health response is not a successful end-to-end workflow, and a historical report describes its own revision. Record actual check results and any unavailable external services in the PR.
