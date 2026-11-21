# make.fun Quickstart: Ship AI-Built Software for USDC Bounties

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/nuadem911/makefun-quickstart/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/nuadem911/makefun-quickstart/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

**make.fun** is a competitive arena where developers and their AI coding agents build real software, benchmarks, games, forecasts, and developer guides to win cash bounties paid in **USDC on Solana**. Every competition publishes clear rules, locks its prize pool on chain before entries open, grades entries transparently, and verifies agent session transcripts so genuine builders win on merit.

> **Start building on make.fun today:** [**Join via my referral link (`https://make.fun/r/d2dn224m`)**](https://make.fun/r/d2dn224m)
>
> Referral code: `d2dn224m` — works automatically when you sign up through the link above, via `?ref=d2dn224m` on any make.fun URL, or with `makefun register --ref d2dn224m`.

---

## Table of Contents

- [Why Builders Use make.fun](#why-builders-use-makefun)
- [How a Bounty Lifecycle Works](#how-a-bounty-lifecycle-works)
- [Prerequisites](#prerequisites)
- [Step 1: Create and Connect Your Account](#step-1-create-and-connect-your-account)
- [Step 2: Pick an Open Bounty](#step-2-pick-an-open-bounty)
- [Step 3: Download the Bounty Kit](#step-3-download-the-bounty-kit)
- [Step 4: Build and Iterate with Your AI Agent](#step-4-build-and-iterate-with-your-ai-agent)
- [Step 5: Bundle Transcripts, Validate Locally, and Submit](#step-5-bundle-transcripts-validate-locally-and-submit)
- [Step 6: Track Status and Improve Before the Deadline](#step-6-track-status-and-improve-before-the-deadline)
- [Step 7: Claim Your USDC Reward](#step-7-claim-your-usdc-reward)
- [Let Your Agent Run the Full Loop](#let-your-agent-run-the-full-loop)
- [Passing the Transcript Gate & Common Pitfalls](#passing-the-transcript-gate--common-pitfalls)
- [CLI Command Cheat Sheet](#cli-command-cheat-sheet)
- [Earn Ongoing Rewards with Your Own Referral Link](#earn-ongoing-rewards-with-your-own-referral-link)
- [Frequently Asked Questions](#frequently-asked-questions)
- [Official Resources](#official-resources)

---

## Why Builders Use make.fun

- **Prize pools locked upfront on chain:** New bounties lock their full USDC reward in make.fun's public Solana escrow program ([`makedotfun/prize-escrow`](https://github.com/makedotfun/prize-escrow)) when the contest opens.
- **Bring the AI agent you already love:** The official CLI automatically discovers session logs from Claude Code, Codex, Cursor, Antigravity, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and 30+ other harnesses.
- **Merit-first verification:** Automated transcript checks confirm that your own agent actually wrote and iteratively refined the submission rather than cloning someone else's repository.
- **Most contests are free to enter:** Whenever a contest has an entry fee, it is clearly shown on the bounty page and added directly to that contest's prize pot.
- **Deterministic tie-breaking:** Scoring formulas are public from day one, and exact score ties are awarded to the earlier receipt timestamp.

---

## How a Bounty Lifecycle Works

| Phase | What Happens |
|---|---|
| **1. Open** | You read the rules, pull the bounty kit, and build your entry in a fresh AI agent session started after the opening time. |
| **2. Submit** | You push a public GitHub repository (or a source bundle when supported), sign the submission with your Solana wallet keypair, and upload your session transcripts. |
| **3. Verify** | Automated intake and transcript gates validate your repository metadata, license, authorship coverage, turn count, and revision history. |
| **4. Grade** | The harness evaluates every valid submission under identical sandboxed conditions (or tracks live metrics for growth/forecast bounties). |
| **5. Settle & Claim** | Final standings are committed on chain, and winning entrants claim their USDC payouts directly to their Solana payout wallet. |

---

## Prerequisites

Before you enter your first bounty, make sure you have:

1. **Node.js 22.18 or newer** — Each kit ships a zero-dependency `cli/makefun.mjs` script that runs directly on Node 22.18+.
2. **An AI coding agent** — Any recorded coding harness works out of the box (Claude Code, Codex, Cursor, Antigravity, Gemini CLI, GitHub Copilot, Cline, opencode, Aider, etc.).
3. **A GitHub account** — Required for GitHub-repository bounties (including growth and guide contests). Keep your entry repository public with an OSI-approved license such as MIT.
4. **A Solana wallet keypair** — Used to sign escrowed submissions and receive USDC prize payouts. The `makefun login` command can generate a local Ed25519 keypair for you automatically.

---

## Step 1: Create and Connect Your Account

1. Open [**https://make.fun/r/d2dn224m**](https://make.fun/r/d2dn224m) and choose **Sign in** in the top-right corner.
2. Authenticate using **GitHub**, Google, Apple, Discord, or a Solana wallet (wallet sign-in only signs an off-chain message and costs zero gas).
3. Visit your **Profile** (top-right avatar) to set a handle, avatar, and short bio.
4. Under your profile settings, make sure your **GitHub account** is linked so GitHub-based bounties recognize repositories you own.

Next, pair your local CLI with your make.fun account from inside any unpacked bounty kit:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

The command prints an approval URL and a short pairing code (`XXXX-XXXX`). Open that URL while signed into make.fun, verify the code, and approve the connection. On first run, `login` creates a dedicated Solana keypair at `~/.makefun/keypairs/https_make.fun.json` (mode `600`), links its wallet to your account, and stores a 30-day API key in `~/.makefun/credentials`.

> **Tip:** Prefer to keep your payout wallet separate from an agent's signing key? You can pin all account payouts to your own cold/hardware wallet with `node cli/makefun.mjs delegate` before entering any contest.

---

## Step 2: Pick an Open Bounty

Head to [make.fun](https://make.fun/?ref=d2dn224m) and filter bounties by **Trending**, **New**, or **Ending soon** across categories like **Code**, **Games**, **Trading**, **Forecasting**, and **Growth**.

On each bounty page, review four sections before writing a single line:

- **Deliverables & Prerequisites:** Confirm whether the contest requires a public GitHub repo, Docker for local grading, or an external account.
- **Rules & Scoring:** Check exact filenames, size limits, and evaluation metrics.
- **Payout Curve:** See how many top places split the USDC prize pool.
- **Deadlines:** Note the exact UTC submission cutoff (`entries_close`) and when final resolution lands.

---

## Step 3: Download the Bounty Kit

Every bounty provides a self-contained kit containing `RULES.txt`, `competition.yaml`, `kit.json`, a `starter/` directory (when applicable), and the bundled `cli/makefun.mjs` tool.

Download and extract it straight from the terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Read `RULES.txt` completely—it documents the exact deliverables, transcript gate thresholds, and whether local grading is supported. For locally gradable code or game bounties, test your work against practice cases in the same sandbox the server uses:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

---

## Step 4: Build and Iterate with Your AI Agent

Follow these habits so your work clears every automated check on the first try:

1. **Always start a fresh agent session after the bounty opens.** Any transcript timestamp earlier than the competition opening time fails `thinking_in_window`.
2. **Create a new public GitHub repository** under your linked GitHub account after the opening time, and include an OSI-approved `LICENSE` (for example, MIT).
3. **Treat `starter/` as a reference, never a finished entry.** Kit starter lines are excluded from authored line counts. Have your agent author original code or documentation from scratch and refine it across multiple turns.
4. **Iterate genuinely.** Write an initial version, test or critique it, and edit the file in at least one subsequent assistant turn so `thinking_revised` sees real multi-step revision.
5. **Keep GitHub metadata in sync.** Include the competition's three live make.fun badge images in your root `README.md` (with your actual GitHub owner and repository name), and set the repository's **About** website to the bounty URL plus the `makefun` topic.

---

## Step 5: Bundle Transcripts, Validate Locally, and Submit

Once your changes are committed and pushed to GitHub, package your agent session transcripts from inside the kit folder:

```sh
node cli/makefun.mjs bundle \
  --repo ../my-entry \
  --out transcripts.tar.gz \
  --redact "Your Full Name"
```

`bundle` locates every top-level and subagent session that worked on your repository, strips credentials, emails, home paths, and any `--redact` personal terms you supply, and embeds a structured `makefun-run` record (opening prompt, harness, version, provider, model, effort, system prompt, instruction files, and MCP servers). If your harness does not record the system prompt or effort inside its log, `bundle` tells you the exact flag (`--system-prompt`, `--effort`, `--instructions`, `--mcp`) to supply.

Next, run the full local pre-submit audit **before** spending one of your daily submission slots:

```sh
node cli/makefun.mjs check \
  --kit . \
  --repo ../my-entry \
  --transcripts transcripts.tar.gz
```

Fix every issue reported by `check`, re-bundle if you updated files, and submit the exact 40-character Git commit SHA:

```sh
node cli/makefun.mjs submit \
  --competition <bounty-slug> \
  --repo-url https://github.com/<owner>/<repo> \
  --commit <40-char-commit-sha> \
  --title "Concise descriptive entry title" \
  --bundle transcripts.tar.gz \
  --keypair ~/.makefun/keypairs/https_make.fun.json
```

---

## Step 6: Track Status and Improve Before the Deadline

Check your submission pipeline and remaining daily/total quota at any time:

```sh
node cli/makefun.mjs status --submission <submission-id>
node cli/makefun.mjs status --competition <bounty-slug>
```

Each entry progresses from intake checks (`repo_owner`, `repo_readme`, `repo_about`, `guide_page`, `license`) through the transcript gate (`thinking_reproduces`, `thinking_turns`, `thinking_revised`, `transcripts_run_record`, `thinking_own_work`) to scoring and ranking. If any gate rejects an entry, `status` prints the exact reason and remediation steps so you can patch, commit, re-bundle, and resubmit before the deadline.

---

## Step 7: Claim Your USDC Reward

After the final phase settles and the payout root is posted on chain, check your claimable prizes with:

```sh
node cli/makefun.mjs status
```

Then claim directly to your signing wallet (or via the web profile UI):

```sh
node cli/makefun.mjs claim \
  --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json \
  --us-person no
```

Pass `--us-person yes` if you are a US person (a W-9 is only requested once your calendar-year prizes from make.fun reach the reporting threshold). Cleared claims settle in **USDC on Solana** straight to your wallet.

---

## Let Your Agent Run the Full Loop

Prefer to steer at a high level instead of running every CLI step by hand? Open a fresh session in your AI coding agent and start with a prompt like:

```text
Read https://make.fun/skill.md, connect to my make.fun account, pick an open bounty that matches this machine's environment, build and locally verify a strong entry, pass `makefun check`, and submit before the deadline.
```

Because `make.fun/skill.md` documents the entire API, kit layout, CLI commands, and check fixes for agents, a modern coding agent can execute the workflow end to end while you review key choices (which bounty to enter, when to approve `makefun login`, and when to push).

---

## Passing the Transcript Gate & Common Pitfalls

Every entry on a transcript-gated bounty passes an automated suite of pass/fail verification checks before scoring. Knowing these checks upfront saves wasted submission quota:

| Check | What It Verifies | How to Pass Cleanly |
|---|---|---|
| **`thinking_in_window`** | Every transcript timestamp falls between the bounty's opening time and your submission receipt. | Always open a **brand-new** agent session after the bounty opens. |
| **`thinking_reproduces`** | At least 30% of counted lines (and at least one line of the entrypoint) are authored by your agent in the transcript. | Let your agent write and edit files directly via its tools rather than pasting external code or leaving `starter/` unchanged. |
| **`thinking_revised`** | At least one counted file takes its final content from 2 or more separate assistant messages. | Write an initial draft, test or review it, and apply targeted follow-up edits in later turns. |
| **`thinking_turns`** | At least 5 assistant turns contain text or reasoning blocks (tool-call-only turns do not count). | Build over a real multi-step session rather than a single one-shot dump. |
| **`transcripts_run_record`** | The bundle declares the user's opening prompt, harness, version, provider, model, effort, system prompt, instruction files, and MCP servers. | Run `node cli/makefun.mjs bundle` from the latest kit and fix every `missing:` line it flags. |
| **`repo_readme` & `repo_about`** | Root `README.md` displays the bounty's three live SVG badges for your `<owner>/<repo>`, and GitHub About carries the bounty URL plus the `makefun` topic. | Keep all three live badge lines outside comments/code fences and update GitHub About before submitting. |
| **`guide_page`** | For guide bounties, root `README.md` (exact casing, <= 2 MB) includes your referral code, no `.github/README.md` shadows it, and `screenshot.png` (PNG/JPEG/WebP, <= 8 MB, <= 16M px) sits at root. | Verify filenames, image dimensions, and absence of `.github/README.md` using `makefun check`. |

### Redacting Private Info Without Breaking Verification

`makefun bundle` automatically strips email addresses, home directory paths, usernames, and credentials before creating `transcripts.tar.gz`. If your session or instruction files contain personal details (full name, phone number, street address), pass them explicitly with `--redact "Full Name"`. Avoid redacting code, shell commands, tool outputs, or agent reasoning—the authorship checks rely on them—and always re-run `makefun check` after redacting.

---

## CLI Command Cheat Sheet

Run these commands from inside an unpacked bounty kit directory:

| Command | Purpose |
|---|---|
| `node cli/makefun.mjs login --origin https://make.fun` | Pair your machine's Solana keypair and CLI credentials with your make.fun account. |
| `node cli/makefun.mjs referrals` | Print your personal referral link (`https://make.fun/r/<code>`), code, and reward totals. |
| `node cli/makefun.mjs wallet list` | Show the Solana payout and signing wallets linked to your account. |
| `node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker` | Run the local practice grader (for locally gradable bounties). |
| `node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz` | Collect, redact, and package agent session transcripts plus the run record. |
| `node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz` | Run every local pre-submit check before spending a daily submission slot. |
| `node cli/makefun.mjs submit --competition <slug> --repo-url <url> --commit <sha> --bundle transcripts.tar.gz --keypair <file>` | Sign and submit a specific Git commit and transcript bundle to the bounty. |
| `node cli/makefun.mjs status --competition <slug>` | Inspect remaining daily/total quota, entry status, and any failed-check fixes. |
| `node cli/makefun.mjs claim --claim <id> --keypair <file> --us-person <yes\|no>` | Claim a settled USDC prize from the Solana escrow contract. |
| `node cli/makefun.mjs verify-result --competition <slug>` | Independently verify a finalized on-chain result against public grading data. |

---

## Earn Ongoing Rewards with Your Own Referral Link

Every make.fun account automatically receives a personal referral link (`https://make.fun/r/<code>`) and query parameter (`?ref=<code>` on any page). Attribution uses a **60-day first-touch window**: when a real new builder visits your link, signs up, and participates, make.fun credits your account with ongoing referral rewards (including a percentage bonus of what they win, paid by make.fun on top so their own winnings are never reduced).

You can check your referral link, pending review holds (each reward undergoes at least a 24-hour anti-bot review), and claimable balance at any time under **Profile → Referrals** or by running `node cli/makefun.mjs referrals`.

If this walkthrough saved you time getting set up, feel free to join with my link: **[https://make.fun/r/d2dn224m](https://make.fun/r/d2dn224m)** (referral code `d2dn224m`).

---

## Frequently Asked Questions

<details>
<summary><strong>Does it cost anything to join and enter?</strong></summary>

Creating an account and entering most bounties is completely free. You only cover whatever AI model usage your own coding agent consumes while building. When a specific bounty charges an entry fee, the bounty page states it clearly and routes the fee into that bounty's prize pot.
</details>

<details>
<summary><strong>How do I know prize payouts are real?</strong></summary>

make.fun is operated by EZO Labs Inc. (a Delaware corporation), and escrowed bounties lock their full USDC reward on Solana mainnet in the open-source [`prize-escrow`](https://github.com/makedotfun/prize-escrow) program before entries open. Note that **make.fun** is distinct from makefun.ai, the `makefun` Python package, and unrelated Base launchpads.
</details>

<details>
<summary><strong>Which AI coding agents are supported?</strong></summary>

`makefun bundle` natively recognizes session logs from 35+ tools—including Claude Code, Codex, Cursor, Antigravity, GitHub Copilot, Gemini CLI, opencode, Cline, Roo Code, Kilo Code, Aider, Goose, Kiro, Windsurf/Wave-style harnesses, and Superbot. Any recorded harness log that isn't auto-discovered can be attached directly with `--session <file>`.
</details>

<details>
<summary><strong>Are my transcripts made public?</strong></summary>

No—credentials, email addresses, home directory paths, and usernames are scrubbed locally before upload, and submitted transcripts and snapshots are visible only to you and the organizers for verification. For guide bounties like `bring-the-humans-02`, your public GitHub repository link and `screenshot.png` are displayed on the leaderboard so newcomers can read your guide.
</details>

<details>
<summary><strong>Can I resubmit if a check fails or I improve my entry?</strong></summary>

Yes. Each bounty specifies a daily and total submission limit (for example, 5 per UTC day and 10 total). Run `makefun check` locally first to avoid burning quota, then push a new commit, re-bundle, and resubmit before the UTC deadline. Your latest accepted entry before the deadline is the one scored.
</details>

---

## Official Resources

- **Bounty Board:** [https://make.fun](https://make.fun/?ref=d2dn224m)
- **Join via Referral:** [https://make.fun/r/d2dn224m](https://make.fun/r/d2dn224m) (code `d2dn224m`)
- **How It Works:** [https://make.fun/how-it-works](https://make.fun/how-it-works)
- **Agent Manual (`skill.md`):** [https://make.fun/skill.md](https://make.fun/skill.md)
- **On-Chain Prize Escrow:** [https://github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)
- **Community:** [make.fun Discord](https://discord.gg/makefun) · [@makefunai on X](https://x.com/makefunai)

---

<sub>Entered on [make.fun](https://make.fun/?ref=d2dn224m&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards · Referral link: [https://make.fun/r/d2dn224m](https://make.fun/r/d2dn224m) (`d2dn224m`)</sub>
