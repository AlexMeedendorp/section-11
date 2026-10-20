# Weather Report Examples

The [route-weather map example](example-route-weather-map.png) is a real-route example render using a real Open-Meteo forecast and the v11.80 renderer.

Fictional worked examples, not live forecasts or athlete data. Times use athlete timezone Europe/Copenhagen, so report weather times omit the zone; a different zone or UTC fallback must be labelled. The map lines are output slots: no image is attached here, and an AI may fill a slot only after reading the matching page. Current binding and expiry are checked internally. Numeric ranges use consistent decimal places, and equal endpoints collapse. Each report has one final attribution line; explanatory paragraphs outside the report are not extra athlete-facing text.

## 1. Two rides with readable maps

**Weather report: Mon 19 Oct 10:00**  
Period: next 5 days

**River loop**  
Date: Tue 20 Oct  
Distance: 60 km  
Ascent: 220 m

Start: 11:00  
Moving time: 2h00m–2h30m  
Total time: 2h05m–2h45m  
Wind: E 6.0–6.4 m/s  
Gusts: up to 11.0 m/s  
Strongest gusts at: 20–35 km  
Headwind: first 35 km  
Rain: 0.8 mm/h, 65% wettest 12:00–13:00  
Temperature: 8.6–9.0 °C  
Feels like: 5.0 °C

Prepare: rain layer for cool, wet stops; keep the existing fuelling plan.

[Matching map page read and shown here; no duplicate band list]

**Lake loop**  
Date: Wed 21 Oct  
Distance: 60 km  
Ascent: 180 m

Start: 11:00  
Moving time: 2h00m–2h30m  
Total time: 2h05m–2h45m  
Wind: W 2.0–3.0 m/s  
Gusts: up to 5.0 m/s  
Rain: <0.1 mm/h, 10%  
Temperature: 12.0–15.0 °C  
Feels like: 11.0–14.0 °C

Prepare: adjustable layers for the warmer forecast; retain the existing fuel/fluid plan.

[Matching map pages read and shown in order here]

Comparison: Wednesday has lower gusts (5.0 versus 11.0 m/s) and lower hourly rain maxima at comparable tier and coverage; this does not authorize moving a workout.  
Coach note: follow [Environmental Conditions Protocol](../../SECTION_11.md#environmental-conditions-protocol) and recheck before departure.  
No route: Thursday recovery ride (no attachment); Saturday loop (attachment has no elevation).

Weather data by [Open-Meteo](https://open-meteo.com/), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Both fictional briefs were fetched at 09:30 and expire at 10:35 CEST, so the internal 10:00 report-time check passes. Complete coverage and well-supported personal ETA need no Note line. River bands assign headwind to 0–20 and 20–35 km, crosswind to 35–50 km and tailwind to 50–60 km; only 20–35 km holds the 11.0 m/s gust maximum. Rain periods support its wettest hour, not a claim about onset. Lake's bands do not establish a unique dominant class or gust-maximum location, so those two lines are omitted. Its numeric rain amount is zero with positive probability, hence the trace label. These are explanatory notes, not report text.

## 2. Assumed start and outlook uncertainty

**Mountain course**  
Date: Fri 23 Oct  
Distance: 96 km  
Ascent: 1,650 m

Start: 10:00 (assumed)  
No start time set. When are you leaving?

Moving time: 3h15m–5h10m  
Total time: 3h20m–5h25m  
Wind: SW/W 4.0–8.0 m/s  
Gusts: up to 13.0 m/s  
Rain: 4.0 mm/6h, 70% timing uncertain  
Temperature: 6.0–12.0 °C  
Feels like: unavailable

Prepare: adjustable warmth/rain protection; check refills against the broad total window.

Note: outlook Fri 08:00–20:00, direction and rain timing uncertain; terrain extrapolation/transferred timing; MET fallback.

[Matching neutral outlook page read and shown here; no bands]

Comparison: no comparable forecast supports choosing another day.  
Coach note: refresh when forecast-tier data arrive; preparation follows [Environmental Conditions Protocol](../../SECTION_11.md#environmental-conditions-protocol).

Weather data by [MET Norway](https://api.met.no/), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

The fictional report time is 10:00 CEST on 19 Oct. The compact `MOSTLY SW-W` label supplies direction, not a headwind segment or exact rain onset. No bands support gust locations or a dominant route-relative class in an outlook, so those lines are absent. A capable agent may preview a same-date push.py `--time` update, wait for confirmation before `--confirm`, then read the next sync's new binding. The six-hour rain maximum is not an hourly rate or a ride total. These are handling notes, not extra athlete-facing lines.

## 3. Partial forecast without a map

All fallback windows below are local on 19 Oct. Rows come directly from fictional `bands`, never raw sections. Gusts, feels-like and probability are unavailable in every band.

**Flat loop**  
Date: Mon 19 Oct  
Distance: 40 km  
Ascent: 0 m

Start: 12:00  
Moving time: 1h15m–1h50m  
Total time: 1h15m–2h20m  
Wind: E 4.0–6.0 m/s  
Gusts: unavailable  
Crosswind: 4–20 km and last 4 km  
Rain: 0.4 mm/h, probability unavailable, wettest 13:00–14:00  
Temperature: 8.0–10.0 °C  
Feels like: unavailable  
A: 0–4 km; time 12:00–12:20; Headwind; wind E 4.0–6.0 m/s; temperature 8.0–9.0 °C; rain 0.2 mm/h, wettest 12:00–13:00  
B: 4–12 km; time 12:10–12:55; Crosswind; wind E 4.0–6.0 m/s; temperature 8.0–9.0 °C; rain 0.2 mm/h, wettest 12:00–13:00  
C: 12–20 km; time 12:30–13:20; Crosswind; wind E 4.0–6.0 m/s; temperature 8.0–10.0 °C; rain 0.4 mm/h, wettest 13:00–14:00  
D: 20–28 km; time 12:45–13:45; Tailwind; wind E 4.0–6.0 m/s; temperature 9.0–10.0 °C; rain 0.4 mm/h, wettest 13:00–14:00  
E: 28–36 km; time 13:00–14:10; Tailwind; wind E 4.0–6.0 m/s; temperature 9.0–10.0 °C; rain 0.4 mm/h, wettest 13:00–14:00  
F: 36–40 km; time 13:10–14:20; Crosswind; wind E 4.0–6.0 m/s; temperature 9.0–10.0 °C; rain 0.4 mm/h, wettest 13:00–14:00

Note: partial brief, no map; generic ETA/default stops; MET fallback; gust, feels-like and probability gaps in every band.

Tomorrow / Ridge loop: brief expired; current weather unavailable and the old map is not shown.  
Comparison: an expired ride cannot be ranked against this partial forecast; missing gusts/probability are not favourable conditions.  
Coach note: prepare adjustable warmth/rain protection per [Environmental Conditions Protocol](../../SECTION_11.md#environmental-conditions-protocol), retain the existing fuelling plan and recheck.

Weather data by [MET Norway](https://api.met.no/), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

For a readable page 1 and missing page 2, show page 1 and transcribe only page 2's bands (for example I–J). If an older brief has no `bands`, state that band detail is unavailable and use only the supported summary. Do not reconstruct it from sections or infer dry intervals from the wettest period.

## 4. Disabled or mixed route availability

Disabled: "Route weather is disabled." No report weather values, maps, historical snapshots or alternate provider fetch.

In a report that also has routed rides, use one line: No route: "Tuesday endurance (no attachment); Thursday loop (attachment has no elevation)." Do not infer flatness or substitute home weather inside a ride block. Other unusable briefs receive one-line reasons; neither case clears conditions for riding. If every planned ride lacks a usable route within 120 h, use example 6 instead.

## 5. Passed start, not completed

Fictional report at 10:17 on 20 Oct. Sync supplied a fresh, matching 10:30 departure with `source: "assumed"`, `assumed_reason: "start_passed"` and `planned_local: "2026-10-20T10:00:00+02:00"`. No matching completed activity was found. The report does not retime the forecast itself.

**Harz test route**  
Date: Tue 20 Oct  
Distance: 96.5 km  
Ascent: 1,657 m

Start: 10:30 (assumed; planned 10:00 has passed.)  
When are you leaving?

Moving time: 3h20m–6h50m  
Total time: 3h20m–8h30m  
Wind: direction unavailable, 4.0–9.0 m/s  
Gusts: up to 12.0 m/s  
Rain: 0.6 mm/h, 65%  
Temperature: 9.0–16.0 °C  
Feels like: 7.0–14.0 °C

Prepare: bring a rain layer

Note: generic ETA and default stops, with no personal history

[Matching map page read and shown here; existing assumed badge]

Weather data by [Open-Meteo](https://open-meteo.com/), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

This excerpt does not supply bands supporting a gust location or dominant wind class, so those lines are omitted. The attribution remains identical without a shown map; use supported band fallback where available. A completed ride instead receives "weather unavailable: completed"; after its local date ends, "weather unavailable: missed". Neither is a reason to reuse an old PNG.

## 6. No planned ride has a usable route within 120 h

### Fetch-capable setup with known home

Fictional handling example: the AI has actual, permitted weather-fetch capability, no explicit current-chat location override, and `athlete_profile.location` in current `latest.json` is "Aalborg, North Denmark, Denmark". This is the default source; the current official dossier's Home region is used only when that profile location is null/empty. Following the shared [Point-weather location](../../SECTION_11.md#point-weather-location) rule, an explicit current-chat athlete statement would take priority for that conversation only, never from memory or earlier chats. The current calendar has only the three unrouted rides below within 120 h; any routed ride beyond that horizon is irrelevant to this case. Geocoding resolved the exact Aalborg city in DK, and Open-Meteo returned current data for the known planned times/windows. These example values are not data to reuse.

**Weather report: Tue 20 Oct 12:45**  
Period: next 5 days

No planned rides with a route in the next 5 days.  
Rides without a route: Wed Push/Recovery; Thu Aerobic Pressure; Fri Long Endurance

Attach a GPX/TCX to the workout in Intervals.icu; the next sync makes a route forecast and map.

**Weather at home**  
Place: Aalborg (from Intervals.icu)  
Date: Wed 21 Oct  
Time: 10:00–11:00  
Wind: W 3.0–4.0 m/s  
Gusts: up to 7.0 m/s  
Rain: 0.2 mm/h, 20%  
Temperature: 10.0–11.0 °C  
Feels like: unavailable

Date: Thu 22 Oct  
Time: 17:00–18:00  
Wind: NW 4.0–5.0 m/s  
Gusts: up to 8.0 m/s  
Rain: 0.4 mm/h, 40%  
Temperature: 9.0–10.0 °C  
Feels like: unavailable

Date: Fri 23 Oct  
Time: 09:00–13:00  
Wind: W/NW 3.0–5.0 m/s  
Gusts: up to 9.0 m/s  
Rain: 1.0 mm/h, 50%  
Temperature: 8.0–12.0 °C  
Feels like: unavailable

Weather data by [Open-Meteo](https://open-meteo.com/), [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Use [External API Reference](../agentic/EXTERNAL_APIS.md): Open-Meteo first, MET Norway fallback. Use the template's single final attribution line without a transformation note. Report text omits GeoNames credit because the displayed place is from the athlete's source; API documentation and other geocoding displays retain it. Preserve native rain periods; hourly maxima are not ride totals. Use one labelled set of facts per planned ride day, without adding Saturday/Sunday or inferring timing from ETA. Unknown starts use an explicitly labelled daily window. No wind classes, strongest-gust km locations, sections, bands, maps, ETA or route claims are supported.

### Setup without weather-fetch capability

For the same three rides and known home, a web chat without weather tools prints:

**Weather report: Tue 20 Oct 12:45**  
Period: next 5 days

No planned rides with a route in the next 5 days.  
Rides without a route: Wed Push/Recovery; Thu Aerobic Pressure; Fri Long Endurance

Attach a GPX/TCX to the workout in Intervals.icu; the next sync makes a route forecast and map.

A home forecast isn't available in this setup.

No Home block, invented values or provider attribution for an unperformed fetch. Never use completed-activity `weather_summary` or old snapshots as a forecast.

### Unknown home or failed fetch

With fetch capability but no explicit current-chat location, a null/empty `athlete_profile.location` in current `latest.json` and no Home region in the current official dossier, keep the no-route message/list and attachment hint, then print: "A home forecast isn't available: no home location. Add your city/country to your Intervals.icu athlete profile, or a Home region in your dossier." Omit the Home block. If geocoding is ambiguous or fails, or the permitted weather fetch fails, report the actual unavailability reason without values. Location memory, an earlier chat, heartbeat configuration or a past activity cannot fill either gap.

### Location source and ambiguity examples

These are selection examples, not additional forecasts. Route data for the session takes precedence over any home location for that session's weather.

| Current inputs | Point-weather result |
|---|---|
| Current-chat statement "I'm in Bergen, Norway today"; Intervals profile Aalborg; dossier Klampenborg | `Place: Bergen (you said)`, only in this conversation after successful geocoding |
| No current-chat override; current Intervals profile Aalborg; dossier Klampenborg | `Place: Aalborg (from Intervals.icu)` |
| No current-chat override; Intervals location null/empty; current official dossier Home region Klampenborg | `Place: Klampenborg (from dossier)` |
| No current-chat override; nonempty Intervals location cannot be resolved; dossier Klampenborg | Home forecast unavailable: geocoding ambiguous. Do not switch to the dossier |
| Earlier chat said Bergen; current Intervals profile Aalborg; no current travel indication | Use Aalborg `(from Intervals.icu)`; the old chat override has expired |
| Athlete says they are away but gives no current place | Omit weather or ask where; do not silently use home |

For the geocoding sample `Aalborg`, country `DK` leaves three results, but the exact name selects the city rather than `Aalborg SØ` or `Aalborg SV`. If multiple equally exact candidates remain, use the uniquely highest population only when they are comparable; a tie or missing population means ambiguous. A failed lookup gets its actual failure reason. Do not guess, pick the first result or silently use a lower-priority source.

### No planned rides at all

The current calendar is empty within 120 h. This example omits the optional Home block because there are no planned ride days to summarize:

**Weather report: Tue 20 Oct 12:45**  
Period: next 5 days

No planned rides in the next 5 days.

In a setup without fetch capability, also say: "A home forecast isn't available in this setup." The optional Home block remains subject to the same capability, location and planned-day gates; never invent an unscheduled day or add a workout.

### Nearby cases that do not use this branch

A usable route within 120 h with an expired brief gets its ride/reason line, not the no-route message or a home replacement. A missing map uses supported band text from its current brief. A report with at least one usable route retains the normal ride blocks and a single No route line for the others. Disabled weather still prints only "Route weather is disabled." with no forecast blocks or alternate provider fetch.
