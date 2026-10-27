# 28-day Report Examples

Synthetic fixtures only. The four supplied chunks are newest first in JSON and displayed oldest first. Chunk 1 agrees with 7_DAY_REPORT_EXAMPLES.md. The fictional dossier states in prose: "Each training bottle contains 60 g carbohydrate." This is sufficient bottle evidence without a table.

## Example 1: four rolling chunks

Intensity illustrates synthetic period-local report_intensity blocks selecting cycling in each chunk and the whole 28-day window. Walks remain below selection thresholds. Cycling has 4, 4, 3 and 3 covered sessions in chronological chunks, 14 in total. Fetch completeness is unknown. The flagged activity has a synthetic power/outdoor/270 W zone_reference. These illustrations decode the file-level schema 2; counts do not imply exact covered dates.

```text
**28-day report: Wed 17 June to Tue 14 July 2026**
Data updated: 14 Jul 15:30

The most recent two chunks carry less load than the first two.

Phase: Base, week 3

**Totals**
Ride: 20h45m (14 sessions, 995 TSS)
Walk: 1h30m (3 sessions, 30 TSS)
Total: 22.25h (17 sessions, 1025 TSS)

**Plan**
Rides: 12 of 14 planned
Walks: 3 of 3 planned ✅
Checked against plan: 9 of 12 followed
Detail: older step assessments are retained; full detail covers 14 days.

**Fitness (start of period -> now)**
CTL: 41.8 -> 42.6 (+0.8)
ATL: 46.0 -> 44.0 (-2.0)
TSB: -4.2 -> -1.4 (+2.8)

**17 Jun to 23 Jun**
Hours: 6h
TSS: 270
CTL: 43.2
Zones (cycling, power, 1/1 rolling week; 4/4 sessions): Z1+Z2 89%, Z3 7%, Z4+ 4%
Hard days: 2 (18 Jun intervals; 21 Jun tempo)
Durability (cycling): 7-day avg 3.6% (N=2)
EF: 7-day avg 1.25 (N=2)
HRRc: 7-day avg 33 bpm (N=1)
HRV: 7-day avg 61 ms (7 days)
RHR: 7-day avg 53 bpm (7 days)
Sleep: 7-day avg 7.00h (7 days)

**24 Jun to 30 Jun**
Hours: 6.5h
TSS: 300
CTL: 43.8
Zones (cycling, power, 1/1 rolling week; 4/4 sessions): Z1+Z2 86%, Z3 10%, Z4+ 4%
Hard days: 2 (25 Jun intervals; 28 Jun by power Z3 only)
Durability (cycling): 7-day avg 3.4% (N=2)
EF: 7-day avg 1.27 (N=3)
HRRc: 7-day avg 32 bpm (N=1)
HRV: 7-day avg 62 ms (6 days)
RHR: 7-day avg 52 bpm (6 days)
Sleep: 7-day avg 7.25h (6 days)

**1 Jul to 7 Jul**
Hours: 4.75h
TSS: 220
CTL: 42.1
Zones (cycling, power, 1/1 rolling week; 3/3 sessions): Z1+Z2 94%, Z3 4%, Z4+ 2%
Hard days: 1 (3 Jul intervals)
Durability (cycling): 7-day avg 3.1% (N=2)
EF: 7-day avg 1.29 (N=2)
HRRc: 7-day avg 32 bpm (N=1)
HRV: 7-day avg 62 ms (7 days)
RHR: 7-day avg 52 bpm (7 days)
Sleep: 7-day avg 7.25h (7 days)

**8 Jul to 14 Jul**
Hours: 5h
TSS: 235
CTL: 42.6
Zones (cycling, power, 1/1 rolling week; 3/3 sessions): Z1+Z2 91%, Z3 6%, Z4+ 3%
Hard days: 1 (10 Jul intervals)
Durability (cycling): 7-day avg 3.1% (N=2)
EF: 7-day avg 1.30 (N=3)
HRRc: 7-day avg 31 bpm (N=1)
HRV: 7-day avg 63 ms (7 days)
RHR: 7-day avg 51 bpm (7 days)
Sleep: 7-day avg 7.50h (7 days)

**Wellness (28 days)**
HRV: 28-day avg 62 ms (27 days)
RHR: 28-day avg 52 bpm (27 days)
Sleep: 28-day avg 7.25h (27 days)
Sleep quality: 28-day avg 2.1/4 (25 days)
Weight: 68.0 kg, 14 Jul (28-day avg. 68.1 kg, 22 weigh-ins)
Weight trend: +0.08 kg/week
Feel: 28-day avg 2.1/5 (N=11)
RPE: 28-day avg 3.9/10 (N=11)

**Intensity**
Zones 28d (cycling, power, 4/4 rolling weeks; 14/14 sessions): Z1+Z2 90%, Z3 7%, Z4+ 3%
TID 28d (cycling, power, 4/4 rolling weeks; 14/14 sessions): Pyramidal

**Key sessions**
**⚠️ 10 Jul, Stepped endurance**
Target: step 2, 190 W for 30m
Actual: 176 W over 1799 seconds

Long ride: 28 Jun, Meadow route, 2h45m, steady power with VI 1.03
Tempo whole-ride decoupling: 21 Jun 3.8%; 28 Jun 3.4% (both at least 90m, VI 1.03)

**Best efforts (Cycling, last 28 days, previous 28 days in brackets)**
5 s: 670 W, 25 Jun (700 W)
1 min: 370 W, 25 Jun (380 W)
5 min: 265 W, 25 Jun (260 W)
20 min: 225 W, 28 Jun (219 W)
60 min: 200 W, 28 Jun (198 W)
HR 20 min: 158 bpm (160 bpm)
Shift: short efforts were lower; sustained efforts were slightly higher.

**DFA a1 (28 days)**
DFA a1: 28-day avg 1.18
Drift: 28-day avg -0.04 (3 eligible sessions)
Sessions: 4 sufficient, from available retained summaries
Easy-state guard: 138 bpm, 3 eligible sessions (descriptive)
Easy-state guard Indoor: 151 W, 3 eligible sessions

**Section 11 flags**
⚠️ Z3 in easy sessions
Session: 28 Jun, Meadow route
Z3 by power: 36m
Z3 by HR: 3m
Zones: power, from outdoor FTP 270 W

**Fun facts (cycling, descriptive)**
Max power (1 s): 780 W, 25 Jun, Hill circuit
Max HR: 179 bpm, 25 Jun, Hill circuit

Longest ride: Meadow route, 28 Jun, 2h45m, 72 km (outdoor)
Distance ridden: 180 km (indoor)
Distance ridden: 330 km (outdoor)
Climbed: 350 m (indoor)
Climbed: 2600 m (outdoor)

Time in the saddle: 20h45m

Work: 14000 kJ (energy of about 58.3 of your 60 g bottles)
Carbs used: 1200 g (about 20.0 of your 60 g bottles)
Most work in a day: 28 Jun, 2100 kJ, 180 g carbs
Most work in a week: 24 Jun to 30 Jun, 4500 kJ, 400 g carbs

**Interpretation**
Volume fell in the latter two chunks while EF and wellness observations held. Sustained power observations were slightly higher than the previous 28 days.

The power-only hard day uses the activity's outdoor FTP reference; its disagreement with HR does not establish intentional intensity or validate zone settings. Retained step assessments and limited DFA coverage constrain the interpretation; the easy-state guard supports no threshold change.
```

## Example 2: sparse data

Only the shown observations exist. The two middle chunks have zero-only metrics and are omitted; their supplied dates still determine the full window. Paired structured plans without step assessments do not acquire duration-only verdicts.

```text
**28-day report: Wed 17 June to Tue 14 July 2026**
Data updated: 14 Jul 15:30

The export contains limited observations for the rolling window.

**Totals**
Ride: 1.67h (5 sessions, 62 TSS)
Total: 1.67h (5 sessions, 62 TSS)

**Plan**
Rides: 5 of 5 planned ✅

**17 Jun to 23 Jun**
Hours: 1h
TSS: 40
EF: 7-day avg 1.20 (N=2)
HRV: 7-day avg 60 ms (2 days)

**8 Jul to 14 Jul**
Hours: 0.67h
TSS: 22
EF: 7-day avg 1.23 (N=2)
HRV: 7-day avg 61 ms (1 day)

**Wellness (28 days)**
HRV: 28-day avg 60.3 ms (3 days)

**Interpretation**
Five sessions were paired to plans across the window.

Pairing alone does not establish execution quality, and the sparse observations do not support a continuous training trend.
```

When LT1/LT2 estimates are absent, their rows are absent. An eligible easy-state guard remains visible independently of threshold confidence; a null drift estimate is never displayed as zero.

## Synthetic ski holiday and indoor ski fragment

For 28 September to 25 October, cycling supplies 75% TSS/60% time and Nordic skiing 25%/40%. Nordic skiing combines four outdoor Nordic ski sessions and one indoor ski session in the 5-11 October chunk, all using the same five-band HR mapping. Cycling has eight power sessions in the other three chunks. The independently selected whole-period lines are:

```
Zones (cycling, power, 3/4 rolling weeks; 8/8 sessions): Z1+Z2 90%, Z3 7%, Z4+ 3%
Zones (Nordic skiing, HR, 1/4 rolling weeks; 5/5 sessions): Z1+Z2 85%, Z3 10%, Z4+ 5%
Nordic skiing coverage: 1 active week; absence in the other chunks is not missing zones
```

These describe observed sessions; activity-fetch completeness is unknown. If a sixth ski session lacks zones, show 5/6 and partial coverage without a whole-period drift claim. Keep a separate power or incompatible HR-mapping bucket if one occurs; never label the line mixed.

## Selected-sport fact fragments

Each independent synthetic fragment assumes its named sport is selected for this report's period and that the matching facts are compatible. Snow ascent has no observations. Rowing duration coverage is partial; a longest session's distance is its own distance. Season longest sessions remain in Volume.

```
**Fun facts (running, descriptive)**
Max HR: 172 bpm, 12 Jul, Park loop

Longest run: Park loop, 12 Jul, 1h,
10 km (outdoor)
Distance run: 18 km (outdoor)
Climbed: 160 m (outdoor)

Running time: 1h50m

**Fun facts (swimming, descriptive)**
Max HR: 158 bpm, 10 Jul, Lake swim
(2 of 3 sessions)

Longest swim: Lake swim, 10 Jul, 40m,
1.8 km (open water)
Distance swum: 2 km (pool/other)
Distance swum: 1.8 km (open water)

Swimming moving time: 1h30m

**Fun facts (Nordic skiing, descriptive)**
Max HR: 165 bpm, 11 Jul, Steady ski

Longest Nordic session: Snow loop,
12 Jul, 1h, 12 km (snow)
Distance skied: 12 km (snow)
Distance skied: 8 km (roller)
Distance skied: 10 km (indoor)
Climbed: 90 m (roller)

Nordic skiing time: 2h30m

**Fun facts (rowing, descriptive)**
Max HR: 162 bpm, 12 Jul, Steady row

Longest row: Steady row, 12 Jul, 1h,
12 km (indoor), 3 of 4 sessions
Distance rowed: 24 km
(indoor, 2 of 3 sessions)
Distance rowed: 6 km (outdoor)

Rowing time: 2h30m (3 of 4 sessions)
```
