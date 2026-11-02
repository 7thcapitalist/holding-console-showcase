# Holding Console (showcase)

Public showcase for a private project. The source code is not published here.

Holding Console is a small, independent dashboard for watching a holding of "business factories", starting with Frontstep (a website-building pipeline). Its main design rule: show what is actually known, and show unknown as unknown.

## The problem

Operational dashboards tend to turn missing data into zeros and estimates into revenue. For a holding that mixes real cash, estimated costs and unreconciled records, that is how you fool yourself. I wanted a console that refuses to.

## How it works

- A **public page** shows an aggregate observation approved for publication. It exposes only numeric fields and timestamps from an allowlist. It does not refresh itself: a new observation means preparing, reviewing and publishing a new build.
- A **private operator page** queries the configured sources when opened or when the operator asks to refresh. It is behind basic credentials; without them the server refuses to serve it.
- A **source adapter** reads HTTPS sources in a versioned JSON contract, filters fields, drops test records, deduplicates ids within a source and keeps unknown values as `null`.
- An **ideas space** with a simple NPV simulator: explicit initial investment, monthly cash flow, monthly rate and horizon. It is a what-if on stated assumptions, not a valuation, and it does not approve budgets or launch factories.

## Design notes

- `null` means unknown. Zero means the source verified there were no events.
- Revenue counts as confirmed only with proven payment and reconciled ledger entries. Thirty-day profit also needs complete cost coverage. Otherwise it stays unknown.
- Estimated variable costs and registered fixed monthly costs are shown separately and are not labeled as paid expenses.
- A send record is not proof of delivery. A "preview ready" status is not proof of a unique preview.
- Money is integer cents with an ISO currency. Dates are ISO 8601 with a time zone.
- The public snapshot is produced by a script that validates the input envelope and writes only allowed fields. The raw private file never enters the repository.

## Architecture

A dependency-free Node server with a handful of modules (source adapter, aggregate projection, public summary, routes), static assets embedded at build time, deployed as a serverless function behind the host's protection. Tests cover routes, source mapping and the public summary.

## Stack

Node.js 20+ (no external dependencies), plain JavaScript front end, `node --test`, Vercel.

## Status

Early prototype. The deployed version shows one embedded aggregate observation from 1 October 2026. No live source is connected. Revenue, effective costs and profit are shown as unknown because they were not reconciled.

## What is shown and what is kept private

Only this README is public. The repository is private because it is business-internal tooling, and its design depends on never mixing private source data into anything public.
