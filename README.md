# NerdWallet · Money Next Steps — Staff PM prototype

A single-file prototype built for the **NerdWallet Staff Product Manager** role. It covers
the three verticals named in the job description — consumer credit, lending, and investing —
in one personalized, *sequenced* experience.

Open `index.html`. No build step, no dependencies, no backend.

```bash
python3 -m http.server 4794 --directory .
```

## The product bet

NerdWallet is very good at answering "which card should I get?" The question a member
actually has is "what should I do with my money next?", and the answer is usually
cross-vertical and ordered: clear the 24% APR balance *before* opening the rewards card,
build the score *before* applying for the loan.

So the prototype's central move is **sequencing rather than ranking**. Five questions —
credit score band, primary goal, monthly surplus, high-interest debt, time horizon — produce
one ranked product per vertical *and* an order to do them in. Carrying card balances at 20%+
changes the math fast enough that leading with an investing recommendation would be actively
bad advice, so the engine leads with payoff instead.

Each question earns its place, and the copy says why underneath it: the score band is used
for approval odds via a soft check, the goal re-ranks everything below, the surplus decides
whether the plan leads with payoff or investing. A five-question onboarding where a member
cannot see what any answer is for is a five-question drop-off funnel.

## Four surfaces

**My Plan** — the sequenced recommendations, each with a "why this matches you" and a path
to the issuer's application page.

**Market Intel** — pick a vertical and the positioning map, feature-coverage grid and
white-space bets all update together. The competitive read is per-vertical because
NerdWallet's position genuinely differs across the three.

**Metrics & Roadmap** — a North Star (activated members: share completing at least one
recommended action within 30 days), an activation funnel with draggable levers that
recompute the outcome, experiments in flight, and a Now/Next/Later roadmap. The levers are
there so the reader can find out for themselves which step in the funnel actually moves the
North Star, rather than being told.

**PM lens** — a toggle that reveals, on every module, the personalization logic behind it,
the metric it moves, and the live experiment testing it. This is the part built for the
interview specifically: it lets the same artifact be a product demo and a PM artifact
without turning the product into an annotated diagram.

## What it is not

A working recommendation engine. The products, market data and funnel numbers are authored.
What is on display is the product judgment — sequencing over ranking, why each onboarding
question survives, which metric is the North Star and what moves it.

## Related

[nerdwallet-money-platform](https://github.com/chloe4ai/nerdwallet-money-platform) is the
same product built for real: Next.js + Express + SQLite, a server-side personalization
engine, ~32k synthetic events aggregated into a live funnel, and a what-if simulator that
recomputes against the database. Read this one for the argument; run that one to see it
hold up under a real schema.
