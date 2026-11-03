# Holding Console (showcase)

Public showcase for a private project. The source code is not published here.

Holding Console is a small dashboard for watching a holding of "business factories", starting with Frontstep (a website-building pipeline). Its main rule: show what is actually known, and show unknown as unknown.

## The problem

Dashboards tend to turn missing data into zeros and estimates into revenue. For a holding that mixes real cash, estimated costs and unreconciled records, that is how you fool yourself. I wanted a console that refuses to.

## How it works

- A **public page** shows a summary that was reviewed and approved for publication. It only exposes a short list of allowed numbers and their timestamps.
- A **private operator page** shows the detailed view and is behind a login.
- Data comes from each business in an agreed format. Test records are dropped, duplicates are removed, and anything missing stays unknown.
- An **ideas space** with a simple what-if calculator for a new venture: investment, monthly cash flow, rate and horizon. It is a what-if on stated assumptions, not a valuation, and it does not approve budgets.

## Principles

- Unknown is not zero. Zero means the source verified there were no events.
- Revenue counts as confirmed only with proven payment and reconciled records. Profit also needs complete cost coverage. Otherwise it stays unknown.
- Estimated costs and registered fixed costs are shown separately and are not labeled as paid expenses.
- A message sent is not proof of delivery. A "preview ready" status is not proof that a preview exists.
- Private data never enters anything public.

## Status

Early prototype. It currently shows one observation from 1 October 2026 and no live source is connected. Revenue, costs and profit are shown as unknown because they were not reconciled.

## What is shown and what is kept private

Only this README is public. The source is private because it is internal tooling for a live business.
