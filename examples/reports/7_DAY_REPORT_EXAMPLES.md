# 7-day Report Examples

Synthetic values only. Both examples end on Tuesday, independent of the configured week start. Example 1 renders every available template section. The synthetic dossier has no bottle statement, so its equivalents use the documented banana fallback.

## Example 1: mixed sports and plan evidence

Cadence endurance has no steps and a 3300-second plan; Park walk has no steps and a 1800-second plan. Both durations are within tolerance. Valley endurance is a paired step plan without an assessment. The partly-followed ride has observed off-target steps.

The revised intensity values illustrate supplied cycling-primary, power-basis blocks; the walk is excluded. The flagged session has a synthetic power/indoor/260 W zone_reference. These are invented source assumptions for the example, not recomputed athlete results.

```text
**7-day report: Wed 8 July to Tue 14 July 2026**
Data updated: 14 Jul 15:30

Three rides and one walk maintained a steady training rhythm.

Phase: Base, week 3
Sessions: 4
Ride: 4h30m (3 sessions, 225 TSS)
Walk: 30m (1 session, 10 TSS)
Hours: 5h (previous 7 days 4.75h)
TSS: 235 (previous 7 days 220)
Plan followed: 1 partly followed, 2 planned without steps

**Sessions**
Wed 8: Ride, Cadence practice, 1h, 50 TSS ✅ (Cadence endurance, planned 55m, ridden 1h)
Fri 10: Ride, Stepped endurance, 1h30m, 75 TSS ⚠️ (steps off)
Sun 12: Ride, Valley loop, 2h, 100 TSS (Valley endurance)
Tue 14: Walk, Park walk, 30m, 10 TSS ✅ (planned 30m, done 30m)

**Key session: ⚠️ Fri 10, Stepped endurance**
Matched window: step 2, recording seconds 1801 to 3600
Target: 190 W for 30m
Actual: 176 W over 1799 seconds
Power: 164 W average, 171 W NP
VI: 1.04
HR: 131 average, 163 maximum
HRRc: 31 bpm

**Intensity and capability**
Zones (cycling, power): Z1+Z2 91%, Z3 6%, Z4+ 3%
TID 7d (cycling, power): Pyramidal
TID 28d (cycling, power): Pyramidal

Durability: 7-day avg 3.1% (N=2), 28-day avg 3.3% (N=8)
EF: 7-day avg 1.30 (N=3), 28-day avg 1.28 (N=10)
HRRc: 7-day avg 31 bpm (N=1), 28-day avg 32 bpm (N=4)

**Fitness**
CTL: 42.6 (previous 7 days 42.1)
ATL: 44.0 (previous 7 days 45.0)
TSB: -1.4 (previous 7 days -2.9)
Ramp rate: 0.5 over 7 days
ACWR: 0.92 (optimal)
Acute (7 days): 235 TSS
Chronic (28-day avg per week): 256.25 TSS
Recovery Index: 0.93

**Wellness**
HRV: 7-day avg 63 ms, range 58-68 (7 days) (previous 7 days 62 ms)
RHR: 7-day avg 51 bpm, range 49-53 (7 days) (previous 7 days 52 bpm)
Sleep: 7-day avg 7.50h, range 7.0-8.0h (7 days) (previous 7 days 7.25h)
Sleep quality: 7-day avg 2.0/4 (7 days) (previous 7 days 2.1/4)
Weight: 7-day avg 68.2 kg, range 68.0-68.4 (6 weigh-ins) (previous 7 days 68.1 kg)
Feel: 7-day avg 2.0/5 (N=3) (previous 7 days 2.2/5, N=3)
RPE: 7-day avg 3.7/10 (N=3) (previous 7 days 3.8/10, N=3)

**Section 11 flags**
⚠️ Z3 in easy sessions
Session: 8 Jul, Cadence practice
Z3 by power: 18m
Z3 by HR: 2m
Zones: power, from indoor FTP 260 W

**Fun facts (cycling, descriptive)**
Max power (1 s): 715 W, 8 Jul, Cadence practice
Max HR: 176 bpm, 12 Jul, Valley loop

Longest ride: Valley loop, 12 Jul, 2h, 50 km (outdoor)
Distance: 60 km (indoor)
Distance: 50 km (outdoor)
Climbing: 600 m (outdoor)

Peak 5 s: 610 W, 8 Jul, Cadence practice
Peak 1 min: 350 W, 8 Jul, Cadence practice
Peak 5 min: 240 W, 10 Jul, Stepped endurance
Peak 20 min: 200 W, 12 Jul, Valley loop
Peak 60 min: 175 W, 12 Jul, Valley loop

Time in the saddle: 4h30m

Work: 3000 kJ (energy of about 28.6 medium bananas)
Carbs used: 250 g (about 9.3 medium bananas)
Most work in a day: 12 Jul, 1400 kJ, 120 g carbs

**Interpretation**
The stepped session's second window fell below target, while both no-step sessions stayed within their planned duration tolerance. Load stayed close to the previous seven days and recovery observations held. Power and HR disagree on easy-session Z3, so the cause remains uncertain.

**Next 7 days**
Wed 15: Ride 45m, Easy spin
Sat 18: Ride 1h45m, Lakeside endurance
```

## Example 2: sparse paired sessions

Recovery spin is a paired step plan without an assessment. Recovery roll has no steps but no available plan name or planned duration, so it has no duration verdict. Sync marks Easy spin indoor; names never determine environment.

```text
**7-day report: Wed 8 July to Tue 14 July 2026**
Data updated: 14 Jul 15:30

Two recorded rides retain plan intent with limited comparison data.

Sessions: 2
Ride: 40m (2 sessions, 22 TSS)
Hours: 0.67h
TSS: 22
Plan followed: 1 planned without steps

**Sessions**
Thu 9: Ride, Easy spin, 20m, 11 TSS (Recovery spin)
Sat 11: Ride, Recovery roll, 20m, 11 TSS (ridden 20m)

**Fun facts (cycling, descriptive)**
Longest ride: Easy spin, 9 Jul, 20m, 8 km (indoor)
Distance: 8 km (indoor)

Time in the saddle: 40m

**Interpretation**
Pairing identifies intent but does not establish execution quality. Missing power and wellness observations prevent a readiness or capability conclusion.
```

Missing comparisons, zero climbing, unavailable peaks, absent equivalents and unplanned upcoming sessions are omitted. No status word or inferred success marker appears in the sparse session lines.

## Runner intensity fragment

For a synthetic primary sport of run, the supplied HR-based primary block has z1_pct=75, z2_pct=15, z3_pct=10 and classification=Pyramidal. Cycling cross-training is excluded; the display expands the supplied run family to running:

```
Zones (running, HR): Z1+Z2 75%, Z3 15%, Z4+ 10%
TID 7d (running, HR): Pyramidal
```

If the primary block is missing, omit these lines and explain the missing intensity source when material. Never reuse a cycling label or all-sports share.
