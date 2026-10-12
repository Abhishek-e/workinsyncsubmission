# WorkInSync — Hybrid Facility Planning Dashboard

A submission for the **Technical Account Manager / Implementation Intern** role at WorkInSync (by MoveInSync), Bangalore.

The brief was simple to read and hard to answer well: *2,000 people, 3 offices in 3 countries, 3 days a week in office — how many seats do we actually need?*

This repo is my attempt at that answer. It's a working dashboard, not a slide deck.

---

## The Problem, Restated

A facility manager staring at 2,000 desks on a spreadsheet has two bad options:

1. **Keep all 2,000 desks** → pay for real estate that sits empty 60% of the week.
2. **Cut too aggressively** → employees show up on Tuesday, can't find a seat, and the whole "return to office" story collapses.

The right answer lives somewhere in the middle. Finding that middle is what this project is about.

---

## How I Approached It

I'll be upfront — I didn't invent a new formula. The math here is grounded in four management ideas that have been quietly shaping operations for decades:

### 1. Lean Thinking — Eliminate *Muda* (Waste)

Toyota's production system calls waste "muda" — anything that consumes resources without creating value. In a hybrid office, an unused desk is muda. Pure, unapologetic muda.

At 3 days a week, a dedicated desk sits idle **60% of the time**. That's the number that should make any facilities lead uncomfortable. Lean says: don't eliminate the desk, eliminate the *idleness*. That's exactly what desk-sharing does.

### 2. Theory of Constraints — Plan for the Bottleneck

Eliyahu Goldratt's insight was that a system is only as fast as its slowest step. For hybrid offices, the bottleneck isn't the weekly average — **it's Tuesday.**

Peak days (Tue–Thu) hit 85–95% attendance. Friday sits at 15–25%. If you size for the average, Tuesday becomes a disaster. If you size for Tuesday, you over-provision the rest of the week. The whole exercise is about finding the right buffer above the constraint.

### 3. The Balanced Scorecard — KPIs That Actually Reflect Value

Kaplan & Norton argued that financial metrics alone give you a warped view of an organization. The same applies here. "Cost per seat" is one lens. But employee experience, booking compliance, and space utilization are equally important. That's why the dashboard tracks **four KPI families**: Space, Cost, Experience, Operations.

### 4. OKRs — Target and Stretch

The three scenarios (Target, Best, Worst) mirror the OKR philosophy: you need a *committed* goal and an *aspirational* one. Target (1,400) is the committed goal. Best Case (1,200) is the stretch. Worst Case (1,500) is the retreat position if adoption lags.

---

## The Core Calculation

Nothing fancy. Just honest arithmetic with a defensible range:

| Scenario | Ratio | Seats | Meaning |
|---|---|---|---|
| **Best Case** | 0.60 | **1,200** | Aggressive sharing. Works only with high adoption. |
| **Target** | 0.70 | **1,400** | Balanced. 10–15% buffer above peak. Recommended. |
| **Worst Case** | 0.75 | **1,500** | Conservative. Cost savings shrink. "Zombie desks" appear. |

**Recommended: 1,400 seats across the 3 offices.**

Why 1,400? Because it sits above the peak-day 90th percentile demand and still leaves a real buffer. It respects the constraint (Tuesday) without punishing Friday.

---

## What the Dashboard Actually Does

I built this as a single-file HTML dashboard so it's portable and easy to demo.

### Pages

- **Dashboard** — KPIs, occupancy trend, cost comparison, employee experience chart. All driven by real numbers.
- **Scenarios** — Side-by-side breakdown of Target / Best / Worst with tradeoffs.
- **Trends** — Explains the bimodal pattern and why average is a lie.
- **Resources** — Every source used, with clickable DOIs and URLs.
- **Action Center** — Real facilities tasks, each with a CTA button.

### Interactions

- **Scenario toggling** — Click Target / Best / Worst and every chart, KPI, and metric redraws with a 1.4-second animation.
- **Hover tooltips** — Every KPI card explains its own logic. No guessing what "Health: 14%" means.
- **Toast notifications** — Clicking an action button gives feedback. Small thing, but it makes the dashboard feel alive.

### Design Choices

I went with a **light grey-blue theme** because facility managers stare at screens all day. Dark themes look cool in screenshots but tire the eyes in practice. The glassmorphic panels give depth without relying on heavy shadows — a design pattern borrowed from Apple's Human Interface Guidelines.

Every element animates in — nothing pops. Charts ease in over 1.4 seconds. Cards bounce in staggered. This isn't decoration; it's *progressive disclosure*. The eye is guided to the most important metric first.

---

## KPI Framework — The Real Answer to "How Do You Measure Success?"

This is where most candidates go wrong. They list metrics without explaining *why* they matter. Here's the reasoning behind each one:

### Space Utilization
- **Peak-Day Desk Utilization (85–90%)** — The single most important number. If it's too low, you're wasting money. Too high, you're frustrating people.
- **Booking-to-Usage Ratio (>85%)** — Measures no-shows. If people book and don't show, the system is broken.
- **Average Weekly Utilization (55–65%)** — Context, not a target. A useful number to sanity-check against peak.

### Financial
- **Cost per Used Seat** — Not "cost per assigned seat." Only count desks people actually sit at.
- **Real Estate Spend as % of Revenue** — The only number your CFO cares about.

### Employee Experience
- **Desk Availability Rate (>95%)** — Did people find a desk when they needed one?
- **Satisfaction Score (>4.0/5)** — Survey-based. Simple, blunt, honest.

### Operations
- **Meeting Room Utilization (50–70%)** — Meeting rooms are usually the most under-utilized asset.
- **No-Show Rate (<15%)** — Booking without showing up is the hybrid equivalent of a wasted conference room.

---

## References

I leaned on four industry reports and three academic papers:

- **JLL Global Occupancy Planning Benchmark 2025** — Peak utilization 80% vs. 54% average
- **CBRE Americas Office Occupier Sentiment Survey 2025** — 73% report peak-day capacity issues
- **Kastle Systems Back-to-Work Barometer 2025** — Tuesday peaks at 95.5% in A+ buildings
- **Building and Environment (2025)** — Data-driven framework for seat occupancy prediction
- **Springer (2025/2026)** — Hot-desking allocation algorithm using matching theory
- **SAGE (2025)** — MILP model for optimizing hybrid work schedules
- **Density.io, YAROOMS, Skedda, Deskbird** — Practitioner sources on desk ratios

All links and DOIs are live in the **Resources** page of the dashboard.

---

## Assumptions and Honest Caveats

I'd rather flag these now than have someone find them later:

1. **The 0.6–0.75 ratio range is an industry benchmark, not a universal law.** It works for typical hybrid setups. A company with a strong in-office culture might need 0.85. A fully remote-first company could go to 0.4.
2. **Country-specific patterns are not modeled.** The 3 offices have different commute cultures, holidays, and norms. The dashboard recommends the *total*, but each office should run its own peak-day analysis.
3. **Adoption risk is real.** The Best Case (1,200) only works if employees actually comply with hoteling. If they don't, you slide toward the Worst Case.
4. **The KPI targets are directional.** They're based on benchmarks from the sources above — not on WorkInSync's own internal data (which I don't have access to).

---

## How to Run It

1. Clone the repo.
2. Open `index.html` in any modern browser.
3. That's it. No build step, no dependencies to install.

The dashboard uses Tailwind (CDN) and Chart.js (CDN), so an internet connection is needed on first load.

---

## File Structure
