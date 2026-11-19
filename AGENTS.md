# Repo

Solidity fund-manager contracts for QCABC (Foundry). Handles deposits, redemptions, share pricing, and portfolio updates. This is money-related code. There is no Vercel app here; the UI lives in `qcabc-fund-manager-ui`.

# Commands

- Install: `make install` (or `forge install`)
- Build: `make build` or `forge build`
- Tests: `make test` or `forge test`
- Format: `make format` or `forge fmt`

Do not run `make deploy` or other deploy targets unless Blake explicitly asked to deploy.

# Verify

`standard` (default in this repo, because it is money/contract code): `forge build` and existing tests for the touched area pass, and the diff matches the ask. Do not add tests.

# Ship mode

`ship_mode: pr`. Open a PR and wait for Blake. If Blake says "commit to main" or "ship it direct" for a task, the agent may commit to `master` (default branch) once verify passes. That still does not authorize a contract deploy.

# Task sizing

Small is the default and needs no planning step. Large means multi-area features, schema or migrations, auth, payments or money, about 300 lines or more or about 8 files or more, or Blake saying "plan this". Large tasks get a plan split into small PRs.

# Don'ts

- No new tests, CI workflows, or dependencies unless asked.
- Do not read real `.env` files or print secrets, keys, or account names. Agents never commit secrets.
- Do not merge, deploy, broadcast, or verify contracts without Blake's go-ahead.
- Do not change fee, whitelist, oracle, or access-control behavior unless that is the ask.
- Handle token amounts with the correct decimals (USDC is 6).

# Review

One pass, blockers only, at most 2 fix rounds. Do not nitpick small improvements or get stuck in a loop.
