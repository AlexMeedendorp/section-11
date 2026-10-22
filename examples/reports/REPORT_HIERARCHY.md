# Report Hierarchy Overview

Section 11-compliant AI coaching reports follow a layered structure. Each level builds on the one below it.

---

## Report Types & Length Norms

| Report Type | Trigger | Target Length | Purpose |
|-------------|---------|---------------|---------|
| **Pre-Workout** | Before each session | Four status groups, then a Today block per session; weather under outdoor rides/runs only | Readiness check, Go/Modify/Skip followed immediately by interpretation |
| **Post-Workout** | After each session | ~25-30 lines | Session analysis, execution quality |
| **7-day** | On request, ending today | One line per session and available fact | Rolling load, plan matches, capability and next seven days |
| **28-day** | On request, ending today | Four supplied chunks and available fact series | Rolling progression, plan matches and capability context |
| **Season** | On demand | Completed-week aggregates and matched-month comparisons | Season trajectory and YoY context |
| **Weather** | On request only | One fact per labelled line; separate identity, facts and maps; one line each for comparison/coach/no-route in mixed-route reports; explicit no-route case otherwise | Five-day route forecast/outlook and practical preparation |

---

## Information Flow Between Reports

Pre-workout informs preparation; post-workout describes completed sessions. The 7-day report summarizes today plus six local dates. The 28-day report consumes four supplied rolling chunks; its newest chunk equals the 7-day window. Season uses completed configured calendar weeks, so its boundaries differ from rolling reports.

Each report reads current source data; it never aggregates earlier AI reports.

**Weather is a parallel planning report**, sourced directly from matching current route-weather briefs, not aggregated from completed sessions. It covers all relevant rides in the next five days and may inform the same-day pre-workout block. It does not replace readiness, infer a Go decision, reschedule training or promote an outlook into section-level certainty. Missing/stale/disabled data stay explicit. Read and show accessible matching PNG pages in their listed order; never describe an unseen image. Expand into band detail only for missing/unreadable pages, JSON-only access or partial briefs, reading forecast `bands` directly rather than aggregating raw sections, one line per band after Feels like. Use separate labelled identity/weather facts, including Moving time and Total time, and an assumed-start question on its own line. Strongest gusts at and dominant wind effect by distance require supported band locations; omit them when unsupported. Wind effect estimates air resistance relative to calm air: Headwind adds it, Tailwind reduces it, Crosswind is roughly neutral (can slightly help or hinder), and Calm requires 0 m/s. Use supplied 80°/110° classes under the weather template's coverage and tie rules. Add blank lines before optional Prepare and material Note lines. Separate blocks with blank lines; no middle-dot separators or hyphen continuation lines. Weather clocks use local HH:MM unless a differing zone or UTC fallback needs a label. Always check expiry. End report text with one linked line, "Weather data by Open-Meteo, CC BY 4.0.", without a transformation note or separate GeoNames line. Maps and data labels remain unchanged.

When no planned ride has a usable route within 120 h, use the [template's explicit no-route case](WEATHER_REPORT_TEMPLATE.md#no-planned-ride-has-a-usable-route-within-120-h), including the ride list and GPX/TCX hint. Only actual fetch capability plus a location resolved under the [shared point-weather rule](../../SECTION_11.md#point-weather-location) allows a separate **Weather at home** block with labelled Place and Time lines; it never substitutes for route weather inside a ride block. Always show the place and source: current-chat statement first `(you said)`, then current `athlete_profile.location` `(from Intervals.icu)`, then dossier Home region `(from dossier)` only when the profile location is null/empty. Without fetch capability, say "A home forecast isn't available in this setup." No planned rides at all gets the single no-rides line, with the home block optional under the same capability/location and planned-day gates.

For fallback data, the single final attribution uses the actual provider name: "Weather data by MET Norway, CC BY 4.0." Name and link both providers on that line only when separate report blocks use both.

- **7-day:** per-session rows, selected key-session windows, Coggan Zones and Seiler TID 7d/28d, durability/EF/HRRc means with N, current load and recovery.
- **28-day:** four supplied dated chunk blocks, full 28-day wellness and DFA, per-sport pairing counts, checked plan results, Best efforts and two-paragraph Interpretation. Preserve 14-day step detail; no ceilings or separate progression section.
- **Season:** completed-week volume, CTL and coupled ACWR coverage, time-weighted Coggan Zones, separately labelled current Seiler TID and calendar-matched YoY. No invented prior-year phase labels.
- **Fun facts:** all three use supplied cycling period facts immediately before Interpretation. Preserve coverage, freshness and attribution. Biggest week belongs only in 28-day/Season. Equivalents are illustrative and never fueling advice.
- **Plan status:** not_assessed remains distinct in source data but is never a count category. Reports distinguish pairing from checked execution, with marker-only session lines and duration checks for paired no-step sessions of every sport. A broad plan match is not formal adherence.
- **Preservation:** post-workout Weekly totals, history week_start, phase detection, planned-week features and ordinary training-block concepts retain their existing meanings.

---

## Consistency Rules

All report types share these formatting principles:

1. **Data first, prose for interpretation only**: structured line-by-line, not bullet summaries
2. **Scannable in 30 seconds**: most important info at the top
3. **Assessment labels in parentheses**: (good), (optimal), (flag) after metrics
4. **Rolling/Season layout**: bold dated header, local Data updated, blank-line groups, avg with window, previous values in brackets; 28-day Fitness permits start -> now; no pipe joins
5. **Section 11 flags surface immediately**: never deferred to a later report
6. **Missing data**: omit missing/zero-only lines and empty sections; preserve meaningful comparison zeros and material coverage explanations
7. **Interpretation at the end**: 2-4 sentences for 7-day/Season; two paragraphs for 28-day, what happened then meaning

---

## Files

| File | Description |
|------|-------------|
| `PRE_WORKOUT_REPORT_TEMPLATE.md` | Pre-workout briefing template |
| `PRE_WORKOUT_REPORT_EXAMPLES.md` | 4 anonymized pre-workout examples |
| `POST_WORKOUT_REPORT_TEMPLATE.md` | Post-workout analysis template |
| `POST_WORKOUT_REPORT_EXAMPLES.md` | 4 anonymized post-workout examples |
| `7_DAY_REPORT_TEMPLATE.md` | 7-day report template |
| `7_DAY_REPORT_EXAMPLES.md` | 2 synthetic 7-day examples |
| `28_DAY_REPORT_TEMPLATE.md` | 28-day report template |
| `28_DAY_REPORT_EXAMPLES.md` | Synthetic 28-day and conditional DFA examples |
| `SEASON_REPORT_TEMPLATE.md` | Season report template |
| `SEASON_REPORT_EXAMPLES.md` | 2 synthetic season examples |
| `WEATHER_REPORT_TEMPLATE.md` | On-request five-day route-weather report |
| `WEATHER_REPORT_EXAMPLES.md` | Synthetic forecast, outlook, partial and unavailable examples |
