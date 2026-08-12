# Practice Management System Demo

An interactive, self-contained demo of the practice management system I built for a small accounting firm in South Africa. Everything on the page works: you can plan a week, log time, approve or query entries, route tax letters, dig through a live audit log, and lose a few minutes to the offline arcade.

**Live demo: https://thrilla99.github.io/practice-management-system-demo/**

## The important disclaimer

Everything here is fictional. "Meridian & Vos", its staff, its clients and every number on the page were made up for this demo. The production system and its data are private, so this page is a replica of how the system works, not a window into it.

## What the real system does

The production system runs the daily operations of a roughly 20 person accounting firm:

- Week planning against real capacity: 8.5 hours Monday to Thursday, 5.5 on a Friday, public holidays excluded. Over-assignment is visible before it happens.
- Time capture in quarter hours against a client and a work type, with a billable flag that is a human decision rather than an automatic one.
- An approval loop. Every entry passes through a team lead, who either confirms it into the firm's numbers or queries it back with a reason.
- Firm dashboards where each metric has exactly one definition, spelled out on the card, with pace-aware thresholds so early-month numbers read fairly.
- Budget versus actual per client, flagging engagements that are probably mispriced and work being done for clients with no budget at all.
- Triage of letters from SARS (the South African tax authority). Each letter is matched to its client and routed onto one person's list, and letters that are stuck waiting on someone can be flagged busy with a reason instead of silently going stale.
- An append-only audit log covering 111 event types, so every entry, approval, edit and role action can be reconstructed after the fact.
- An offline arcade with a firm-wide leaderboard, because the app is an offline-capable PWA and an error page felt like a waste of the moment.

Roles matter throughout. Staff, team leads and the firm head each see a different slice of the system, and the role switcher in the demo mirrors that: some sections lock unless you sit in the right chair.

## How the demo is built

One HTML file. No frameworks, no build step, no external requests. The styling, the three themes (light, dark and glass), the starfield and the snake game are all inline. Clone the repo and open `index.html` in a browser and the whole thing works, including offline.

## How the production system is built

- Next.js 14 (App Router) with TypeScript
- Supabase Postgres, with row-level security enforcing the role model at the database rather than only in the UI
- 104 hand-numbered SQL migrations
- Fully bilingual, English and Afrikaans, via next-intl
- Offline-capable PWA with a remote kill switch
- Deployed on Vercel, hardened with rate limiting, monitored crons and CI type checks

It has been live in daily use since April 2026, with about 20 daily users and roughly 890 client engagements. The numbers quoted in the demo were checked against the codebase on 12 August 2026.

## Author

Melton Swarts · [LinkedIn](https://www.linkedin.com/in/melton-swarts-a00a39323/)

The production codebase is private. This repo is its public face.
