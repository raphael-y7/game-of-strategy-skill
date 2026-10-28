<h1 align="center">Game of Strategy Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the game-theoretic analysis methods from Avinash Dixit, Susan Skeath and David Reilly's *Games of Strategy* into 14 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- Good news lands and the stock falls anyway — you cannot tell whether "the market is wrong" or both sides are rationally and stably locked in a lose-lose cell, nor which cell the divergence converges to
- A price war, capacity race or brokerage commission war keeps going below cost — you cannot see the prisoner's-dilemma payoff structure, nor judge who blinks first or how long the truce lasts
- Co-operation with a known end date (crowded positions, alliances, lock-up expiries, earn-out maturities) — you cannot compute the threshold return and timing of collapse, only guess that "the end is near"
- Research notes, stock tips, IR communication, buybacks and guidance all sit in front of you — you cannot separate zero-cost talk from genuinely costly, credible signals
- IPO subscriptions, private placements, block trades at a discount, merger arbitrage — you find out the bad news after winning, because there is no adverse-selection check before bidding
- Central-bank forward guidance, controlling-shareholder purchase commitments, policy deterrence — you cannot score the credibility of the commitment, nor tell promises, threats and warnings apart on observability and irreversibility

## What was distilled

14 capability cards, organized in the order "classify first, solve second, information and structure last". 8 of them are promoted to standalone skills and 6 stay inside the routing entry, loaded on demand (per-card destinations are listed in [INDEX.md](./INDEX.md)):

- **Entry and classification**: `source-router` (six-dimension game classification and source routing entry)
- **Core solution methods**: `event-game-tree-rollback` (event game tree rollback), `payoff-table-nash-equilibrium` (payoff tables and Nash equilibrium location), `mixed-strategy-randomization` (mixed strategies and randomized execution), `focal-point-selection` (focal points and key price levels)
- **Information and credibility**: `credibility-signaling-filter` (signal and statement credibility), `strategic-moves-credibility` (strategic moves and credibility scoring)
- **Co-operation and many-player structures**: `cooperation-threshold-repeat-game` (co-operation thresholds: repeated games and the timing of collapse), `collective-action-stampede` (collective action and stampedes: many-player criteria), `strategic-crowding-ess` (strategic crowding and crowded-position collapse: evolutionary criteria)
- **Rules and scenario pricing**: `mechanism-design-incentives` (mechanism design and incentive contracts), `brinkmanship-dual-threshold` (brinkmanship probabilistic-threat dual thresholds), `winner-curse-auction-bidding` (winner's curse and auction bidding), `batna-negotiation` (BATNA negotiation analysis)

## Two packaging modes: single and pack

The same 14 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `game-of-strategy-skill` | **9**: one source router + 8 promoted standalone skills |
| Where the 14 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 8 cards become standalone skills; the other 6 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 8 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 9 directories |

The 8 cards promoted to standalone skills in the pack:

- `source-router` — six-dimension game classification and source routing entry
- `event-game-tree-rollback` — event game tree rollback
- `payoff-table-nash-equilibrium` — payoff tables and Nash equilibrium location
- `cooperation-threshold-repeat-game` — co-operation thresholds
- `credibility-signaling-filter` — signal and statement credibility
- `strategic-moves-credibility` — strategic moves and credibility scoring
- `winner-curse-auction-bidding` — winner's curse and auction bidding
- `strategic-crowding-ess` — strategic crowding and crowded-position collapse

The 6 cards that are not promoted (`mixed-strategy-randomization`, `focal-point-selection`, `collective-action-stampede`, `brinkmanship-dual-threshold`, `batna-negotiation`, `mechanism-design-incentives`) stay in the router's `references/` and are reached through the routing entry — no capability is lost.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "can I trust this news / does this commitment count / how much should I bid / is this style crowded" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: a price war below cost that will not stop

**User question**

"Two brokerages have pushed commission rates below cost. It is obviously lose-lose, so why can't it stop? Should I cut mine too?"

**How the skill reasons**

- Run the six questions in `source-router`: actions are simultaneous (each sets rates at the same moment, blind to the other's move this round) → route to `payoff-table-nash-equilibrium`
- Draw a 2×2 payoff table and declare the convention first: row player's payoff comes first, column player's second, same units and same direction
- Dominance subtraction: if "cut" beats the alternative against both opponent choices, it is a strictly dominant strategy
- Circle best responses cell by cell in both directions; a doubly circled cell is a pure-strategy Nash equilibrium; then check whether that cell is the worse lose-lose cell
- If any weak-dominance elimination with equality was used, re-check every cell — the book explicitly warns that weak-dominance elimination can drop equilibria

**Example final answer**

> Conclusion: this is a prisoner's-dilemma payoff structure. The "lose-lose" outcome is not a market failure; it is the stable landing point of two rational players. The book's standard demo is Congress vs the Fed (Table 4-5): for either interest-rate choice, Congress's best response is deficit (4>3, 2>1); for either fiscal choice, the Fed's best response is high interest (4>3, 2>1); the unique doubly circled equilibrium is (deficit, high interest) = (2,2), while (balance, low interest) = (3,4) is better for both — rational players can stably lock into a suboptimal cell. Mapped onto the commission war: as long as "cut" is your dominant strategy in your own payoff table, refusing to cut unilaterally just donates share, and calling a truce by tacit agreement will not work.
>
> Two things you have to supply. First, the payoff numbers: the book only gives teaching numbers, so share loss, fee rate and unit cost in your table must be estimated by you; if you cannot estimate them, do not fill in invented figures — output the qualitative direction ("cut is / is not a dominant strategy") instead. Second, if you used elimination with equality (say "treat a tie as no-cut"), re-check every cell — the Rowena-Colin game in Table 4-6 is the book's counter-example where weak-dominance elimination drops two equilibria, and stalemate states are exactly what gets eliminated.
>
> One more boundary: payoff tables are net expected returns, so tail losses must be written in. The book's Kreps game shows that a catastrophic cell with tiny probability (the book's magnitude is 1/1009) flips the "expected-value dominant" conclusion, so your ruin line has to enter the table.

### Example 2: a private placement at your own fair value — is winning a gain?

**User question**

"A company is pricing a private placement. If I bid my own fair value of 20, winning means profit, right?"

**How the skill reasons**

- Classify first: common value (one true value for everyone, each bidder holds a noisy estimate) or private value (mostly your own synergies) — only common value triggers the curse correction
- Two mandatory checks: (1) given what I know, would I pay this price? (2) given that nobody else would bid this high, and that is the only reason I can buy it, would I still pay it? The second question must be answered explicitly
- Conditional-expectation recomputation: bid b is accepted → true value lies between 0 and b → conditional mean b/2 → times your operating-improvement factor g; if g×(b/2) < b, i.e. g < 2, any positive bid that wins loses money
- Mechanism mapping: private-placement pricing is close to a first-price mechanism, so bid below your true valuation; a call auction is close to second-price, where bidding your true valuation is dominant
- Summary output: the revised bid ceiling + the reason for the markdown + one sentence on the mechanism-matching strategy

**Example final answer**

> Do not bid 20 yet. "Winning means profit" assumes your valuation is correct, but in a common-value auction winning is itself bad news: if you can win, every rival's estimate is below yours, so your estimate is precisely the most optimistic one. The book's Takic merger example computes this cleanly — bid b being accepted means the target's value is uniform on 0 to b, so the conditional mean is b/2; even if your management improves it by 50%, the conditional value is only 1.5×(b/2) = 0.75b, below b. You win only when winning is not worth it.
>
> Follow the flow: answer question two first — "given nobody would bid 20 and that is why I can buy it, would I still pay it" — then compute with your own improvement factor g whether g×(b/2) exceeds b. Private placement is a first-price mechanism, so the correct move is to bid below true valuation, not to bid your maximum.
>
> This must be stated honestly: the book gives only the direction ("adjust downward") and the criterion g<2, not a closed-form answer for how much to cut — the card's boundary section lists this as a blind spot. The markdown size has to be set by you and written into your plan; do not pretend the book has a ready formula. Also, the ±1 billion uniform error and the 10 bidders in the oil-lease example are teaching settings; in real markets estimation errors are correlated (everyone reads the same research note), so the practical markdown is usually larger than the uniform case. The book's MBA experiment (only 5 of 69 participants kept bidding down) is a reminder: knowing the curse exists is not the same as being able to correct for it.

## How these skills were generated

This skill set was produced by the RIA-TV++ pipeline of **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)**, in six stages:

1. **Whole-book comprehension (Adler analysis)** — Mortimer Adler's analytical reading method, breaking the book down through structure, interpretation, criticism and application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) work at once to pull candidate methodology units out of the text
3. **Triple verification** — every candidate must pass three tests: at least two independent in-book corroborations (cross-domain), the power to answer questions the book never states, and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along six dimensions: R (source quote) / I (restatement in our own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, then generate the capability index and routing table
6. **Trigger and output testing** — design blind trigger tests for every card (including decoys: it must trigger when it should and stay silent when it should not) plus output evaluation scenarios; failing cards go back for rework and are regression-tested afterwards

Several book-specific decisions shaped the result: the book has no direct stock-market cases (the auction and negotiation chapters come closest), so the "game concept → market scenario" mapping is built by the cards themselves with self-declared parameters; the voting-system chapter and the biological mathematics of the evolutionary chapter are used for their ideas only, not computed; and the mechanism-design chapter is a book-level scoping decision, covered only indirectly by the screening half of the credibility card.

## Testing and verification

`evals/` holds the trigger test cases published together with the generation process, one file per skill: 9 files, 55 cases in total.

- **should_trigger, 27 cases**: does it trigger when it should, and does it route to the right capability card
- **should_not_trigger, 18 cases**: decoys — pure technical-indicator calculations, and questions already specific enough to hit one card directly (the entry must not swallow them); silence is the expected behaviour
- **edge_case, 10 cases**: personal decisions versus games, and missing elements where the skill must ask instead of filling in

These files record cases and expected behaviour (`expected_behavior`), not scores. No scoring record is shipped in this repository; you can run the cases yourself.

## Repository structure

```text
game-of-strategy-skill/
├── README.md                      ← the Chinese README
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── INDEX.md                       ← skill map: destinations and dependencies of the 14 cards
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step breakdown, stage 0)
├── verified.md                    ← triple-verification verdicts for 47 candidates (35 passed / 12 rejected)
├── TEST_SUMMARY.md                ← stage 4 pressure-test summary (scope / structural checks / results)
├── CANGJIE_ADAPTATION.md          ← cangjie adaptation notes (text state / distillation goals / evidence rules / limits of use)
├── candidates/                    ← stage 1 raw candidate pool (audit material, not compiled)
│   ├── frameworks.md              ← framework and method candidates (f family)
│   ├── principles.md              ← principle / rule / calculation candidates (p family)
│   ├── cases.md                   ← case candidates (c family)
│   ├── counter_examples.md        ← counter-example and failure-mode candidates (x family)
│   ├── glossary.md                ← term candidates (65 entries)
│   └── supplement_t13_t14.md      ← supplementary extraction: T13 collective action / T14 evolutionary games
├── bundle/                        ← the bundle this repository was compiled from (audit material)
│   ├── verified.yaml              ← the 14 canonical units (slug / intents / destination / promotion gate)
│   ├── cards/                     ← the 14 capability card source files
│   │   ├── celue-00-source-router.md
│   │   ├── celue-01-event-game-tree-rollback.md
│   │   ├── celue-02-payoff-table-nash-equilibrium.md
│   │   ├── celue-03-cooperation-threshold-repeat-game.md
│   │   ├── celue-04-mixed-strategy-randomization.md
│   │   ├── celue-05-credibility-signaling-filter.md
│   │   ├── celue-06-focal-point-selection.md
│   │   ├── celue-07-strategic-moves-credibility.md
│   │   ├── celue-08-collective-action-stampede.md
│   │   ├── celue-09-brinkmanship-dual-threshold.md
│   │   ├── celue-10-winner-curse-auction-bidding.md
│   │   ├── celue-11-batna-negotiation.md
│   │   ├── celue-12-strategic-crowding-ess.md
│   │   └── celue-13-mechanism-design-incentives.md
│   └── book/
│       ├── overview.md            ← whole-book overview
│       └── glossary.md            ← glossary
├── single/                        ← single-entry mode
│   └── game-of-strategy-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest with file hashes
│       ├── test-prompts.json      ← entry trigger cases (7, identical to evals/game-of-strategy-skill.json)
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule cheatsheet
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← the 14 capability cards
│               ├── source-router.md
│               ├── event-game-tree-rollback.md
│               ├── payoff-table-nash-equilibrium.md
│               ├── cooperation-threshold-repeat-game.md
│               ├── mixed-strategy-randomization.md
│               ├── credibility-signaling-filter.md
│               ├── focal-point-selection.md
│               ├── strategic-moves-credibility.md
│               ├── collective-action-stampede.md
│               ├── brinkmanship-dual-threshold.md
│               ├── winner-curse-auction-bidding.md
│               ├── batna-negotiation.md
│               ├── strategic-crowding-ess.md
│               └── mechanism-design-incentives.md
├── pack/                          ← multi-entry mode (compact pack)
│   ├── BUILD_MANIFEST.json        ← build manifest with file hashes
│   ├── capability-destinations.json  ← promotion destinations of the 14 cards
│   ├── game-of-strategy-skill-router/
│   │   ├── SKILL.md               ← source routing entry
│   │   ├── test-prompts.json      ← entry trigger cases (7, identical to evals/game-of-strategy-skill.json)
│   │   └── references/            ← the 14 cards + index, used internally by the router
│   │       ├── overview.md
│   │       ├── capability-index.md
│   │       ├── cheatsheet.md
│   │       ├── glossary.md
│   │       └── capabilities/      ← the 14 capability cards
│   │           ├── source-router.md
│   │           ├── event-game-tree-rollback.md
│   │           ├── payoff-table-nash-equilibrium.md
│   │           ├── cooperation-threshold-repeat-game.md
│   │           ├── mixed-strategy-randomization.md
│   │           ├── credibility-signaling-filter.md
│   │           ├── focal-point-selection.md
│   │           ├── strategic-moves-credibility.md
│   │           ├── collective-action-stampede.md
│   │           ├── brinkmanship-dual-threshold.md
│   │           ├── winner-curse-auction-bidding.md
│   │           ├── batna-negotiation.md
│   │           ├── strategic-crowding-ess.md
│   │           └── mechanism-design-incentives.md
│   ├── source-router/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   ├── event-game-tree-rollback/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   ├── payoff-table-nash-equilibrium/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   ├── cooperation-threshold-repeat-game/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   ├── credibility-signaling-filter/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   ├── strategic-moves-credibility/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   ├── winner-curse-auction-bidding/
│   │   ├── SKILL.md
│   │   └── test-prompts.json      ← 6 trigger cases
│   └── strategic-crowding-ess/
│       ├── SKILL.md
│       └── test-prompts.json      ← 6 trigger cases
└── evals/                         ← trigger test cases (55)
    ├── game-of-strategy-skill.json
    ├── source-router.json
    ├── event-game-tree-rollback.json
    ├── payoff-table-nash-equilibrium.json
    ├── cooperation-threshold-repeat-game.json
    ├── credibility-signaling-filter.json
    ├── strategic-moves-credibility.json
    ├── winner-curse-auction-bidding.json
    └── strategic-crowding-ess.json
```

## How to use

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/game-of-strategy-skill.git
```

### Install single (try this first)

```bash
# macOS / Linux
cp -r game-of-strategy-skill/single/game-of-strategy-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-of-strategy-skill\single\game-of-strategy-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two json files under `pack/` into the skills directory:

```bash
# macOS / Linux
cd game-of-strategy-skill/pack
cp -r game-of-strategy-skill-router \
      source-router \
      event-game-tree-rollback \
      payoff-table-nash-equilibrium \
      cooperation-threshold-repeat-game \
      credibility-signaling-filter \
      strategic-moves-credibility \
      winner-curse-auction-bidding \
      strategic-crowding-ess ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\game-of-strategy-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('game-of-strategy-skill-router','source-router','event-game-tree-rollback','payoff-table-nash-equilibrium','cooperation-threshold-repeat-game','credibility-signaling-filter','strategic-moves-credibility','winner-curse-auction-bidding','strategic-crowding-ess') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to confirm it works

Ask "this company is pricing a private placement, how much should I bid", and see whether the agent goes straight into the two-question check and conditional-expectation recomputation of `winner-curse-auction-bidding` instead of giving you generic valuation talk. With single installed it reads the entry first and follows the routing table into a card; with pack installed the matching capability is hit directly.

## Source

- *Games of Strategy* by Avinash Dixit, Susan Skeath and David Reilly

## Disclaimer

This repository publishes only the distilled skills, indexes and rule cheatsheets. It contains no PDF, EPUB, OCR files, screenshots or full transcript of the book. Quotations inside the capability cards serve only to cite the methodology's origin and keep the material auditable.

All numeric criteria in this repository (co-operation threshold returns, brinkmanship dual thresholds, ESS critical proportions, the conditional-expectation coefficient of the winner's curse, and so on) are inductions from cases and teaching exercises; the book provides no statistical backtesting support. Test them against your own instruments and declare the conventions you use. Nothing in this repository is investment advice.

## License

[MIT](./LICENSE)
