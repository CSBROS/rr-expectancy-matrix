# R:R Expectancy Matrix

Expectancy per trade for every win rate against every reward-to-risk ratio, including ratios that risk more than they target. Built for discretionary traders who want to know what their numbers imply before the next trade.

**Live:** https://csbros.github.io/tools/rr-matrix/

## What it computes
| Panel | Method |
|---|---|
| Matrix | `E = p·b − (1 − p) − c`, breakeven `p* = (1 + c) / (1 + b)`; views for expectancy, growth-optimal size f*, and P(profit after N trades) |
| Next N trades | Exact binomial: P(net profit), outcome percentiles, wins needed, longest losing streak; simulated drawdown |
| Trade simulator | Seeded random sequence drawn in real time, against the exact 50% / 90% cone of all possible runs |
| Position sizing | Median log-growth `g(f)` for fixed $, ¼ f*, ½ f*, f*, 2× f* |
| Monte Carlo | Every sizing rule on the same random outcomes: median final balance, drawdown, P(bust) |
| Prop challenge | P(pass) against a trailing or static drawdown, with lift over a no-edge baseline at the breakeven win rate |

## Checks
- Exact binomial tails match direct sums to within 1e-11.
- f* matches a brute-force search for the growth peak.
- With no edge, the pass simulation matches the closed form (static 50.0% vs 50%; trailing 37.8% vs ≈36.8%).

## Use
Open `index.html` in a browser. No build step, no data leaves the page.

## Assumptions
Every trade hits target or stop; trades are independent; costs are a fixed R per trade. Break-even stops, partial exits and regime clustering are outside the model, and the page says so.

Educational tool, not financial advice. MIT licensed.
