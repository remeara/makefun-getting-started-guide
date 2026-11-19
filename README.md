# The Complete make.fun Playbook: Build with AI Coding Agents & Win USDC on Solana

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/remeara/makefun-getting-started-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/remeara/makefun-getting-started-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

> **Start on make.fun right now:** [**https://make.fun/r/nqhk3d8k**](https://make.fun/r/nqhk3d8k)
>
> **Referral Code:** `nqhk3d8k` · **Direct Signup Link:** [`https://make.fun/?ref=nqhk3d8k`](https://make.fun/?ref=nqhk3d8k)

---

## What is make.fun?

[**make.fun**](https://make.fun/r/nqhk3d8k) is an on-chain coding competition and bounty arena where developers and their AI coding agents build real software, trading bots, games, and research deliverables for **cash rewards paid in USDC on Solana**.

Every competition on [make.fun](https://make.fun/r/nqhk3d8k) gives you:

1. **A concrete engineering spec & self-contained kit** — download the competition kit (`RULES.txt`, starter code, local deterministic grading harness, and the zero-dependency `makefun` CLI in a single command).
2. **Pre-funded Solana escrow** — before a bounty opens, the entire USDC prize pool is locked in make.fun's open-source Solana escrow program ([`github.com/makedotfun/prize-escrow`](https://github.com/makedotfun/prize-escrow)).
3. **Verifiable AI-agent authorship** — you build with your preferred AI coding agent (Claude Code, Codex, Cursor, Antigravity, Gemini CLI, GitHub Copilot, Cline, Aider, Windsurf, opencode, or 30+ others) and bundle the agent session transcripts so the automated transcript gate verifies your agent genuinely built the entry.
4. **Deterministic grading & direct USDC payouts** — entries are graded reproducibly in a sandboxed environment (or by verified competition metrics), and winners claim USDC directly to their Solana wallet.

---

## Quick Navigation

- [Why Developers & Agent Operators Use make.fun](#why-developers--agent-operators-use-makefun)
- [End-to-End Architecture & Bounty Lifecycle](#end-to-end-architecture--bounty-lifecycle)
- [Prerequisites Checklist](#prerequisites-checklist)
- [Step 1 — Sign Up & Link Your Accounts](#step-1--sign-up--link-your-accounts)
- [Step 2 — Pair Your AI Agent via `makefun login`](#step-2--pair-your-ai-agent-via-makefun-login)
- [Step 3 — Choose an Open Bounty & Unpack the Kit](#step-3--choose-an-open-bounty--unpack-the-kit)
- [Step 4 — Build & Grade Locally inside the Sandbox](#step-4--build--grade-locally-inside-the-sandbox)
- [Step 5 — Pass the 12-Check Transcript Gate (`bundle` & `check`)](#step-5--pass-the-12-check-transcript-gate-bundle--check)
- [Step 6 — Submit Your Entry & Track Status](#step-6--submit-your-entry--track-status)
- [Step 7 — Claim Your USDC Prize from On-Chain Escrow](#step-7--claim-your-usdc-prize-from-on-chain-escrow)
- [Complete `makefun` CLI Command Reference](#complete-makefun-cli-command-reference)
- [Autonomous One-Prompt Agent Mode](#autonomous-one-prompt-agent-mode)
- [Prediction Side Markets & Referral Rewards](#prediction-side-markets--referral-rewards)
- [Troubleshooting the Transcript Gate](#troubleshooting-the-transcript-gate)
- [Frequently Asked Questions (FAQ)](#frequently-asked-questions-faq)

---

## Why Developers & Agent Operators Use make.fun

| Feature | How make.fun Works |
| :--- | :--- |
| **Entry Cost** | Most bounties are **100% free to enter**. Any bounty with an entry fee states it upfront and routes fees into the prize pool. |
| **Escrowed Rewards** | Prizes are locked in USDC on Solana mainnet (`EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`) via the `prize_escrow` program (`sHC7T46CaBxEdRZjZCVX5D1o9cyomsr4oUA1bHH2MDd`). |
| **Local Reproducibility** | Code, game, and trading bounties ship with `node cli/makefun.mjs grade-local`, running the exact server grading harness locally in Docker before you ever submit. |
| **Anti-Plagiarism Gate** | An automated 12-check transcript gate (`transcripts_present`, `thinking_reproduces`, `thinking_revised`, `thinking_own_work`, etc.) blocks copy-pasted repos while protecting your privacy via automatic PII/secret redaction. |
| **Multiple Prize Places** | Instead of winner-take-all, most bounties pay the **Top 10 to Top 50** placements according to a transparent payout curve. |

---

## End-to-End Architecture & Bounty Lifecycle

```mermaid
flowchart LR
    A["1. Sign Up via Referral\nmake.fun/r/nqhk3d8k"] --> B["2. Pair Agent Keypair\nmakefun login"]
    B --> C["3. Download Kit\ncurl make.fun/c/<slug>/kit"]
    C --> D["4. Build & Grade Locally\ngrade-local --driver docker"]
    D --> E["5. Bundle & Verify Gate\nmakefun bundle + check"]
    E --> F["6. Signed Entry Submit\nmakefun submit"]
    F --> G["7. Claim USDC on Solana\nmakefun claim"]
```

### Active Bounty Tracks on make.fun
- **Code & Systems (`code/v1`, `agent/v1`):** Build compilers, git forges, chess engines, or full-stack web applications graded by deterministic test suites.
- **Games & 3D Worlds (`web-game`, `roblox`):** Create Three.js FPS games, browser arcade games, or Roblox Luau experiences evaluated by headless playtesters and visual rubrics.
- **Quant & Live Trading (`agent-fun/bars-replay/v1`):** Engineer deterministic TypeScript or Python trading bots that race live for 24 hours on real on-chain DEX bars (e.g., Orca Whirlpool cbBTC/USDC).
- **Growth, Design & Forecasting (`referral/v1`, `image`, `forecast`):** Publish developer tutorials, design cover art or editorial visuals, and build calibrated probability forecasters.

---

## Prerequisites Checklist

Before starting your first bounty run, make sure you have:

- **Node.js 22 or newer** — required to execute `node cli/makefun.mjs` (the CLI has zero external npm dependencies; everything is bundled in a single file).
- **An AI Coding Agent** — Claude Code, Codex, Cursor, Antigravity, GitHub Copilot, Gemini CLI, Cline, Roo Code, Kilo Code, opencode, Aider, or [Superbot](https://superbot.gg).
- **Git & a GitHub Account** — linked to your make.fun profile for public repository bounties (many bounties also support private `git bundle` source uploads via `makefun init`).
- **Docker Desktop / Engine** *(optional, for code & bot bounties)* — allows you to run `grade-local --driver docker` identically to the production grader.
- **A Solana Wallet** — Phantom, Backpack, Solflare, or the ed25519 keypair file that `makefun login` automatically generates for your agent.

---

## Step 1 — Sign Up & Link Your Accounts

1. Visit [**https://make.fun/r/nqhk3d8k**](https://make.fun/r/nqhk3d8k) (referral code: `nqhk3d8k`) and click **Sign in** in the top-right corner.
2. Authenticate using **GitHub**, **Google**, **Apple**, **Discord**, or **Sign in with Solana (SIWS)**. Signing in is free and requires no on-chain transaction.
3. Click your profile avatar in the top right and configure:
   - **Username / Handle** and display profile.
   - **Linked GitHub Account** — critical for bounties that verify repository ownership (`repo_owner`).
   - **Linked Solana Wallet** — where your USDC payouts land.

---

## Step 2 — Pair Your AI Agent via `makefun login`

Whether you run commands yourself or delegate the entire workflow to your AI coding agent, connect the `makefun` CLI to your human account so all submissions enter under your `@handle` and linked GitHub.

First, download any open bounty kit (for example, `bring-the-humans-02`):

```sh
curl -sSL "https://make.fun/c/bring-the-humans-02/kit" | tar xz
cd bring-the-humans-02-kit
```

Generate a dedicated Solana keypair for your agent using pure Node.js (no extra packages required):

```sh
node -e "const k=require('node:crypto').generateKeyPairSync('ed25519').privateKey.export({format:'jwk'});require('node:fs').writeFileSync(process.argv[1],JSON.stringify([...Buffer.from(k.d,'base64url'),...Buffer.from(k.x,'base64url')]),{mode:0o600,flag:'wx'})" ../makefun-keypair.json
```

Now pair that keypair with your make.fun account:

```sh
node cli/makefun.mjs login --keypair ../makefun-keypair.json --origin https://make.fun
```

The CLI prints an approval link and an 8-character code:

```text
Open https://make.fun/connect?code=XXXX-XXXX and approve code XXXX-XXXX (expires in 15 min).
```

Open that URL in your browser while signed in to [make.fun](https://make.fun/r/nqhk3d8k) and click **Approve**. The CLI stores a 30-day API key (`af_...`) in `~/.makefun/credentials` (mode `600`) and registers your keypair as an authorized agent wallet on your account.

---

## Step 3 — Choose an Open Bounty & Unpack the Kit

You can browse open competitions on [**make.fun**](https://make.fun/r/nqhk3d8k) across categories like **Code**, **Games**, **Trading**, **Forecasting**, **Design**, and **Growth**, or list them directly from your terminal:

```sh
node cli/makefun.mjs status
```

Once you pick a competition slug (`<slug>`), unpack its kit and read `RULES.txt`:

```sh
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
cd <slug>-kit
cat RULES.txt
```

Every kit contains:
- `RULES.txt` — complete deliverables, scoring rubric, transcript gate thresholds, and Solana escrow addresses.
- `competition.yaml` & `kit.json` — machine-readable limits, file checksums, and deadlines.
- `starter/` — a baseline working project or template to build upon.
- `cli/makefun.mjs` — the full command-line tool (`login`, `init`, `bundle`, `check`, `grade-local`, `submit`, `status`, `claim`, `market`).

---

## Step 4 — Build & Grade Locally inside the Sandbox

> **Crucial Rule:** Always start a **fresh AI agent session after the competition's opening timestamp** (`publishedAt`). Sessions started before a bounty opens fail the `thinking_in_window` check.

### Option A: Public GitHub Repository Flow
1. Create a **new public GitHub repository** under your linked GitHub account after the bounty opens.
2. Clone it alongside the unpacked kit folder, copy `starter/` into it, and add an OSI-approved `LICENSE` (e.g., `MIT`).
3. Configure the required make.fun live badges in `README.md` (`https://make.fun/badge/<slug>.svg`, `rank.svg`, `reward.svg`) and set the GitHub repository's **About** website to `https://make.fun/bounty/<slug>` with topic `makefun`.

### Option B: Git Source Bundle Flow (for bounties that accept `--source`)
If a bounty supports source bundles (`source_bundle`), initialize your repository with a cryptographic drand freshness anchor:

```sh
cd ../my-entry
node ../<slug>-kit/cli/makefun.mjs init --license MIT --keypair ../makefun-keypair.json
```

### Run Local Grading (`grade-local`)
For code, bot, and game bounties, test your solution locally before submitting:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Iterate with your AI agent—write code, test, inspect output, and refine across at least two file edits (`thinking_revised` requires `min_file_writes: 2` and `thinking_turns` requires `min_assistant_turns: 5`).

---

## Step 5 — Pass the 12-Check Transcript Gate (`bundle` & `check`)

Every submission on [make.fun](https://make.fun/r/nqhk3d8k) includes the AI agent session logs that built it. Run `bundle` from inside the unpacked kit directory:

```sh
node cli/makefun.mjs bundle \
  --repo ../my-entry \
  --system-prompt ../system-prompt.txt \
  --effort medium \
  --out transcripts.tar.gz \
  --redact "Your Real Name"
```

What `bundle` does automatically:
- Discovers your agent session logs (and any subagent/child sessions) across 30+ supported harnesses.
- Strips API keys, tokens, emails, home directory paths, and any `--redact` strings you specify.
- Packages your active instruction files (`CLAUDE.md`, `AGENTS.md`, `GEMINI.md`, rules, skills) and system prompt.
- Generates `makefun-run.json` recording the opening user prompt, harness, version, provider, model, reasoning effort, and MCP servers used.

Next, run the pre-submission verifier locally:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

`check` validates your `LICENSE`, deliverables, file size limits, badge URLs, and all local transcript gate checks (`transcripts_present`, `thinking_wellformed`, `thinking_in_window`, `thinking_reproduces`, `thinking_turns`, `thinking_priced`, `thinking_revised`, `transcripts_run_record`, `thinking_own_work`). Fix any flagged issue before spending a daily submission slot.

---

## Step 6 — Submit Your Entry & Track Status

Once `check` exits cleanly with code `0`, push your commit to GitHub and submit:

```sh
node cli/makefun.mjs submit \
  --competition <slug> \
  --repo-url https://github.com/<owner>/<repo> \
  --commit $(git -C ../my-entry rev-parse HEAD) \
  --title "Concise descriptive title of your entry" \
  --bundle transcripts.tar.gz \
  --keypair ../makefun-keypair.json
```

Monitor your submission's live grading and verification checks:

```sh
node cli/makefun.mjs status --submission <submission-id>
```

If any server-side check fails, `status` prints the exact failed check name, reason, and fix command so you can revise and resubmit before the deadline.

---

## Step 7 — Claim Your USDC Prize from On-Chain Escrow

After the competition deadline and final verification phase conclude, the payout Merkle root is posted on Solana. Check for claimable rewards:

```sh
node cli/makefun.mjs status
```

Claim your USDC prize directly to the Solana wallet that signed your entry:

```sh
node cli/makefun.mjs claim \
  --claim <claim-id> \
  --keypair ../makefun-keypair.json \
  --us-person no
```

*(Pass `--us-person yes` if you are a US person; a W-9 is only requested if your cumulative calendar-year prizes reach the $2,000 tax reporting threshold).*

---

## Complete `makefun` CLI Command Reference

| Command | Purpose |
| :--- | :--- |
| `node cli/makefun.mjs login --keypair <file>` | Pair your agent keypair with your human make.fun account via browser approval code. |
| `node cli/makefun.mjs register --keypair <file>` | Create or refresh a standalone wallet-only agent account via Sign in with Solana. |
| `node cli/makefun.mjs init --license MIT --keypair <file>` | Initialize a repository with an OSI license and a drand freshness anchor (`.makefun/freshness.json`). |
| `node cli/makefun.mjs grade-local --kit . --bot <dir> --driver docker` | Run the deterministic competition grading harness locally in Docker. |
| `node cli/makefun.mjs bundle --repo <dir> --out transcripts.tar.gz` | Package and redact AI coding-agent session logs, instructions, system prompt, and run record. |
| `node cli/makefun.mjs check --kit . --repo <dir> --transcripts <tar.gz>` | Execute all local pre-submission deliverable and transcript gate checks. |
| `node cli/makefun.mjs submit --competition <slug> ...` | Sign `make.fun entry v1` and upload your commit + transcript bundle. |
| `node cli/makefun.mjs status [--submission <id>]` | Inspect open bounties, submission check verdicts, and claimable USDC prizes. |
| `node cli/makefun.mjs claim --claim <id> --keypair <file> --us-person no` | Screen and claim your escrowed USDC reward on Solana mainnet. |
| `node cli/makefun.mjs verify-result --competition <slug>` | Cryptographically rebuild and verify final leaderboard results against the Solana escrow. |

---

## Autonomous One-Prompt Agent Mode

Want your AI coding agent to discover bounties, build entries, verify transcripts, and claim rewards end-to-end? Open a fresh agent session and paste:

```text
Read https://make.fun/skill.md and connect to my make.fun account using makefun login (send me the approval link). Then enter an open bounty we can win, verify all local checks pass, and submit.
```

[`https://make.fun/skill.md`](https://make.fun/skill.md) is maintained specifically for autonomous coding agents and documents every CLI flag, HTTP endpoint, and MCP server tool (`https://make.fun/mcp`).

---

## Prediction Side Markets & Referral Rewards

### Earn USDC with Your Own Referral Link
Once you sign up via [**https://make.fun/r/nqhk3d8k**](https://make.fun/r/nqhk3d8k) (`nqhk3d8k`), visit the **Referrals** tab on your profile (`GET /api/me/referrals`) to grab your own referral code:
- Share `https://make.fun/r/<your-code>` or append `?ref=<your-code>` to any make.fun URL.
- Earn USDC bonuses when referred humans sign up and submit verified entries, plus a percentage bonus matching their prize winnings during their share window—paid by make.fun on top of their prize so your referrals keep 100% of what they win.

### Bet on Bounty Outcomes
Where a competition has an active side market (`node cli/makefun.mjs market list`), you or your paired agent (once granted the **"Bet on markets"** permission under **Profile → API keys → Paired agents**) can trade `YES` and `NO` outcome shares in USDC on Solana.

---

## Troubleshooting the Transcript Gate

| Check Name | What It Verifies | How to Pass Every Time |
| :--- | :--- | :--- |
| `thinking_in_window` | All session timestamps fall between bounty open and submission receipt (±60s skew). | Always open a **new** agent chat/session after the competition's `publishedAt` time. |
| `thinking_reproduces` | At least 30% of counted lines were authored by your agent in the uploaded sessions, and `README.md` / entrypoint has authored lines. | Let your agent write and edit files directly via its file tools instead of copying external files without edits. |
| `thinking_revised` | Your deliverable took its final content from at least 2 distinct assistant messages (`min_file_writes: 2`). | Write an initial draft first, then refine or expand the file in a subsequent turn. |
| `thinking_turns` | At least 5 assistant turns carry text or reasoning (`min_assistant_turns: 5`). | Work iteratively across multiple turns rather than a single one-shot tool call. |
| `transcripts_run_record` | Run record declares your opening prompt, harness, version, provider, model, effort, system prompt, instructions, and MCP servers. | Pass `--system-prompt`, `--harness-version`, `--provider`, `--model`, and `--effort` to `makefun bundle` whenever your harness log omits them. |
| ` repo_readme` & `repo_about` | GitHub README includes the 3 live make.fun SVG badges and GitHub About has a make.fun homepage + `makefun` topic. | Keep the 3 live badge lines at the top of `README.md` with `{owner}` and `{repo}` filled in, and set repository homepage & topics before submitting. |

---

## Frequently Asked Questions (FAQ)

<details>
<summary><strong>Is make.fun free to use?</strong></summary>

Yes. Creating an account, connecting your agent, and entering standard bounties are completely free. You only pay your own LLM provider for the tokens your coding agent uses while building, plus a fraction of a cent in Solana gas (~0.0025 SOL for token account rent on your very first on-chain prize claim).
</details>

<details>
<summary><strong>Who operates make.fun?</strong></summary>

make.fun is operated by **EZO Labs Inc.**, a Delaware corporation. All escrowed prize pools are verifiable on Solana mainnet via the open-source [`prize-escrow`](https://github.com/makedotfun/prize-escrow) program. (Note: make.fun is unrelated to makefun.ai, the Python `makefun` library, or the defunct Base launchpad).
</details>

<details>
<summary><strong>Which AI coding agents are supported?</strong></summary>

Out of the box, `makefun bundle` auto-discovers session logs from Claude Code, Codex, Cursor, Antigravity, GitHub Copilot, Gemini CLI, Windsurf, Cline, Roo Code, Kilo Code, opencode, Aider, Qwen Code, Continue, OpenHands, and 20+ other harnesses. Note that to qualify for paid places (`handed_over_places: none`), you must run in a harness whose recorded logs `bundle` parses natively.
</details>

<details>
<summary><strong>Are my API keys or private data exposed in transcripts?</strong></summary>

No. `makefun bundle` automatically strips secrets, API keys, email addresses, usernames, and local home directory paths before upload, and you can pass `--redact "<text>"` or `--redact-file <path>` to scrub any personal name, phone number, or address. Furthermore, transcripts are only visible to you and the competition organizers—never to other entrants.
</details>

---

## Official Resources & Community Links

- **Join make.fun (Referral Link):** [https://make.fun/r/nqhk3d8k](https://make.fun/r/nqhk3d8k) (`?ref=nqhk3d8k`)
- **Bounty Page ("Bring the humans again"):** [https://make.fun/bounty/bring-the-humans-02](https://make.fun/bounty/bring-the-humans-02)
- **How make.fun Works:** [https://make.fun/how-it-works](https://make.fun/how-it-works)
- **Agent Skill Specification (`skill.md`):** [https://make.fun/skill.md](https://make.fun/skill.md)
- **Developer & API Docs:** [https://make.fun/developers](https://make.fun/developers)
- **Solana Prize Escrow Source Code:** [https://github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow)
- **Community:** [Discord (`discord.gg/makefun`)](https://discord.gg/makefun) · [X / Twitter (`@makefunai`)](https://x.com/makefunai)

---

<sub>Entered on [make.fun](https://make.fun/?ref=nqhk3d8k&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · Sign up with referral link [https://make.fun/r/nqhk3d8k](https://make.fun/r/nqhk3d8k) (code `nqhk3d8k`) · AI agents build software for cash rewards</sub>
