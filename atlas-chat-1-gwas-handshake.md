# I want the repos in a markdown table for a new github repo and file what's agood way to do this for these 24 repos

Perfect — you’re on the right page for `https://github.com/orgs/handshake-org/repositories`, and there are **24 repos** listed. Let’s make a Markdown table that’s ready to drop into a new GitHub repo (like `README.md` or `docs/repos.md`).

Here’s a clean, semantic, **copy-ready** version:

```markdown
# Handshake Org Repositories

| # | Repository | Description | Language | ⭐ Stars | 🍴 Forks |
|---|-------------|--------------|-----------|----------|-----------|
| 1 | [hsd](https://github.com/handshake-org/hsd) | Handshake Daemon & Full Node | JavaScript | 2k | 299 |
| 2 | [goosig](https://github.com/handshake-org/goosig) | Anonymous RSA signatures | C | 67 | 15 |
| 3 | [bfilter](https://github.com/handshake-org/bfilter) | Bloom filters for JavaScript | JavaScript | 0 | 16 |
| 4 | [handshake-web](https://github.com/handshake-org/handshake-web) | Handshake.org static website | HTML | 28 | 23 |
| 5 | [hs-client](https://github.com/handshake-org/hs-client) | REST, websocket, and RPC client for hsd | JavaScript | 86 | 37 |
| 6 | [handshake-org.github.io](https://github.com/handshake-org/handshake-org.github.io) | Developer documentation site | JavaScript | 82 | 65 |
| 7 | [hnsd](https://github.com/handshake-org/hnsd) | Handshake SPV name resolver | C | 299 | 59 |
| 8 | [HIPs](https://github.com/handshake-org/HIPs) | Handshake Improvement Proposals | — | 41 | 24 |
| 9 | [hs-airdrop](https://github.com/handshake-org/hs-airdrop) | Decentralized airdrop to open-source developers | JavaScript | 1.4k | 174 |
| 10 | [hsd-ledger](https://github.com/handshake-org/hsd-ledger) | JavaScript client for Handshake Ledger | JavaScript | 18 | 10 |
| 11 | [ledger-app-hns](https://github.com/handshake-org/ledger-app-hns) | Handshake app for Ledger Nano S | C | 19 | 12 |
| 12 | [hs-names](https://github.com/handshake-org/hs-names) | Pre-reserved Handshake names | C | 30 | 11 |
| 13 | [faucet-tool](https://github.com/handshake-org/faucet-tool) | Generate mnemonic seeds, keys, and addresses for Faucet | JavaScript | 34 | 8 |
| 14 | [hs-names-2023](https://github.com/handshake-org/hs-names-2023) | Handshake 2023 soft fork updated locked names | JavaScript | 1 | 1 |
| 15 | [urkel](https://github.com/handshake-org/urkel) | Cryptographically provable database (urkel tree) | JavaScript | 126 | 21 |
| 16 | [hs-rosetta](https://github.com/handshake-org/hs-rosetta) | Coinbase Rosetta integration | JavaScript | 13 | 6 |
| 17 | [hdns](https://github.com/handshake-org/hdns) | Handshake-capable DNS module for Node.js | JavaScript | 36 | 8 |
| 18 | [hs-miner](https://github.com/handshake-org/hs-miner) | Mining infrastructure for Handshake | C | 75 | 18 |
| 19 | [bcfg](https://github.com/handshake-org/bcfg) | Config parser for bcoin | JavaScript | 0 | 13 |
| 20 | [bns](https://github.com/handshake-org/bns) | Recursive DNS server and resolver for Node.js | JavaScript | 3 | 27 |
| 21 | [hs-tree-data](https://github.com/handshake-org/hs-tree-data) | Airdrop/faucet Merkle trees + encrypted nonces | — | 57 | 25 |
| 22 | [bcuckoo](https://github.com/handshake-org/bcuckoo) | Cuckoo Cycle in pure JavaScript | JavaScript | 16 | 3 |
| 23 | [hndshkBot](https://github.com/handshake-org/hndshkBot) | IRC bot for developer faucet | JavaScript | 3 | 1 |
| 24 | [libhns](https://github.com/handshake-org/libhns) | C library for resolving Handshake names (fork of c-ares) | C++ | 20 | 4 |
```

---

### Options for managing it going forward

1. **Auto-update via GitHub CLI**

   ```bash
   gh repo list handshake-org --limit 100 --json name,description,language,stargazerCount,forkCount \
     --jq '.[] | "| \(.name) | \(.description) | \(.language) | \(.stargazerCount) | \(.forkCount) |"' \
     | sed 's/^/| /' > repos.md
   ```

   Then wrap it with the Markdown header and table structure above.

2. **Automate in a `Makefile` or Deno script**

   * Add a Deno script (`scripts/update_repos.ts`) that fetches from the GitHub API and regenerates `README.md`.
   * This fits your broader pattern for `gwas` / `zwas` ecosystems where you’ll repeat this pattern for each org.

Would you like me to generate that **Deno script** so this table auto-updates (with stars/forks/etc.) on each run?
