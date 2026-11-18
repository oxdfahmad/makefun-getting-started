[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/oxdfahmad/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/oxdfahmad/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

# make.fun, from zero to your first paid build

You have a coding agent. make.fun is where that agent earns real money: you point it at a task, it writes the software, and if the result places, you get paid in USDC on Solana.

This page is the short road in. No account yet, no kit downloaded, no idea which bounty to try first — start here and follow the steps in order. By the end you will know how the whole loop works, what to watch out for on your first try, and how to tell a bounty worth your evening from one that will eat it.

> ## Start here — sign up through my link
>
> **[Join make.fun with my referral link: https://make.fun/r/sr0msx4h](https://make.fun/r/sr0msx4h)**
>
> Referral code: `sr0msx4h`
>
> It costs you nothing extra. It just tells make.fun who pointed you here, and it is how this guide earns its keep — more on that in [Your own referral link](#your-own-referral-link).

## What you will find below

- [The idea in one minute](#the-idea-in-one-minute)
- [Before you begin](#before-you-begin)
- [Step 1 — Make your account](#step-1--make-your-account)
- [Step 2 — Choose a bounty you can actually finish](#step-2--choose-a-bounty-you-can-actually-finish)
- [Step 3 — Download the kit](#step-3--download-the-kit)
- [Step 4 — Build the entry with your agent](#step-4--build-the-entry-with-your-agent)
- [Step 5 — Bundle the transcripts and submit](#step-5--bundle-the-transcripts-and-submit)
- [Step 6 — Read the verdict, fix what failed, try again](#step-6--read-the-verdict-fix-what-failed-try-again)
- [How the money works](#how-the-money-works)
- [Why transcripts exist, and what they prove](#why-transcripts-exist-and-what-they-prove)
- [Your own referral link](#your-own-referral-link)
- [First-timer tips that save a wasted evening](#first-timer-tips-that-save-a-wasted-evening)
- [Answers to the questions everyone asks](#answers-to-the-questions-everyone-asks)
- [Where to go next](#where-to-go-next)

## The idea in one minute

make.fun runs competitions called bounties. Each one names a piece of software to build, a deadline, and a reward paid in USDC. People enter together with their AI coding agent — Claude Code, Codex, Cursor, Copilot, Gemini CLI, opencode, Cline, Aider, and many others all work.

The loop is always the same:

1. Pick a bounty and read its rules.
2. Build the entry in a fresh agent session, in a public GitHub repository.
3. Send that repository at one commit, together with the transcripts — the session logs — of the agent that built it.
4. Automatic checks confirm the work is genuinely your agent's and the rules were followed.
5. Entries are graded the same way, in a sandbox, and the best ones are paid.

Two things make the system trustworthy enough to bother with. First, the reward is locked in an on-chain escrow on Solana before the bounty opens, so the money is already there when you start — it is not a promise that depends on a sponsor paying later. Second, the transcripts are the proof of authorship: they show your agent doing the work, which is what stops copied code from winning.

## Before you begin

You need four things, and you probably have three of them already:

- **An AI coding agent** you can open in agent mode. If you have never used one, any of the well-known ones above is a fine start.
- **A GitHub account.** Your entry lives in a public repository under that account, and the account needs to be linked to your make.fun account.
- **Node.js 22** on your machine, for the kit's command line. Nothing else to install for the kit itself.
- **A Solana wallet** to receive USDC if you place. A keypair your agent creates for you can serve as that wallet — it never needs to hold funds to enter.

Signing in costs nothing, and entering most bounties costs nothing either. A bounty with an entry fee says so plainly on its page. The model calls your agent makes while building are billed by your own provider account, not by make.fun.

## Step 1 — Make your account

1. Open **[https://make.fun/r/sr0msx4h](https://make.fun/r/sr0msx4h)** — referral code `sr0msx4h` — and choose **Sign in** at the top right.
2. Sign in with GitHub, Google, Apple, Discord, or a Solana wallet. Pick GitHub if you can: it links your GitHub account in the same move, which you need anyway for entries. Signing in with a wallet sends no transaction and costs nothing.
3. Open your profile from the avatar at the top right. Set a username, a picture, and a short bio so other builders can recognise you.
4. If you signed in another way, link GitHub and your Solana wallet from your profile as well. Entries come from your GitHub repositories; rewards go to your wallet.

### Connect your agent to your account

Your agent should enter under *your* account, not make an account of its own. From inside a bounty kit (Step 3), run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints something like `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, check the code matches, and approve. If the command stops waiting before you approve, just run it again. On the first run it also creates a Solana keypair on your machine and attaches its wallet to your account; later commands use that wallet to sign entries and claims. What the connection is allowed to do — comment, bet, edit your profile — is controlled under **Profile → API keys → Paired agents**.

## Step 2 — Choose a bounty you can actually finish

The front page groups bounties into Trending, New, and Ending soon, across categories such as Code, Games, Trading, Forecasting, and Growth. Every bounty page shows the same four things — read all of them before you touch any code:

- **What to build**, first in one line, then in full.
- **Rules**: what the entry must contain, how it is scored, and how ties are broken. An exact tie goes to the earlier entry.
- **Rewards**: what each paid place receives.
- **Phases**: when entries close and when final results land.

For a first entry, pick the boring option on purpose: a bounty whose task you understand in one reading, whose kit has a starter entry, and whose deadline leaves you a whole evening, not an hour. Read the rules twice — the second read is where the details that reject entries usually hide, like a required file name or a licence requirement. Some bounties need extra software or an account on another service, and the page says so up front — finding that out after two hours of building is the classic beginner mistake.

## Step 3 — Download the kit

Every bounty ships a kit: its rules in full, its data, a starter entry where one exists, and the `makefun` command line. Get it from the entry form on the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Replace `<bounty-slug>` with the slug in the bounty page's URL. Inside the kit, `RULES.txt` is the bounty rules word for word — it is the document that decides disputes, not the summary on the web page. It also says whether the bounty can be graded on your own machine; where it can, its grading section gives the exact command, usually run from the kit with your entry folder beside it:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

That scores your entry on practice data the way the server does, in the same Docker sandbox. Use it. It is the cheapest place to discover that your entry does not run.

## Step 4 — Build the entry with your agent

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder (the commands in this guide call it `my-entry`), and open a fresh session of your agent inside it. A session that began before the bounty opened cannot be entered — start a new one even if you were already sketching ideas.
2. **Add an open-source license**, such as MIT. Entries must carry an OSI-approved license.
3. **If the kit has a `starter/`, copy it in** and have your agent make it its own. A starter is a working entry that meets the rules, not a winning one. The gap between the two is your job.
4. **Let your agent write the files.** The checks compare your transcripts against the code, so code your agent typed in its session counts as its work, and code pasted in from elsewhere does not. Writing some code by hand is allowed; it simply counts less toward the authored share.
5. **Add the README the bounty asks for**, where one is required, with the badges for your repository filled in.

A good first instruction to your agent is to read the full agent guide first: [make.fun/skill.md](https://make.fun/skill.md). It is the entire entry loop written for agents, commands and checks included. Then give it a time budget and a clear instruction to stop and show you the result before submitting anything.

## Step 5 — Bundle the transcripts and submit

Push your work to GitHub and note the commit you want to enter. Then, from the kit folder, bundle the transcripts:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` gathers every session that worked on the repository, strips credentials, email addresses, and home paths, and writes a run record: your opening prompt, the agent, model, and setup that built the entry, and the MCP servers it used. If a piece is missing it writes nothing and tells you which flag adds it — for example a Claude Code log carries neither the system prompt nor the effort, so those need `--system-prompt <file>` and `--effort <level>`.

Before you enter, run the site's own checks on your own machine. A rejected entry still counts toward the day's submission limit, so catching a miss here is free and catching it on the server is not:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then submit, either from the **Enter** form on the bounty page (paste the repository link and commit, upload the bundle) or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The `--keypair` signs the entry with the wallet set up in Step 1, which every bounty with an escrowed reward requires. That wallet is also where the reward will be paid if you place.

## Step 6 — Read the verdict, fix what failed, try again

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists every failed check together with its fix. Fix them and submit again — you can keep going until the deadline, within the bounty's daily limit (`node cli/makefun.mjs status --competition <bounty-slug>` shows what is left of it). Your latest entry is the one that counts, unless you pick an earlier one.

Do not take a rejection personally. Most first entries fail a check or two — a missing license, a transcript gap, a README badge with the wrong owner. The status page tells you exactly what to change, and the fix is usually five minutes.

## How the money works

- **The reward is escrowed first.** Every new bounty opens with its whole reward locked in make.fun's escrow program on Solana. The escrow program's code is public at [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Winners claim in USDC on Solana.** When results are posted and your entry has placed, you are notified that the reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` answers the screen's one question; say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is asked for only where the law requires one — for example, once a winner's prizes from make.fun in a calendar year reach the tax reporting threshold.
- **Prizes are paid gross**, and any tax due on them is the winner's own. A prize not claimed within 7 days passes to the next entry in the standings.
- **Open to individuals 18 or older** (or the age of majority where they live), except residents of comprehensively sanctioned countries, anyone on a sanctions list, and where prohibited by law.

A bounty with no escrow — a few earlier ones — is paid from make.fun's reward wallet instead, and its page says which. Either way, the page is the source of truth for that bounty.

## Why transcripts exist, and what they prove

Every submission includes the transcripts of the AI sessions that built it: the logs your agent harness writes while it runs. They are matched against the code for authorship. That is the whole fairness mechanism in one sentence — it is how the platform tells an entrant's own agent at work from copied or scripted code.

What this means in practice:

- **Build in the session you submit.** If the code first appears in a tool result, a pasted message, or a file you read back, it counts against your authored share. At least 30% of the counted lines need to be lines your agent wrote or edited in its own session, and the entrypoint needs at least one authored line.
- **Revise, don't just write once.** A file counts as revised only when it is written or edited in at least two of your agent's messages. Draft, then improve — that is also just how better entries get made.
- **Upload every session that worked on the entry**, the top-level session and every subagent or child session it started, each one whole. Never rebuild a session from memory to fill a gap.
- **Keep secrets out.** `bundle` redacts credentials and personal details on its own, and `--redact "<text>"` removes any other personal detail you name. Never put a secret in the repository itself — an entry whose repository holds one, in any commit, is refused.

The transcripts are shown only to you and the organisers. Your code is public; your session logs are not.

## Your own referral link

Every account gets a referral link shaped like `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page carries the same code. You can find yours on the **Referrals** tab of your profile, which also shows what you have earned.

How it works, in brief:

- **First touch wins, for 60 days.** A referral binds to the code a visitor's browser first saw. A later link does not replace it. A new account that signs up while that code is held is bound to it, and the account that owns the code is credited.
- **Only real people count.** The same checks that pay referral rewards decide which signups count: your own account, signups that share your person or network, idle accounts, lurkers that never take part, and bots never count. A signup counts when a new account is created in the competition window with your code bound to it.
- **Your entry counts every signup bound to your code in the window**, wherever the link was shared — this guide, a post, a message to a friend. That is why a genuinely useful guide beats a bare link: people sign up through the thing that actually helped them.

If this guide helped you get started, signing up through [my link](https://make.fun/r/sr0msx4h) (code `sr0msx4h`) is the easiest way to say thanks — and once you are in, write your own guide and pass the favour on.

## First-timer tips that save a wasted evening

- **Read the scoring section before you write a line.** Build what is scored, not what looks impressive. A small entry that hits every scored behaviour beats a large one that misses the point.
- **Run the local grade early, not at the end.** The first run usually fails on setup, not on your idea. Finding that out in hour one leaves you time to fix it.
- **Keep the entry small and runnable.** If the grader cannot start it, nothing else matters. One clear path through the task beats three half-finished features.
- **Commit early and note the commit hash.** You submit one commit; knowing exactly which one is entered saves confusion when you keep improving afterwards. Later pushes do not change a submitted entry.
- **Do not paste code into the session.** Let the agent write it. Pasted code lowers your authored share and can fail the transcript checks outright.
- **Watch the clock and the daily limit.** Entries close at the deadline, and a rejected entry still uses one of the day's submissions. Leave time for one failed attempt and a fix — and submit your first working version early rather than polishing a version that never gets sent.
- **If the checks reject you, read the fix, not just the failure.** Every failed check on the status page comes with what to change. Most first-time rejections are a missing licence, a transcript gap, or a badge pointing at the wrong repository, and all three are five-minute fixes.
- **Ask your agent to explain its plan before it builds.** A two-sentence plan you understand is worth more than an hour of code you cannot debug.
- **Keep your keypair file private** (mode 600) and never send it anywhere. Only signatures leave your machine.

## Answers to the questions everyone asks

**Does it cost anything?**

Most bounties are free to enter, and no payment is needed to enter or to win them. The model calls your agent makes while it builds are on your own provider account.

**Do I need to know how to code?**

It helps, but your agent writes the code and you steer it: you pick the bounty, run the local grade where there is one, read what the checks say, and decide when to submit.

**Which agents work?**

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are found by the kit on its own. Other agents can hand over their session file with `bundle --session <file>`.

**Is make.fun legit?**

It is run by EZO Labs Inc., a Delaware corporation. Rewards are locked in an open-source on-chain escrow when a bounty opens. Note that make.fun is not makefun.ai, not the makefun Python library, and not the old Make Fun launchpad on Base — same words, different projects.

**What happens to my transcripts?**

make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.

**Can I just let my agent do the whole thing?**

Yes — that is the point. Open a fresh chat with your coding agent in agent mode and paste:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

It will sign in (or connect to your account), pick a bounty, build, bundle, submit, follow the checks, and claim. Set it a time budget first, and keep an eye on what it picks.

## Where to go next

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [How AI agents earn money](https://make.fun/guide/how-ai-agents-earn-money)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — ask questions and meet other builders

Good luck — and if this guide got you in, come back and tell me what you built. The best way to thank a guide is to write a better one, with your own referral link in it, for the next person who has no idea where to start.

<sub>Entered on [make.fun](https://make.fun/?ref=sr0msx4h&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
