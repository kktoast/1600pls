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

## v2.2.0 — Advanced Math questions live, wordmark update
- Added 30 real Advanced Math questions (Equivalent expressions, Nonlinear equations/systems, Nonlinear functions) — pulled and hand-verified from source PDF since equations render as images in text extraction
- Advanced Math domain is no longer "Coming Soon" — fully playable with filters, scoring, and recommendations like Algebra
- Wordmark: both "1600" and "pls" now bold; "pls" keeps the gold underline accent

## v2.3.0 — Predicted score & improvement graphs
- Every completed practice set now logs a session record (accuracy) and a predicted-score snapshot to the browser's local storage
- New **Predicted Math Score** chart on Home — a 200–800 estimate recalculated after each completed set, weighted by domain accuracy (clearly labeled as a rough estimate, not an official College Board prediction)
- New **Accuracy Improvement** chart on Home — plots accuracy per completed practice set over time, so trend lines build up the more you practice
- Refactored the chart renderer into a shared `buildLineChart()` helper used by all three Home charts (Score History, Predicted Score, Improvement) for consistency

## v2.3.1 — Chart layout fit
- Predicted Score and Improvement charts now sit in their own equal-width two-column grid (previously inherited a lopsided 1.35:1 ratio meant for the score history + recommendations layout)
- Removed the forced min-width/horizontal-scroll on charts; they now scale cleanly to their panel width at any screen size
- Slightly more compact chart proportions with larger internal label text so numbers stay legible when panels are narrower

## v2.4.0 — Practice Hub: full tests + guided skill selection
- Math tab now opens on a **Practice Hub** instead of dropping straight into questions
- **Full Practice Test** — generates a randomized, mixed-domain set every time, sampled proportionally to each domain's real SAT weighting (the exact same weights used for the Predicted Score chart on Home). Choose a length (10/20/30 questions) and see a live preview of the domain breakdown before starting.
- **Practice by Skill** — pick a domain and specific skills/difficulty first, see exactly how many questions match, then start — no more landing straight on Question 1 with no context.
- Fixed a scoring bug: answer logging now correctly attributes each question to its actual source domain (important once tests mix domains) instead of assuming the currently active domain tab.
- Session and prediction logging now labels full-test completions distinctly from single-skill sets.
- Summary screen (after finishing any set) now offers "Back to hub" alongside retry/shuffle options.

## v2.5.0 — Animations and micro-interactions
- Buttons, chips, domain tabs, skill rows, and choice bubbles now have tactile "weight" — a quick scale-down on click/press across the whole site
- Checking an answer now gives real feedback: correct answers pop with a soft green glow, incorrect ones give a quick shake — plays once right when you check, not on every revisit
- The rationale panel fades in smoothly each time it appears
- Primary nav (Home / Math / Reading & Writing) now slides directionally — moving right slides content in from the right, moving left (going back) slides in from the left
- Practice Hub → session transitions slide forward; "Back to hub" slides back — matches the natural forward/backward feel of the flow
- Next/Previous question navigation slides the question card in the corresponding direction
- Respects `prefers-reduced-motion` — all animations collapse to near-instant for anyone with that OS/browser setting enabled
