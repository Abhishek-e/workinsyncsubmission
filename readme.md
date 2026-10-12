# WorkInSync Hybrid Seat Planning

A small, browser-based planning dashboard for a straightforward workplace question: **how many desks should support 2,000 employees who come to the office three days a week across three locations?**

The short answer is **1,400 seats as a starting plan**. It reduces the dedicated-seat baseline by 600 desks while keeping 200 seats above the simple weekday-average attendance. The recommendation is a planning scenario, not a final lease or office-by-office allocation.

## The decision in numbers

| Planning case | Seats | Seats per employee | Fewer than 2,000 dedicated desks | What it means |
| --- | ---: | ---: | ---: | --- |
| Lean | 1,200 | 0.60 | 800 (40%) | Matches the average weekday attendance; leaves no average-day cushion. Peak-day demand must be managed closely. |
| **Recommended** | **1,400** | **0.70** | **600 (30%)** | Adds 200 seats above the average weekday attendance and gives a practical starting point for local validation. |
| Conservative | 1,500 | 0.75 | 500 (25%) | Keeps more room for demand variation, with a smaller reduction in desk count. |

### Where the 1,200-person average comes from

The brief assumes 2,000 employees each attend **3 days out of a 5-day work week**:

```text
2,000 employees × 3 office days = 6,000 employee-days per week
6,000 employee-days ÷ 5 weekdays = 1,200 people per weekday on average
1,400 recommended seats − 1,200 average attendees = 200 seats above the average
2,000 dedicated desks − 1,400 recommended seats = 600 fewer desks (30%)
```

An average is not a peak forecast. If attendance clusters on Tuesday through Thursday, the busiest day can be materially higher than 1,200. The 1,400-seat case is therefore a **recommendation to validate**, not a claim that every office can safely operate at that number today. Before reducing space, compare several weeks of bookings and badge entries by location and weekday, account for teams that need to be onsite together, and preserve accessible and specialist workspaces.

## What the dashboard shows

- **Dashboard:** the 2,000-person planning brief, the 1,400-seat recommendation, and the difference from a dedicated-seat setup.
- **Scenario selector:** compare 1,200, 1,400, and 1,500 seats. The occupancy charts show illustrative weekday patterns to make the trade-offs visible; they are not company attendance data.
- **Seat-footprint chart:** compares the selected scenario with 2,000 dedicated desks. It does not estimate rent or claim a specific cash saving.
- **Experience guardrails:** suggested service targets for desk availability, booking use, and satisfaction. They are targets to discuss, not measured results.
- **Trends and resources:** explain why a weekly average is not enough to set a seat count and provide links for further reading.
- **Action center:** add one of four suggested workstreams or create a custom action, then mark it complete or reopen it. The action list is saved in this browser with `localStorage`; it does not sync to a task system or another device.

## Assumptions and limits

This is a portfolio-level exercise built from the stated inputs: **2,000 employees, 3 offices, and 3 in-office days per employee each week**. It does not include employee counts by location, actual attendance history, floor plans, lease costs, room mix, team schedules, accessibility requirements, or WorkInSync customer data.

For that reason, the dashboard’s weekday curves and experience targets are illustrative. They help compare options, but should not be presented as observations. The 0.60–0.75 seat-to-employee range is a scenario range rather than a universal industry rule. A final recommendation should use each office’s observed peak demand and an agreed service buffer.

The plotted weekday curves are a worked example that distributes roughly **6,000 employee-days** across the week. The 1,200-seat case assumes attendance can be perfectly spread, so all seats are occupied each weekday on average; the 1,400- and 1,500-seat cases show different illustrative peaks. The displayed percentages are rounded. Replace these curves with actual local data before using them to make capacity decisions.

One useful reference point is JLL’s *Global Occupancy Planning Benchmark Report 2025*, based on 99 organizations representing 745 million square feet. It reports global actual office utilization of 54% and a 79% utilization target. Those figures describe the report’s respondents; they are context for measuring utilization, not inputs to the 1,400-seat calculation. [Read the report (PDF)](https://www.jll.com/content/dam/legacy/jll-com/documents/pdf/research/global/25-insights-global-occupancy-planning-benchmark-report-2025.pdf).

CBRE’s 2025 Americas survey also illustrates the difference between average and peak conditions: 73% of respondents placed peak-day utilization in the 61–100% range, compared with 34% for average utilization. This is U.S.-focused survey context, not a direct estimate for the three offices in this exercise. [Read the survey](https://www.cbre.com/insights/reports/2025-americas-office-occupier-sentiment-survey).

## Run locally

No build step or package installation is needed. Open `index.html` in a modern browser. The dashboard loads Tailwind CSS and Chart.js from CDNs, so an internet connection is required for styling and charts.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Single-page dashboard, scenario data, charts, and interactions |
| `readme.md` | Recommendation, arithmetic, assumptions, and run instructions |
