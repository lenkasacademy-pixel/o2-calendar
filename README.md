# O2 Health Hub — content calendar

Planning doc for **@o2health_hub** (Instagram) — September to October 2026.

Live: https://lenkasacademy-pixel.github.io/o2-calendar/

Single self-contained `index.html`. Data lives in three arrays near the bottom:

- `POSTED` — what is already on the grid. Read from the **public** profile on
  11 Sep 2026. The logged-out view caps at 12 posts and exposes only date and
  media type, so there are **no captions, likes or view counts** here.
- `PLAN` — `[date, pillar, format, title, brief, cta]`, 20 posts to 9 Oct.
- `PILLARS` — the five content themes and their colours.

`TODAY` drives the highlighted cell; move it on each refresh.

## Why the plan is ordered this way

Weighted by what the ads actually produce (see `lenkasacademy-pixel/o2-reports`):
autism leads every week at ₹113 per 20-second call against ₹332 for endoscopy.
Diabetes and weight get a weekly slot because they sit in the bio but have never
been advertised. Cadence is 5/week Mon–Fri, reel-led — at 290 followers, reach
has to come from non-followers.

## Known gap: no view counts

Per-post views are **not available** to the Meta connector — `ads_get_ig_accounts`
returns empty for ad account `924502380456661` (and for `707133374756093`), so
@o2health_hub is not linked to any ad account and `ads_get_ig_media` cannot be
called. This MCP has no organic-insights tool in any case. To fill in views:

1. Link the Instagram account in Business settings (also fixes post boosting), or
2. Export Instagram Insights → Content → last 30 days, and paste the numbers in.

Once available, add a `views` field to `POSTED` and surface it on the posted chips.
