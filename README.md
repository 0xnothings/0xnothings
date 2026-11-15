# 0xnothings

Zero-dependency Node.js tooling. Every tool in every repo runs with plain `node tools/<name>.js` — no `npm install`, no build step, no framework.

## Repositories

| Repo | What it is |
|---|---|
| [tools-security](https://github.com/0xnothings/tools-security) | Recon, web-app testing, secrets, CVE intel, static audit |
| [tools-devops](https://github.com/0xnothings/tools-devops) | Deploy gates, config hygiene, log analysis, host audits |
| [tools-web](https://github.com/0xnothings/tools-web) | Scraping, feeds, API pagination, metadata extraction |
| [tools-data](https://github.com/0xnothings/tools-data) | CSV/JSON/ZIP/binary format handling, text analytics |

## Conventions

Every tool follows the same contract. Learn it once, use it everywhere.

```bash
node tools/<name>.js --help     # usage, always exits 0
node tools/<name>.js <input>    # human table
node tools/<name>.js <input> --json   # machine output
```

- **Standard library only.** Node 18+ builtins. Nothing else.
- **Exit codes are meaningful.** `0` clean, `1` findings or blocked, `2` CI gate tripped.
- **Read-only by default.** Tools that write take an explicit `--out` and never in-place mutate.
- **Conservative defaults.** Rate limits and concurrency start low. Raise them yourself when you own the target.

## Why zero dependencies

A 200-line tool that pulls 40 transitive packages is not a tool, it is a liability. No lockfile churn, no supply-chain surface, no `npm audit` noise. The whole repo is auditable in an afternoon.

## License

MIT — Copyright (c) 2026 0xnothings
