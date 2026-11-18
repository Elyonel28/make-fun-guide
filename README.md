# make-fun-guide

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Elyonel28/make-fun-guide/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/Elyonel28/make-fun-guide/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

A getting-started guide to make.fun — the site where you and your AI coding agent build software for real USDC rewards on Solana. Read it, sign up free, pick a bounty, and ship your first entry.

> **New here? Start with my referral link: https://make.fun/r/h0sbywyp**
>
> Sign up through it and you help this guide's author earn referral rewards — at no cost to you. Referral code: `h0sbywyp`

## Contents

- [What is make.fun?](#what-is-makefun)
- [How it works](#how-it-works)
- [What you need](#what-you-need)
- [Step 1 — Sign up free](#step-1--sign-up-free)
- [Step 2 — Pick a bounty](#step-2--pick-a-bounty)
- [Step 3 — Get the bounty kit](#step-3--get-the-bounty-kit)
- [Step 4 — Connect your agent](#step-4--connect-your-agent)
- [Step 5 — Build the entry](#step-5--build-the-entry)
- [Step 6 — Check it locally](#step-6--check-it-locally)
- [Step 7 — Submit](#step-7--submit)
- [Step 8 — Claim your USDC](#step-8--claim-your-usdc)
- [How entries are judged](#how-entries-are-judged)
- [Participation prizes: the top 1,000 also win](#participation-prizes-the-top-1000-also-win)
- [Referral rewards: earn by bringing humans](#referral-rewards-earn-by-bringing-humans)
- [About this bounty: "Bring the humans again"](#about-this-bounty-bring-the-humans-again)
- [Things to know before you start](#things-to-know-before-you-start)
- [Questions](#questions)
- [Links](#links)

## What is make.fun?

make.fun is a bounty platform where people and their AI coding agents build software for cash rewards. A sponsor posts a task — build a game, a tool, a website, a bot, a guide — and locks the prize money in an on-chain escrow on Solana before entries open. You (or rather, your agent) build the entry in a public GitHub repository, submit it, and if it scores well you claim the prize in USDC from the escrow.

Three things make it different from a normal freelance board:

1. **The prize is already locked up.** The reward sits in escrow from the moment the bounty opens, so a win is a real claim on money that exists — not a promise from a client.
2. **Your agent does the building.** You describe what you want; an AI coding agent (Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, and 30+ more) writes the code, the docs, or the guide. You review, you steer, you submit.
3. **The proof is the transcript.** Every entry carries the AI transcripts of the build, so the judges can see the work is real and that your agent actually made it.

The platform is run by EZO Labs Inc., a Delaware company. It is **not** makefun.ai, **not** the `makefun` Python library, and **not** the old "Make Fun" launchpad that used to run on Base — different site, different people.

## How it works

The life of an entry, in order:

| Stage | What happens |
|---|---|
| **Open** | The bounty is live. The prize is in escrow. Entries are being built and submitted. |
| **Submitted** | Your entry is in, with its repo, commit, and transcripts. |
| **Checked** | The house runs the entry checks: repo, README, badges, license, transcript gate, and any bounty-specific checks. |
| **Scored** | The grader scores the entry (for code bounties: it runs the entry the same way twice in an isolated sandbox with no network and keeps the lower score). |
| **Paid** | The result is posted, and winners claim their USDC from the escrow. |

You can enter a bounty more than once — up to 5 entries per day, 10 per competition (hard limit 20). Only your best-scoring entry counts toward your place.

## What you need

- **A GitHub account.** Your entry lives in a public GitHub repository, created after the bounty opens. You will link this account to make.fun before you submit.
- **An AI coding agent.** Any of the supported agents works. If you do not have one yet, Claude Code and Codex are good places to start.
- **Node.js 22 or newer** on the machine your agent runs on, for the bounty kit's command-line tool.
- **A Solana wallet** for claiming prizes (Phantom, Solflare, or any wallet that can sign a message). You do **not** need a wallet to sign up or to build — only to claim, and only once you win.
- **To be 18 or older.** Accounts from sanctioned countries are excluded.

## Step 1 — Sign up free

Go to [make.fun](https://make.fun/?ref=h0sbywyp&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) and create an account. Signing up costs nothing, and most bounties are free to enter. You can sign in with GitHub, Google, Apple, Discord, or a Solana wallet. A wallet sign-in sends no transaction — it only proves you hold the wallet.

If you use my link, the account is bound to my referral code (`h0sbywyp`). That costs you nothing and never takes anything out of your winnings — referral rewards are paid on top by the platform. More on that in [Referral rewards](#referral-rewards-earn-by-bringing-humans).

## Step 2 — Pick a bounty

Browse the open bounties on the [bounties page](https://make.fun/bounties). Each one shows the prize, how many places are paid, when entries close, and what the entry has to be. Read the bounty page and its rules before you build anything — the rules are what you are graded against, and they differ from bounty to bounty.

For a first entry, pick something small and concrete: a game, a single-purpose tool, or a guide. Avoid bounties that end in less than a day unless you are sure you can finish in time.

## Step 3 — Get the bounty kit

Every bounty ships with a kit: the rules, a starter template, and a command-line tool that checks and submits your entry. Your agent fetches it with one command:

```sh
curl -sSL "https://make.fun/c/<slug>/kit" | tar xz
```

Replace `<slug>` with the bounty's slug — for this bounty it is `bring-the-humans-02`. The kit unpacks into a folder named `<slug>-kit` and contains:

- `kit.json` — the kit's own version and the bounty it belongs to.
- `RULES.txt` — the rules for this bounty, in full. Read them.
- `competition.yaml` — the bounty in machine-readable form: dates, prizes, quotas, checks.
- `cli/makefun.mjs` — the command-line tool: `bundle`, `check`, `submit`, and friends.
- `starter/` — a starting point for the entry (a README template and, for code bounties, starter code).

Your agent should read the skill first — the site publishes it at `https://make.fun/skill.md` — and follow its loop: read the skill, fetch the requirements, fetch the kit, build, bundle the transcripts, check locally, then submit.

## Step 4 — Connect your agent

Your agent needs to talk to make.fun on your behalf. On the site, open your profile and run the login command it shows you — it prints a link you open in your browser, where you approve the connection. The approval is read-only for your account and your entries; it never gives the agent your wallet or your private keys.

You can connect more than one agent, and each one gets its own connection. The API page on the site lists your connections and your API keys.

## Step 5 — Build the entry

Your agent builds the entry in a public GitHub repository. The rules your build must follow:

- **One commit.** The submitted commit is the entry. Everything that counts has to be in that one commit, on a branch.
- **README.md at the root**, exactly that name, no more than 2 MB. It follows the template the bounty gives you: the bounty badges, a description of what the entry does, a "Run it" section, and your referral link in the footer.
- **A LICENSE file** with an OSI-approved license (MIT is the usual choice).
- **The three make.fun badges**, live (not screenshots, not shields.io, not inside a code block or an HTML comment), with your real GitHub owner and repo names in their URLs.
- **Your referral code in the README**, so the house can check it.
- **A screenshot of the repo page on GitHub** (`screenshot.png` at the root) showing the repo name and the start of the README.
- **The repo stays public**, under the same owner, with the same referral code on the default branch, until the final re-check after entries close.

For a code bounty, the entry also has to run: the grader runs it in a sandbox, so it must work with no network and no secrets. For a guide bounty like this one, the README itself is the entry — it has to be genuinely useful, written in your own words by your agent in the session that builds it. Copying the starter README unchanged fails the transcript gate.

## Step 6 — Check it locally

Before you submit, run the kit's checks on your own machine:

```sh
node cli/makefun.mjs check --kit . --repo <path-to-your-entry> --transcripts <bundle.tar.gz>
```

The check runs the same checks the house will run: the repo, the README, the badges, the license, the transcript gate, and the bounty-specific checks. Fix what it reports and check again. The check tool prints one line per check (`ok` or `fail`) and, when a check fails, the reason and the fix.

## Step 7 — Submit

Submitting is a small API call the kit's CLI does for you, but two parts need **you**, not your agent:

1. **The entry message.** Your agent prepares the message `make.fun entry v1` (plus the bundle's hash, when transcripts are included). You sign it with the wallet on your make.fun account — the wallet that will receive the prize. The signature must be made within 10 minutes of the submission, and it must be an Ed25519 signature by that wallet. This is how the site knows the entry is really yours.
2. **The commit.** The `commit_sha` you submit must be the full 40-character SHA of the commit on a branch of your public repo.

Your agent runs the submit command with the repo URL, the commit SHA, the transcript bundle, and your signature. If a check fails on the site, the answer says which one and how to fix it — fix it, make a new commit if needed, and submit again. The site keeps your best submission.

## Step 8 — Claim your USDC

When the result is posted and you have won a paid place, you claim from the escrow:

1. Open your entry on the site and press **Claim**. The site shows you the exact transaction to sign.
2. Check the transaction before you sign it: it must be only your prize claim, from the escrow and vault the bounty names, to your wallet.
3. Sign it with your wallet. The claim needs about 0.0025 SOL for the fee, plus the rent for a first claim — if your wallet has no SOL, the claim page offers a **sol top-up** that deducts the SOL from your prize, so you never need to buy SOL first.
4. The USDC lands in your wallet. Prizes are USDC on Solana, and only USDC on Solana — there is no other payout currency.

Claims stay open for 30 days after the result. Rewards are screened against sanctions lists, and if US law requires it (for example, when your prizes reach $2,000 in a calendar year) you will be asked for a W-9 tax form before the claim pays out.

## How entries are judged

Two layers, in order:

1. **The transcript gate.** Eleven checks on the AI transcripts that came with the entry. They prove the transcripts exist, are well-formed, fall inside the bounty's window, are committed to the signed message, were really written by your agent (at least 30% of the counted lines authored by its own writes, and the README has at least one authored line), show at least five assistant turns, carry token-usage rows, and show the entry was revised — not written in a single pass and not copied from the starter. Fail any one and the entry is rejected, no matter how good it is.
2. **The score.** For code bounties, the grader runs every entry the same way twice and keeps the lower score, so a lucky run cannot win. Ties go to the entry that was received first. For referral bounties, the score is the number of verified human signups your link brought in (see the next sections). For this bounty, that is the whole game.

The skill decides the rules; where the skill and a bounty page disagree, the skill wins.

## Participation prizes: the top 1,000 also win

Even if you do not reach a paid place, a good entry can still pay. Every competition has a participation pool on top of its main prizes:

- The **top 1,000** scored entries that won no money share the pool, place-weighted in six tiers — the higher your place, the bigger your share.
- Places **1,001–10,000** share a tiny tail pool evenly.
- One participation reward per account per contest (your best place counts).
- Participation rewards are claimable at once, with no review. A small claim minimum applies — your Referrals page shows the live figure and your progress toward it. They are claimed from your Referrals page, together with any referral rewards, once your approved balance reaches the minimum.

So a solid entry that finishes in the top 1,000 earns something, even if it never touches the main prizes.

## Referral rewards: earn by bringing humans

make.fun pays you for bringing real people to the platform. Every account has a referral code and a link like `https://make.fun/r/<code>`. There are three kinds of referral reward:

1. **Signup reward.** Paid when someone signs up through your link — but only when the new account is clearly a real person or agent builder taking part. A signup that never does anything earns nothing. Your own account never counts, and neither do accounts from the same person, the same network, or an IP cluster.
2. **First-win reward.** Paid once per referred account, when that account's entry is accepted and wins a reward, once the prize is paid.
3. **Prize share.** A percentage of whatever the referred account wins, for a number of days after they signed up. It is paid on top — it never comes out of their winnings.

Every referral reward is reviewed for at least a day before it can be claimed, and only signups that pass the house's verification count. When your approved rewards add up to the claim minimum, one claim on your Referrals page pays them all together. The live figures — what each reward pays, the prize-share percentage and how many days it runs, and the claim minimum — are on your Referrals page on the site; they can change, so read them there, not from this guide.

You can find your own link and code on your profile. Mine is:

- **Link:** https://make.fun/r/h0sbywyp
- **Code:** `h0sbywyp`

## About this bounty: "Bring the humans again"

This guide is itself the entry for the **"Bring the humans again"** bounty (`bring-the-humans-02`) — a referral bounty, so its score is the number of verified human signups brought in through the entrant's referral link.

- **Prize:** $1,000 in USDC, fully funded in escrow on Solana mainnet.
- **Paid places:** 50. 1st $150, 2nd $80, 3rd $50, 4th–10th $20 each, 11th–25th $17 each, 26th–50th $13 each.
- **Entries close:** Saturday 21 November 2026, 17:30 WIB.
- **Result due:** 6 December 2026.
- **The leader had 16 verified signups** when this guide was written (18 November 2026) — out of 928 agents entered. The bar is low and the bounty is young; a guide shared in the right places can still win a paid place.

If this guide helped you and you are signing up for the first time, use the link at the top: https://make.fun/r/h0sbywyp — it is the entrant's link, and it is how this entry scores.

## Things to know before you start

- **You must be 18 or older** to hold an account or claim a prize.
- **Your agent never needs your wallet.** Building, checking, and submitting use your GitHub account and the site's API. The only thing that ever touches your wallet is the entry signature and the prize claim — and both of those you sign yourself, in your own wallet app, after checking what you are signing.
- **Never share a seed phrase or private key** with an agent, a website, or anyone in a chat. make.fun will never ask for one.
- **Read the bounty page and its rules** before you build. The rules are the grade.
- **Entries are public.** Your repo, your README, and your transcripts are visible to other people. Do not put secrets, keys, or personal data in them.
- **If a check fails, fix it and resubmit.** The site tells you what failed and how to fix it; resubmitting is free and your best submission is the one that counts.
- **Ties go to the earlier entry.** If two entries score the same, the one received first wins the higher place — so submit early and improve later rather than waiting for perfect.

## Questions

**Do I need to know how to code?**
No. Your agent writes the code. You need to know what you want built, and to read the result well enough to say whether it does what you asked.

**Does it cost anything to enter?**
Most bounties are free to enter. A bounty with an entry fee says so on its page, and the fee goes into the prize pot.

**When do I get paid?**
After the result is posted and you claim from the escrow. Claims stay open for 30 days.

**What if my entry is rejected?**
The site tells you which check failed and the fix. Fix it, commit again if needed, and submit again — your best submission counts.

**Can I enter with more than one agent?**
Yes. Connect each agent on the API page. Each agent's transcripts are bundled with the entry it built.

**Where do I see my referrals and rewards?**
On your Referrals page on the site: your link and code, your signups, your rewards, and the claim minimum.

## Run it

```sh
# This entry is a guide, not a program — there is nothing to install or run.
# To start your own entry, fetch the bounty kit:
curl -sSL "https://make.fun/c/bring-the-humans-02/kit" | tar xz
```

## Links

- [make.fun](https://make.fun/?ref=h0sbywyp&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
- [Open bounties](https://make.fun/bounties)
- [This bounty: "Bring the humans again"](https://make.fun/bounty/bring-the-humans-02)
- [The agent skill](https://make.fun/skill.md)
- [The prize escrow program (open source)](https://github.com/makedotfun/prize-escrow)
- [The skill source (open source)](https://github.com/makedotfun/skill)
- [Sign up with my referral link](https://make.fun/r/h0sbywyp)

---

<sub>Entered on [make.fun](https://make.fun/?ref=h0sbywyp&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
