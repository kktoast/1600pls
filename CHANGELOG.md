# freeSAT — Changelog

All notable changes to this site are logged here so progress is never lost between sessions.
Repo: https://github.com/kktoast/1600pls

---

## v2.0.0 — Home page, score tracking, recommendations, decluttered UI
- Restructured navigation to three clean top-level tabs: **Home**, **Math**, **Reading & Writing**
- New **Home** tab:
  - Score history chart (custom SVG line/area chart) — log real or practice SAT scores (Math + R&W) over time, stored in the browser via localStorage
  - Lifetime stats row: latest score, questions answered, lifetime accuracy, questions live
  - **Recommended Practice** panel — ranks skills by estimated score impact using a weighted heuristic against your actual answer history (also persisted via localStorage), with a one-click "Practice this skill" jump into Math filtered to that exact skill
- Visual decluttering: removed the graph-paper background texture in favor of a subtle single gradient, merged the sidebar's 4 panels down to 2 (Session + Filters), tightened spacing throughout
- Answer attempts are now logged persistently (domain, skill, correct/incorrect, timestamp) to power lifetime accuracy + recommendations, separate from the in-session score ring

## v1.1.0 — Site rebrand + Math domain structure
- Renamed the site to **freeSAT**, new wordmark and tagline
- Added top-level tabs: **Math** / **Reading & Writing** (R&W marked "Under Construction")
- Added Math domain tabs: **Algebra** (live, 30 questions), **Advanced Math**, **Problem-Solving & Data Analysis**, **Geometry & Trigonometry**
- Empty domains show a "Coming Soon" state listing their real official SAT sub-skills instead of a blank page
- Sidebar filters (skill + difficulty) now scope to the active domain

## v1.0.0 — Initial Algebra practice app
- Built from a 30-question SAT Algebra question bank (systems of equations, linear equations in one/two variables, linear functions, linear inequalities)
- Scantron-style multiple choice + grid-in answer entry
- KaTeX-rendered math, inline tables/graphs recreated from source PDF
- Skill + difficulty filters, session score ring, end-of-set accuracy summary by skill

---

### For future chats
If you're picking this up in a new conversation: this file + the git commit history at the repo link above is the full source of truth for what's been built. Point a new Claude session at the repo (or paste a scoped access token) and it can clone it to see exactly where things stand before making changes.

## v2.1.0 — Rebrand to 1600pls
- Renamed the site from freeSAT to **1600pls**, matching the repo/URL
- Updated wordmark, page title, tagline, and footer accordingly
