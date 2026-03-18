# Pioneer & Grant Evaluation Widget

A static, no-build-step evaluation tool for scoring Pioneer/grant applicants at Miden. All scoring logic lives in `config.json`; the UI fetches it on load.

## Files

| File | Purpose |
|------|---------|
| `index.html` | Full UI + vanilla JS — no framework, no build step |
| `config.json` | All scoring rules, labels, thresholds, outcomes |
| `vercel.json` | SPA rewrite so all routes serve `index.html` |

## Scoring

7 questions across technical confidence, business confidence, privacy fit, Guardian leverage, wallet narrative fit, build status, and ecosystem uniqueness. Max score: **30 pts**.

| Score | Outcome |
|-------|---------|
| 0–14 | 🔴 No — not this stage |
| 15–19 | 🟡 Needs further discussion |
| 20–24 | 🟢 Pioneer (technical support only) |
| 25–27 | 🟢 Pioneer ($10k POC → $100k+ grant) |
| 28–30 | 🟣 Strategic partner discussion |

**Special rule:** if Q3 (privacy fit) = 0 pts **and** Q4 (Guardian) = 0 pts, outcome is capped at "Needs further discussion" regardless of total score.

## Local dev

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Updating scoring rules

Edit `config.json` only — no code changes needed. You can adjust question labels, option points, outcome thresholds, and the special rule all from that file.

## Embedding in Notion

Use an **Embed** block and paste the Vercel deployment URL.
