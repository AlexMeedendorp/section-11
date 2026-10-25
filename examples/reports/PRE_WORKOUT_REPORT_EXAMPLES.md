# Pre-Workout Report Examples

> Fictional examples showing standard pre-workout report format, not current athlete data.  
> See `PRE_WORKOUT_REPORT_TEMPLATE.md` for field reference.

The fictional Polarization/TID lines use period-local report_intensity blocks selecting cycling. Each seven-day example has four observed cycling sessions with compatible power zones in one rolling week; the 28-day shifting example has sixteen across four chunks. These new intensity values and coverage counts are synthetic, independently supplied for this illustration; they do not reanalyse other example metrics. Fetch completeness remains unknown. These illustrations decode the file-level schema 2; counts do not imply exact covered dates.

The point-weather blocks use the shared [Point-weather location](../../SECTION_11.md#point-weather-location) rule. Example 2 uses `athlete_profile.location` from current `latest.json`; example 4 uses a current-chat statement; example 5 uses the current official dossier's Home region because the profile location is null/empty. Route data takes precedence; unresolved travel means omit weather or ask. Rest days, indoor sessions, walks and other sports have no weather. All dates, metrics, source assignments and weather values below are fictional, independent of the approved live-data layout references.

Assume permitted geocoding and weather fetches succeeded where a home forecast is shown. The athlete timezone is Europe/Copenhagen. Weather times omit its zone label; Data updated keeps the local timestamp and zone. Link [Open-Meteo](https://open-meteo.com/) and [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) in the one final attribution line. GeoNames credit remains in API documentation and other geocoding displays; report places are labelled with the athlete's source. Missing values stay unavailable.

## Assumed departure clarification (fictional route-weather excerpt)

```text
**Today: Fictional mountain ride**
Outdoor ride
Distance: 96.5 km
Ascent: 1,657 m
Terrain: hilly

Climbs
4.0 km: 0.8 km at 3.2% (max 5.4%)

Pacing: keep the early climb controlled.

**Weather on the route**
Start: 10:00 (assumed)
No start time set. When are you leaving?

Moving time: 3h20m–6h50m
Total time: 3h20m–8h30m
Wind: W 4.0–9.0 m/s
Gusts: up to 12.0 m/s
Strongest gusts at: 24–42 km
Headwind: first 42 km and last 18.5 km
Rain: 0.6 mm/h, 65% wettest 13:00–14:00
Temperature: 9.0–16.0 °C
Feels like: 7.0–14.0 °C

Prepare: bring a rain layer

Note: generic ETA and default stops, with no personal history

Weather data by Open-Meteo, CC BY 4.0.
```

This fictional session excerpt omits the surrounding status/recommendation, not required fields in a full report. No duration or structure was supplied, so neither line appears. Its invented complete bands assign headwind to 0–24, 24–42 and 78–96.5 km (60.5 km), crosswind to 42–60 km (18 km) and tailwind to 60–78 km (18 km); only the 24–42 km band has the 12.0 m/s maximum gust. These support both location lines without copying the approved live reference's numbers. Rain coverage supports the stated wettest window, not an onset claim. Matching PNG pages are posted directly after the complete report text, only after being read.

Midnight is unset, so the default is assumed. Check binding and expiry before using the brief. A capable agent may preview the exact push.py time update, apply it only after confirmation and then re-read the next sync's brief. Missing/unreadable pages require the applicable `bands[].display` fallback, never raw-section aggregation. Preparation follows Environmental Conditions Protocol; readiness rules are unchanged.

If sync supplied `assumed_reason: "start_passed"` and a 10:30 departure after planned 10:00, use `Start: 10:30 (assumed; planned 10:00 has passed.)`, then `When are you leaving?` on its own line and a blank line. Use the newly bound brief's weather/map, never retime it in the report. See the [passed-start example](WEATHER_REPORT_EXAMPLES.md#5-passed-start-not-completed). The same final attribution is required with or without a map.

---

## Example 1: Rest Day: No Sessions Scheduled

```
**Pre-workout: Sunday 18 January**
Data updated: 18 Jan 09:15 CET

**Current Status Summary**
RHR: 44 bpm (baseline: 46 bpm)
HRV: 58 ms (7d avg: 54 ms)
Sleep: 8h30m
Sleep Quality: 3/4

TSB: +1.85
CTL: 72.40
ATL: 70.55
ACWR: 0.84 (optimal); start-of-day
Recovery Index: 0.93 (good)
Ramp Rate: -1.30
Load/Recovery: 5.8
Durability: 2.14% 7d mean(4) (stable)
EF: 1.44 7d mean(4) (stable)

Polarization (cycling, power, 1/1 rolling week; 4/4 sessions): Z1+Z2 90%, Z3 3%, Z4+ 7%; Polarized (PI: 2.32)

Total hours, last 7 days: 14h12m
Total activities, last 7 days: 11
Total TSS, last 7 days: 468

Rest day: no sessions scheduled.

Next session: Monday: 3×10min Threshold @ 260W (TSS 88)

**Recommendation: Go**
Readiness is good: HRV is above its 7-day average, RHR is below baseline and sleep is solid.
Keep the scheduled rest day; review readiness again before tomorrow's threshold session.
```

---

## Example 2: Endurance Day: Normal Readiness

```
**Pre-workout: Monday 19 January**
Data updated: 19 Jan 08:45 CET

**Current Status Summary**
RHR: 46 bpm (baseline: 46 bpm)
HRV: 53 ms (7d avg: 54 ms)
Sleep: 7h48m
Sleep Quality: 3/4

TSB: -3.20
CTL: 73.50
ATL: 76.70
ACWR: 1.04 (optimal); start-of-day
Recovery Index: 0.88 (good)
Ramp Rate: 0.45
Load/Recovery: 6.0
Durability: 1.85% 7d mean(3) (stable)
EF: 1.45 7d mean(3) (stable)

Polarization (cycling, power, 1/1 rolling week; 4/4 sessions): Z1+Z2 90%, Z3 3%, Z4+ 7%; Polarized (PI: 2.32)

Total hours, last 7 days: 15h18m
Total activities, last 7 days: 12
Total TSS, last 7 days: 502

**Today: SkiErg**
Indoor SkiErg
Duration: 10m
Main set: Zone 2

**Today: Endurance**
Outdoor ride
Duration: 2h00m
Planned TSS: 71
Main set: 15m @153W; 1h30m @162W; 15m @150W

**Weather at home**
Place: Klampenborg (from Intervals.icu)
Time: 10:00–12:00
Temperature: 2.0 °C
Feels like: unavailable
Wind: S 5.1 m/s
Gusts: unavailable
Rain: unavailable

Prepare: warm layers and gloves.

**Recommendation: Go**
HRV and RHR are near baseline, with 7h48m sleep and balanced load.
Proceed as planned, keeping the ride steady and dressing for the cold.

Weather data by Open-Meteo, CC BY 4.0.
```

---

## Example 3: Interval Day: Fresh and Ready

```
**Pre-workout: Wednesday 21 January**
Data updated: 21 Jan 09:30 CET

**Current Status Summary**
RHR: 44 bpm (baseline: 46 bpm)
HRV: 61 ms (7d avg: 55 ms)
Sleep: 8h54m
Sleep Quality: 1/4

TSB: +0.50
CTL: 74.20
ATL: 73.70
ACWR: 0.99 (optimal); start-of-day
Recovery Index: 0.91 (good)
Ramp Rate: 0.30
Load/Recovery: 5.9
Durability: 2.40% 7d mean(3) (improving)
EF: 1.47 7d mean(3) (improving)

Polarization (cycling, power, 1/1 rolling week; 4/4 sessions): Z1+Z2 90%, Z3 3%, Z4+ 7%; Polarized (PI: 2.32)

Total hours, last 7 days: 16h6m
Total activities, last 7 days: 13
Total TSS, last 7 days: 530

**Today: VO2 MAX**
Indoor ride
Duration: 1h30m
Planned TSS: 84
Main set: 3 sets of 10×(30s @320W, 15s recovery)

**Recommendation: Go**
HRV is above its 7-day average, RHR is below baseline and sleep was 8h54m.
Proceed with the planned intervals; load and readiness support the session.
```

---

## Example 4: Compromised Readiness: Modify Recommended

```
**Pre-workout: Friday 23 January**
Data updated: 23 Jan 08:55 CET

**Current Status Summary**
RHR: 50 bpm (baseline: 46 bpm)
HRV: 42 ms (7d avg: 54 ms)
Sleep: 5h12m
Sleep Quality: 4/4

TSB: -12.80
CTL: 74.90
ATL: 87.70
ACWR: 1.17 (optimal); start-of-day
Recovery Index: 0.68 (moderate)
Ramp Rate: 1.10
Load/Recovery: 7.1 (tolerance 6.4): over threshold; back off today.
Durability: 5.80% 7d mean(3) (declining) ⚠️
EF: 1.38 7d mean(3) (declining) ⚠️
Monotony: 2.5: elevated, add variety this week

Polarization (cycling, power, 1/1 rolling week; 4/4 sessions): Z1+Z2 90%, Z3 3%, Z4+ 7%; Polarized (PI: 2.32)
TID 28d (cycling, power, 4/4 rolling weeks; 16/16 sessions): Pyramidal; observed-session drift: shifting

Total hours, last 7 days: 18h24m
Total activities, last 7 days: 14
Total TSS, last 7 days: 612

**Today: Threshold**
Outdoor ride
Duration: 1h30m
Planned TSS: 90
Main set: 3×12min @260W

**Weather at home**
Place: Klampenborg (you said)
Time: 10:00–11:30
Temperature: 1.0 °C
Feels like: unavailable
Wind: E 2.1 m/s
Gusts: unavailable
Rain: unavailable

Prepare: warm layers and gloves.

**Recommendation: Modify**
Readiness: Compromised. HRV 42 is 22% below 7d average, RHR spiked to 50 (+4 above baseline),
and sleep duration was 5h12m. These are the classified amber/red signals; quality 4/4 is context only.
Load/Recovery over threshold at 7.1, monotony elevated at 2.5, and durability declining (5.8% mean
decoupling, up from 3.2% 28d avg). Body is absorbing a heavy week and aerobic efficiency is slipping.
Swap threshold intervals for an easy endurance ride (Z2, 1h30m, ~50 TSS). Save the intensity
for when readiness recovers.

Weather data by Open-Meteo, CC BY 4.0.
```

## Synthetic multi-main-sport intensity excerpt

A triathlon period with 60/28/12% eligible TSS selects cycling, running and swimming independently of zone availability. Cycling has two power sessions and running three five-band HR sessions in the rolling week; two swims have pace only. No other status or readiness rule changes.

```text
Polarization (cycling, power, 1/1 rolling week; 2/2 sessions): Z1+Z2 80%, Z3 15%, Z4+ 5%; Pyramidal
Polarization (running, HR, 1/1 rolling week; 3/3 sessions): Z1+Z2 75%, Z3 15%, Z4+ 10%; Pyramidal
Zones (swimming, 1 active rolling week; 0/2 sessions): unavailable, pace mapping deferred
```

Observed-session distributions are not proof of complete activity retrieval. A missing new block yields unavailable intensity rather than an all-sports fallback.

---

## Sleep context excerpts (fictional)

These optional lines belong within the existing readiness status group, not replacement reports. All values and dates are invented. The reference is 8h across 28/28 dates, 12 May–8 June 2026; the recent review is 9–15 June. Each of the latest three nights has 27600 raw seconds (7h40m), giving exactly 3600 seconds combined difference. All three are above seven hours and still meet the context rule. No extra readiness signal or automatic recommendation change follows.

```text
Sleep context: 3 consecutive nights below personal reference, 13–15 Jun: 7h40m, 7h40m, 7h40m; reference 8h (28/28 nights), recent 7/7; low confidence
```

With 12 June missing and the other six recent dates observed, the same latest three qualify. Do not give a full-week mean or imply a known episode start across the gap:

```text
Sleep context: 3 observed consecutive nights below reference, 13–15 Jun: 7h40m, 7h40m, 7h40m; reference 8h (28/28 nights), recent partial 6/7, 12 Jun missing; low confidence
```

When a pattern is requested but 14 June is missing, the latest three are incomplete:

```text
Sleep context: unavailable for the repeat comparison; 14 Jun missing, recent 6/7, reference 8h (28/28 nights); low confidence
```

With an absent or stale block, say the requested context is unavailable and name that cause. With false/null and no relevant request or athlete report, omit the line. A full-window run reads “at least 7”, never an exact episode length.

Explicit athlete reports of fragmentation on 13 and 15 June remain separate even with above-reference measured durations:

```text
Sleep context: repeated fragmentation reported by you for 13 and 15 Jun; duration comparison does not establish awakenings; low confidence
```

“Recently” without dates does not become two nights. Repeated messages about one date count once; no statement is unknown, and a denial or correction applies only to its stated dates. Keep day disruption and current fatigue separate without double-counting. For a later same-day session, put relevant context within Current state or Decision of the continuation block and retain its current-state and start-of-day ACWR rules.

## Example 5: Outdoor run and walk (session excerpt)

The fictional run has no supplied duration, TSS or structure; those lines are omitted. Profile location is null/empty and the current official dossier supplies Klampenborg. A permitted point forecast covers the known planned hour. The following walk gets no weather. This excerpt omits the surrounding status and recommendation.

```text
**Today: Easy run**
Outdoor run

**Weather at home**
Place: Klampenborg (from dossier)
Time: 10:00–11:00
Temperature: -2.0 °C
Feels like: unavailable
Wind: N 3.8 m/s
Gusts: unavailable
Rain: unavailable

Prepare: warm layers and gloves.

**Today: Evening walk**
Walk
Duration: 20m

Weather data by Open-Meteo, CC BY 4.0.
```
