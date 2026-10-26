# Report Examples

Reference templates and examples for Section 11-compliant AI coaching reports.

---

## Output Format Guidelines

AI systems should structure athlete reports consistently.  
See templates and examples below for annotated reference.

Every period intensity line uses its own report_intensity block decoded with report_intensity_schema (2), with one line per selected sport and actual power/HR basis/mapping plus covered weeks and sessions. Use compatible report_intensity_comparison with its coverage limits; resolve explicit rolling refs with parent dates and monthly blocks by first occurrence across the ordered tiers; unresolved or old history is unavailable. Per-activity zones and zone_reference retain their meanings. See [Report intensity source](../../SECTION_11.md#report-intensity-source).

**Pre-Workout Reports must include:**
- Readiness assessment (HRV, RHR, Sleep vs baselines)
- Load context (TSB, ACWR, Load/Recovery, Monotony if elevated)
- Capability snapshot (Durability 7d mean + trend; TID drift if not consistent)
- One Today block per planned session in calendar order (or rest day + next session preview)
- Go/Modify/Skip recommendation with rationale

**Post-Workout Reports must include:**
- Bold dated header and local Data updated (zone only when different from athlete timezone or UTC fallback)
- One-line session summary
- Completed session metrics (power, HR, zones, decoupling, VI, TSS vs planned)
- Plan compliance assessment
- Weekly running totals (polarization, durability 7d/28d + trend, TID 28d + drift, CTL, ATL, TSB, ACWR, hours, TSS)
- Interpretation (2-4 sentences: compliance, key quality observations, load context, recovery note)
- One block per activity with blank-separated time, distance/context, climbs, power, HR and energy groups; separate Terrain, Temperature and Wind lines; descriptive activity power peaks
- Tomorrow as one session per line in start-time order, with sport and time when present; preserve all sessions

Post-workout duration displays round to whole minutes, while eligibility gates retain exact duration_formatted. Use labelled facts without middle-dot separators or hyphen continuation lines; power and HR zones each occupy one line with labels first. Weekly totals has four unlabelled groups: Phase; capability/TID; load/recovery; Hours/TSS. Missing fields stay omitted under the template's existing rules.

**7-day reports** cover today plus six local dates: sport totals, nonzero readable plan counts, marker-only session lines, selected key-session windows, Zones/TID, capability avg with window/N, fitness, full wellness, separate flag blocks, descriptive fun facts and Next 7 days without clock times. No planned TSS, not-assessed category or power-curve block.

**28-day reports** show Totals, Plan, Fitness start -> now, one dated block per supplied rolling_7d_chunks window (oldest first), full 28-day Wellness, Intensity, Key sessions, Best efforts with previous values in brackets, 28-day DFA, flags, fun facts and two-paragraph Interpretation. Preserve 14-day step detail and current calendar-week Phase; no ceilings or separate progression section.

**Season reports** use completed configured calendar weeks: Position, phase cycles ending at Deload (null weeks separate), Volume, Fitness with coupled ACWR known coverage, Intensity with dated half averages, matched-month YoY with prior values in brackets, non-empty Notable, season fun facts and Interpretation.

All three use bold dated headers, local Data updated, blank-line groups and one labelled fact per line. Means say avg with window; omit missing/zero-only lines and retain partial/stale coverage. Fun facts precede Interpretation, with equivalents inline from a clear dossier bottle statement or documented banana fallback. Peaks appear in 7-day/Season fun facts; Most work in a week appears only in 28-day/Season.

Permanent request aliases: "weekly report" means 7-day report; "block report" means 28-day report. The four old template/example paths remain managed pointers until the first release after 31 December 2026. Update personal instructions to the new filenames. The configured week start still controls history, Season, phase and planned-week features.

See `POST_WORKOUT_REPORT_TEMPLATE.md` for field reference and rounding conventions.  
See `REPORT_HIERARCHY.md` for how data flows between report levels.

**Weather Reports are on request only:** cover all relevant planned outdoor rides in the next five days using matching current route-weather briefs. Use the route name followed by separate Date, Distance and Ascent lines. Give Start, Moving time, Total time, Wind, Gusts, Rain, Temperature and Feels like one labelled line each. Strongest gusts at and the dominant wind effect by distance require the template's supplied-band evidence; omit unsupported claims. Relative to calm air, Headwind estimates added air resistance, Tailwind reduced resistance and Crosswind roughly neutral effect (can slightly help or hinder); Calm requires 0 m/s. Use the producer's 80°/110° classes with the existing coverage, location and tie rules. Put the assumed-start question on its own line, followed by a blank line. Separate identity, facts, maps and rides with blank lines, including before optional Prepare and material Note lines. Use no middle-dot separators or hyphen continuation lines. Weather times use local HH:MM, adding a zone only when different from the athlete's or a UTC fallback; maps/data retain zones. Check expiry even when omitted from text; preserve outlook uncertainty. End report text with one linked line, "Weather data by Open-Meteo, CC BY 4.0." No transformation note, safety tagline, GeoNames line or fetched timestamp belongs in report text; PNG footers stay unchanged. Comparison, Coach note and No route each take one line. Read and show accessible matching PNG pages in order; never describe an unseen map. Only JSON-only, partial or missing/unreadable-map paths add forecast band detail after Feels like, one line per supplied `bands` entry, never aggregated from raw sections. Pre-workout uses the same weather layout directly under each outdoor ride or run only. No forecast report data or maps when route weather is disabled.

**When no planned ride has a usable route within 120 h**, replace the single No route line with the [template's explicit no-route case](WEATHER_REPORT_TEMPLATE.md#no-planned-ride-has-a-usable-route-within-120-h): clear message, ride list and GPX/TCX hint. Only an AI with actual weather-fetch capability and a location resolved under the [shared point-weather rule](../../SECTION_11.md#point-weather-location) may add a separate **Weather at home** block with Place/source and Time lines, never route detail or a replacement inside a ride block. Without fetch capability, say "A home forecast isn't available in this setup." No planned rides at all gets a single no-rides line; the optional home block follows the template's same gates and planned-day rule.

---

For fallback data, the single final attribution names the actual provider: "Weather data by MET Norway, CC BY 4.0." Name both providers on that same line only when separate report blocks use both. Link each provider and the licence.

## Files

| File | Description |
|------|-------------|
| [REPORT_HIERARCHY.md](REPORT_HIERARCHY.md) | Overview of all report types, length norms, and data flow |
| [PRE_WORKOUT_REPORT_TEMPLATE.md](PRE_WORKOUT_REPORT_TEMPLATE.md) | Template structure for pre-workout briefings (no data) |
| [PRE_WORKOUT_REPORT_EXAMPLES.md](PRE_WORKOUT_REPORT_EXAMPLES.md) | Fictional route, rest-day, indoor, multi-session and outdoor-run examples |
| [POST_WORKOUT_REPORT_TEMPLATE.md](POST_WORKOUT_REPORT_TEMPLATE.md) | Template structure for post-workout analysis (no data) |
| [POST_WORKOUT_REPORT_EXAMPLES.md](POST_WORKOUT_REPORT_EXAMPLES.md) | 8 post-workout scenarios plus synthetic new-field excerpts |
| [7_DAY_REPORT_TEMPLATE.md](7_DAY_REPORT_TEMPLATE.md) | Template structure for 7-day reports (no data) |
| [7_DAY_REPORT_EXAMPLES.md](7_DAY_REPORT_EXAMPLES.md) | 2 synthetic example 7-day reports |
| [28_DAY_REPORT_TEMPLATE.md](28_DAY_REPORT_TEMPLATE.md) | Template structure for 28-day reports (no data) |
| [28_DAY_REPORT_EXAMPLES.md](28_DAY_REPORT_EXAMPLES.md) | 2 synthetic example 28-day reports |
| [SEASON_REPORT_TEMPLATE.md](SEASON_REPORT_TEMPLATE.md) | Template structure for season reports (no data) |
| [SEASON_REPORT_EXAMPLES.md](SEASON_REPORT_EXAMPLES.md) | Synthetic season examples |
| [WEATHER_REPORT_TEMPLATE.md](WEATHER_REPORT_TEMPLATE.md) | On-request five-day planned-route weather |
| [WEATHER_REPORT_EXAMPLES.md](WEATHER_REPORT_EXAMPLES.md) | Synthetic forecast, outlook and missing-data examples |

---

## Report Types

### Pre-Workout Briefing (grouped status and session blocks)
Generated **before** a planned session. Includes:
- Bold Pre-workout date and zone-labelled Data updated header
- Current readiness (HRV, RHR, Sleep vs baselines)
- Load context (TSB, ACWR, Load/Recovery, Monotony if > 2.3)
- Capability snapshot (Durability 7d mean + trend; TID drift if not consistent)
- Four blank-separated status groups without subgroup headings; preserve all template fields and conditionals
- A Today block per session with available type, route facts, duration, TSS and condensed main set; omit an absent structure rather than printing a no-structure line
- Weather directly under outdoor rides and runs only, with labelled home location/source when no route is supplied
- Go/Modify/Skip Recommendation followed immediately by two-to-three-sentence interpretation without a separate heading; expand Modify/Skip

### Post-Workout Analysis (grouped activity blocks)
Generated **after** a completed session. Includes:
- Execution summary (actual vs planned)
- Key metrics (power, HR, decoupling, VI, carbs)
- Zone distribution (Grey Zone and Quality tracking)
- Load impact (updated CTL, ATL, TSB, weekly totals)
- Capability update (Durability 7d/28d + trend, TID 28d + drift in weekly totals)
- Coaching interpretation
- Descriptive W/kg, work, available exact power peaks, elapsed time and sport-aware pace from sync 3.147; peaks never establish FTP, zones or readiness

### 7-day report

Generated on request for a rolling seven-date window. Follow [7_DAY_REPORT_TEMPLATE.md](7_DAY_REPORT_TEMPLATE.md) and its complete/sparse synthetic examples.

### 28-day report

Generated on request from four supplied rolling chunks. Follow [28_DAY_REPORT_TEMPLATE.md](28_DAY_REPORT_TEMPLATE.md); its examples preserve the DFA comparison and diagnostic cases.

### Season report

Generated on request from completed calendar weeks with separately labelled current snapshot context and calendar-matched YoY. Follow [SEASON_REPORT_TEMPLATE.md](SEASON_REPORT_TEMPLATE.md) and [SEASON_REPORT_EXAMPLES.md](SEASON_REPORT_EXAMPLES.md).

---

## Brevity Rule

These templates follow Section 11's brevity principle:
- **Normal metrics:** Brief (2-3 sentence interpretation + key data)
- **Threshold breach:** Detailed (full analysis with recommendations)
- **Rest day:** Minimal (confirm recovery status, preview next session)
- **Athlete asks "why":** Deep dive on specific area

---

## Conditional Fields

Some fields appear only when relevant:
- **Weather:** Route data for the session takes precedence over any home location for that session's weather. For point forecasts use an explicit current-chat statement first `(you said)`, then `athlete_profile.location` in current `latest.json` `(from Intervals.icu)`, then the current official dossier's Home region `(from dossier)` only when the profile location is null/empty. Show the place and source under the [shared rule](../../SECTION_11.md#point-weather-location). Chat overrides last only for that conversation, never from memory or earlier chats; heartbeat configuration is not a weather-location source. If something indicates the athlete is elsewhere and the location is unresolved, omit weather or ask. City-level text needs [geocoding](../agentic/EXTERNAL_APIS.md#geocoding-for-point-weather); ambiguity or failure means unavailable with the reason. If all three sources lack a location, say "A home forecast isn't available: no home location. Add your city/country to your Intervals.icu athlete profile, or a Home region in your dossier."
- **Monotony:** Include only if > 2.3; omit entirely when normal
- **Load/Recovery tolerance note:** Include only when within 0.2 of threshold
- **Coach notes** (brief contextual tips) are encouraged to humanize recommendations
- **Key session detail (7-day):** Cap at 2-3 sessions; if 4+ hard days, prioritize most notable

---

## Notes

- Worked report text uses anonymized/placeholder data; replace with actual values from your JSON feed
- Zone percentages round to nearest whole number (see rounding convention in POST_WORKOUT_REPORT_TEMPLATE.md)
- Reports read current source data at their own scope; see REPORT_HIERARCHY.md for rolling versus calendar windows.
- Flags surface immediately in the 7-day report and retain documented resolution in the 28-day report.
