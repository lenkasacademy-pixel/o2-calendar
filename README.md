# O2 Health Hub — content calendar

Two pages for **@o2health_hub** (Instagram).

| Page | What it is | Live |
|---|---|---|
| `index.html` | Planning doc — September to October 2026 | https://lenkasacademy-pixel.github.io/o2-calendar/ |
| `september.html` | Performance report — 1–10 September 2026, client-facing | https://lenkasacademy-pixel.github.io/o2-calendar/september.html |

Both are self-contained single files. No build step.

## `index.html` — the plan

Data lives in three arrays near the bottom:

- `POSTED` — what is already on the grid. Read from the **public** profile on
  11 Sep 2026. The logged-out view caps at 12 posts and exposes only date and
  media type, so there are no captions or view counts here.
- `PLAN` — `[date, pillar, format, title, brief, cta]`, 20 posts to 9 Oct.
- `PILLARS` — the five content themes and their colours.

`TODAY` drives the highlighted cell; move it on each refresh.

### Why the plan is ordered this way

Weighted by what the ads actually produce (see `lenkasacademy-pixel/o2-reports`):
autism leads every week at ₹113 per 20-second call against ₹332 for endoscopy.
Diabetes and weight get a weekly slot because they sit in the bio but have never
been advertised. Cadence is 5/week Mon–Fri, reel-led — at 290 followers, reach
has to come from non-followers.

## `september.html` — the performance report

1–10 September 2026, organic Instagram only. 11 feed posts (7 images incl. one
carousel, 4 Reels) and 11 stories. 4,371 organic views; 16,656 including ads.
The 7 Sep endoscopy Reel alone did 2,343 views — 59% of the organic total.

Data lives in `POSTS` and `STORIES` near the bottom of the file. To extend the
report to the full month, add rows and move the window label in the masthead.

## Where the per-post numbers come from

Earlier versions of this README said view counts were unavailable. They are —
just not through the ads MCP. `ads_get_ig_accounts` still returns empty for ad
account `924502380456661`, so `ads_get_ig_media` cannot be called and there is
no organic-insights tool on that connector. **Meta Business Suite has the data.**

1. Business Suite → **Insights → Content**, asset `1057665037421388`
   (the O2 Health Hub page). Add `&platform=Instagram` to the URL for
   Instagram-only account totals.
2. Set the date range with a preset (`This month`) and set the first filter to
   **Posts** — the table renders roughly 12 rows at a time and does not lazy-load
   reliably, so filtering stories out brings the whole post list into view.
3. Every post here is crossposted to Facebook, so the table's figures are
   combined. Click a row to open its detail page and read the
   **"X from Facebook / Y from Instagram"** split under Views and Interactions.
   That split is the Instagram number.
4. Account-level totals, organic-vs-ads breakdown and a `Published content`
   count (a useful cross-check) sit at **Insights → Content → Overview**.

### Reach vs views

Meta retired per-post **reach** for content published after 31 July 2025 and
replaced it with **views** and **viewers**. The Reach column still shown in the
content table for crossposted posts is effectively the Facebook side only — do
not report it as Instagram reach. Account-level Instagram reach is still
reported and is the only place the word belongs.
