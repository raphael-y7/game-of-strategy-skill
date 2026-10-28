<h1 align="center">Games of Strategy Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the game-analysis methods from Avinash Dixit, Susan Skeath and David Reiley's *Games of Strategy (4th Edition)* into 14 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- Good news lands and the stock drops: you cannot tell whether the market is wrong, or both sides are each acting rationally and stably locked into a losing cell — nor which cell the deviation converges to
- Price wars, capacity races and brokerage commission cuts keep going below cost: you cannot see that this is a prisoner's-dilemma payoff structure, nor judge who blinks first and how long the tacit deal lasts
- Crowded trades, alliances, lock-up expiries and earn-out deadlines: you cannot state the critical rate of return or the break-up timing for cooperation, only guess that "it feels close to the end"
- Research notes, stock tips, IR communication, buybacks and guidance: you cannot tell which sentence is costless cheap talk and which is a genuinely costly, credible signal
- IPO subscriptions, private-placement pricing, block-trade discounts and merger arbitrage: you find out it was bad news only after you won — there is no adverse-selection check before you bid
- Central-bank forward guidance, major-shareholder purchase commitments and policy deterrents: you cannot score the credibility of the commitment, nor separate commitment, threat and promise on observability and irreversibility

## What was distilled

14 capability cards, organized in the order "classify first, solve second, handle information and structure last":

- **Entry and classification**: `source-router` (six-dimension game classification and source routing entry)
- **Foundational solutions**: `event-game-tree-rollback` (event game tree and rollback), `payoff-table-nash-equilibrium` (payoff tables and Nash equilibrium location), `mixed-strategy-randomization` (mixed strategies and randomized execution), `focal-point-selection` (focal points and key price levels)
- **Information and credibility**: `credibility-signaling-filter` (signal and talk credibility), `strategic-moves-credibility` (strategic moves and credibility scoring)
- **Cooperation and multi-player structure**: `cooperation-threshold-repeat-game` (cooperation thresholds in repeated games and break-up timing), `collective-action-stampede` (collective action and stampedes, multi-player criteria), `strategic-crowding-ess` (strategic crowding and crowded-trade collapse, evolutionary criteria)
- **Rules and scenario pricing**: `mechanism-design-incentives` (mechanism design and incentive contracts), `brinkmanship-dual-threshold` (brinkmanship probabilistic threats and dual thresholds), `winner-curse-auction-bidding` (winner's curse and auction bidding), `batna-negotiation` (BATNA negotiation analysis)

## Two packaging modes: single and pack

The same 14 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `game-of-strategy-skill` | **9**: one source router + 8 promoted standalone skills |
| Where the 14 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 8 cards become standalone skills; the other 6 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 8 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 9 directories |

The 8 entries promoted to standalone skills in the pack (7 capability cards plus 1 routing entry):

- `source-router` — six-dimension classification and source routing
- `event-game-tree-rollback` — event game tree and rollback
- `payoff-table-nash-equilibrium` — payoff tables and Nash equilibrium location
- `cooperation-threshold-repeat-game` — cooperation thresholds
- `credibility-signaling-filter` — signal and talk credibility
- `strategic-moves-credibility` — strategic moves and credibility
- `winner-curse-auction-bidding` — winner's curse and auction bidding
- `strategic-crowding-ess` — strategic crowding and crowded-trade collapse

The 6 cards that were not promoted (`mixed-strategy-randomization`, `focal-point-selection`, `collective-action-stampede`, `brinkmanship-dual-threshold`, `batna-negotiation`, `mechanism-design-incentives`) stay in the router's `references/` and are reached through the routing entry, so no capability is lost.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "can I trust this / does this commitment count / how much should I bid / is this style crowded" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: a price war below cost — why does it not stop?

**User question**

"Two brokerages have pushed commission rates below cost. It is obviously lose-lose, so why can't it stop? Should I cut my rates too?"

**How the skill reasons**

- First `source-router`'s six questions: the timing is simultaneous (each sets its rate at the same time and cannot see the rival's current move) → route to `payoff-table-nash-equilibrium`
- Draw the 2×2 payoff table, declaring the convention first: row player's payoff first, column player's second, with unit and direction on the same scale
- Dominance subtraction: if "cut" is better against both rival choices, it is a strictly dominant strategy
- Optimal-response analysis circles the best response cell by cell in both directions; a double-circled cell is a pure-strategy Nash equilibrium; then check whether that equilibrium cell is worse for both than "neither cuts"
- If any weak dominance with ties was used along the way, re-check every cell — the book explicitly warns that weak-dominance elimination can drop equilibria

**Sample answer**

> Verdict: this is a prisoner's-dilemma payoff structure. "Lose-lose" is not market failure; it is the stable landing point of two rational players. The book's standard demonstration is Congress vs the Fed (Table 4-5): given either interest rate, Congress's best response is a deficit (4>3, 2>1); given either fiscal policy, the Fed's best response is high rates (4>3, 2>1); the only double-circled cell is (deficit, high rates) = (2,2), while (balanced, low rates) = (3,4) is better for both — rational players can stably lock into a second-best cell. Applied to the commission war: as long as "cut" is dominant in your payoff table, refusing to cut unilaterally just gives away share, and calling for a truce does nothing.
>
> Two things you must supply. First, the payoffs: the book only gives teaching numbers, so share loss, fee rates and unit costs in your table are yours to estimate; if you cannot estimate them, output the qualitative direction ("cut is / is not dominant") instead of inventing numbers. Second, if you used an elimination with ties (say "treat a tie as not cutting for now"), re-check every cell — Table 4-6 (the Rowena-Colin game) is the book's example of weak-dominance elimination dropping two equilibria, and a sideways standoff is exactly the tie state most easily eliminated away.
>
> One more boundary: payoff tables are net expected payoffs, so tail losses belong in them. The book's Kreps game shows that a disaster cell with a tiny probability (1/1009 in the book's numbers) flips the "higher expected value" conclusion, so the blow-up line has to be in the table.

### Example 2: private-placement pricing — is bidding my fair value a sure win?

**User question**

"A company is running a private-placement book. I plan to bid the 20 yuan I calculated as fair value — if I get it, I make money, right?"

**How the skill reasons**

- Classify first: is the value common (one true value for everyone, each bidder holding a noisy estimate) or private (mostly own-use synergy)? Only common value triggers the curse correction
- The two mandatory questions: (1) given what I know, would I buy at this price? (2) knowing that nobody else would bid this high and that is the only reason I can buy it, would I still? The second must be answered explicitly
- Conditional-expectation check: if bid b is accepted, the true value lies between 0 and b, so the conditional mean is b/2; multiply by your operating improvement factor g; if g×(b/2) < b, i.e. g < 2, any positive bid that wins loses money
- Mechanism mapping: a placement book resembles a first-price mechanism, so bid below your true valuation; a call auction resembles a second-price mechanism, where bidding your true value is dominant
- Output: the corrected bid ceiling, the reason for the markdown, and the one-line mechanism strategy

**Sample answer**

> Do not bid 20 yet. "If I win I make money" assumes your valuation is right, but in a common-value auction winning is itself bad news: you can only win because every rival's estimate is below yours, so yours is the most optimistic one. The book's Takic merger example is clean — if bid b is accepted, the target's value is uniform between 0 and b, so the conditional mean is b/2; even with a 50% operating improvement, the conditional value is only 1.5×(b/2) = 0.75b, less than b. In other words, you win only when winning is not worth it.
>
> Follow the flow: answer question two first — "knowing nobody else would bid 20 and that is why I can buy it, do I still want it?" — then compute g×(b/2) against b with your own improvement factor. A placement book is a first-price mechanism, so the right move is to bid below your true valuation, not to bid it in full.
>
> One honest caveat: the book gives the direction of the markdown and the g < 2 criterion, but no closed-form for how much to mark down — the card's own boundary section lists this as a blind spot. The size of the markdown is yours to define and write into the plan; do not pretend the book has a ready formula. Also, the oil-lease example's ±100 million uniform error and 10 bidders are teaching assumptions; in real markets estimation errors are correlated (everyone reads the same research), so the actual markdown is usually larger than the uniform case suggests. The book's MBA experiment — only 5 of 69 participants kept shading their bids — is a reminder that knowing the curse exists is not the same as executing the correction.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — write trigger blind tests (including decoy questions: fire when they should, stay silent when they should not) and output evaluation scenarios for every card; failing cards go back for rework and are re-verified afterwards

A few book-specific decisions also shaped the result: the original has no direct stock-market case (the auction and negotiation chapters come closest), so the "game concept → market scenario" mapping and its parameters were built inside the cards; the voting chapter and the biological mathematics of the evolutionary chapter were kept as ideas only, without computation; and the mechanism-design chapter was a book-level scoping decision, covered indirectly through the screening half of the credibility card.

## Repository layout

```text
game-of-strategy-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← triple-verification conclusions for 43 canonical units
├── single/                        ← single-entry build
│   └── game-of-strategy-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 14 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json        ← build manifest and file hashes
│   ├── capability-destinations.json  ← promotion destinations for the 14 cards
│   ├── game-of-strategy-skill/    ← source router entry
│   │   ├── SKILL.md
│   │   └── references/            ← 14 cards + indexes, called by the router
│   ├── source-router/
│   │   └── SKILL.md
│   ├── event-game-tree-rollback/
│   │   └── SKILL.md
│   ├── payoff-table-nash-equilibrium/
│   │   └── SKILL.md
│   ├── cooperation-threshold-repeat-game/
│   │   └── SKILL.md
│   ├── credibility-signaling-filter/
│   │   └── SKILL.md
│   ├── strategic-moves-credibility/
│   │   └── SKILL.md
│   ├── winner-curse-auction-bidding/
│   │   └── SKILL.md
│   └── strategic-crowding-ess/
│       └── SKILL.md
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/game-of-strategy-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r game-of-strategy-skill/single/game-of-strategy-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-of-strategy-skill\single\game-of-strategy-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

```bash
# macOS / Linux
cd game-of-strategy-skill/pack
cp -r game-of-strategy-skill \
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
@('game-of-strategy-skill','source-router','event-game-tree-rollback','payoff-table-nash-equilibrium','cooperation-threshold-repeat-game','credibility-signaling-filter','strategic-moves-credibility','winner-curse-auction-bidding','strategic-crowding-ess') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "This company is running a private-placement book — how much should I bid?" If the agent goes straight into `winner-curse-auction-bidding`'s two-question check and conditional-expectation calculation instead of giving generic valuation commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *Games of Strategy (4th Edition)* by Avinash Dixit, Susan Skeath and David Reiley; Renmin University of China Press, April 2020 (Economics Science Translation Series; original edition W. W. Norton, 2015)
- Distilled from the whole book, producing 14 capability cards
- The original cases are heavily US-centred (Congress vs the Fed, US-Japan trade, the Cuban missile crisis, the baseball strike) and include no direct stock-market case; this skill pack prioritizes A-share scenarios, and the "game concept → market scenario" mapping and its parameters were built inside the cards
- The book's formulas (cooperation thresholds, the dual-threshold window, the ESS threshold family, the winner's-curse conditional expectation) come with teaching numbers only; in practice you must plug in your own payoffs, continuation probabilities and estimation errors

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (cooperation thresholds, brinkmanship dual thresholds, ESS critical proportions, the winner's-curse conditional-expectation factor, etc.) are case- and teaching-example-based rules without statistical backtesting; test them on your own instruments and declare the convention you use. Nothing in this repository is investment advice.

## License

[MIT](https://opensource.org/licenses/MIT)
