# Season Report Examples

Synthetic fixtures only. Both examples use Sunday-start completed calendar weeks; the current partial week is excluded. Numbers are invented, not athlete data.

## Example 1: cycles, a phase gap and current snapshot

Eight completed weeks run from 17 May through 11 July. The first three ACWR values are unknown; the remaining five are 0.75, 0.90, 1.10, 1.30 and 1.40. The fictional dossier has no stated bottle.

The intensity values illustrate synthetic report_intensity_season selecting cycling across eight completed Sunday-start weeks, with 24/24 observed power sessions. Current 28-day cycling has 14/14 sessions across four rolling chunks. Each matched month selects cycling independently using the same mapping and settings: June has 12/12 sessions over five touched weeks on each side. Fetch completeness is unknown; all-sport hours are not intensity weights. These illustrations decode the file-level schema 2; counts do not imply exact covered dates.

```text
**Season report: Sun 17 May to Sat 11 July 2026**
Data updated: 14 Jul 15:30
History updated: 12 Jul 08:00

Eight completed weeks show consistent volume, with more training than last June.

**Position**
Season: Mid Season
Phase: Base, week 3
Previous phase: Deload

**Phases**
17 May-20 Jun: Build 4 weeks, Deload 1
21-27 Jun: no detected phase
28 Jun-11 Jul: Base 2 weeks

**Volume (8 completed weeks)**
Hours: 40h (avg. 5 h/week over 8 completed weeks)
TSS: 1880 (avg. 235/week over 8 completed weeks)
Longest ride: 2.75h, week of 28 Jun
Longest week: 6.5h, week of 21 Jun

**Fitness**
CTL peak: 44.2, week of 21 Jun
CTL now: 42.6, 14 Jul
ACWR below 0.8: 1
ACWR 0.8 through 1.3: 3
ACWR above 1.3 through 1.5: 1
ACWR known: 5 of 8 weeks

**Intensity**
Zones (cycling, power, 8/8 weeks; 24/24 sessions): Z1+Z2 92%, Z3 5%, Z4+ 3% (zone-time weighted)
TID 28d (now, cycling, power, 4/4 rolling weeks; 14/14 sessions): Pyramidal
Hard days: avg. 1.5/week over 8 completed weeks
First half (17 May-13 Jun): avg. 1.5 hard days/week
Second half (14 Jun-11 Jul): avg. 1.5 hard days/week
Weeks with a hard day: 8 of 8

**June 2026 (June 2025 in brackets)**
Hours: 23h (20h)
Apr-Jun monthly avg. hours: 21h (19h)
TSS: 1050 (900)
Apr-Jun monthly avg. TSS: 980 (870)
CTL peak: 44.2 (40.5)
CTL end: 43.8 (39.9)
Zones (cycling, power, 5/5 weeks; 12/12 sessions each side): Z1+Z2 90% (93%), Z3 6% (4%), Z4+ 4% (3%)
Hard days: June avg. 1.8/week (1.5/week)
Longest ride: 2.75h (2.5h)
HRV: June avg. 62 ms (59 ms)
RHR: June avg. 52 bpm (54 bpm)

**Notable**
Deviation: Z3 exceeded 5% in 3 of 8 completed weeks

**Fun facts (cycling, descriptive)**
Max power (1 s): 810 W, 27 May, Ridge circuit
Max HR: 181 bpm, 27 May, Ridge circuit

Longest ride: Meadow route, 28 Jun, 2h45m, 72 km (outdoor)
Distance: 250 km (indoor)
Distance: 530 km (outdoor)
Climbing: 700 m (indoor)
Climbing: 4300 m (outdoor)

Peak 5 s: 690 W, 27 May, Ridge circuit
Peak 1 min: 380 W, 27 May, Ridge circuit
Peak 5 min: 265 W, 25 Jun, Hill circuit
Peak 20 min: 225 W, 28 Jun, Meadow route
Peak 60 min: 200 W, 28 Jun, Meadow route

Time in the saddle: 37h

Work: 26000 kJ (energy of about 247.6 medium bananas)
Carbs used: 2200 g (about 81.5 medium bananas)
Most work in a day: 28 Jun, 2100 kJ, 180 g carbs
Most work in a week: 21 Jun to 27 Jun, 4500 kJ, 400 g carbs

**Interpretation**
Completed-week volume and the matched June comparison show a larger training base. Z3 is a recurring pattern to review, while three unknown ACWR weeks limit the load distribution summary. Current TID is a separate 28-day observation and does not establish a Season-wide intensity classification.
```

## Example 2: short history and partial power coverage

Two completed Sunday-start weeks are available. One ACWR value is 0.95; the other is unknown. There is no prior-year match. Only retained power and moving-time facts are supplied. This older history has no report_intensity_season block.

```text
**Season report: Sun 28 June to Sat 11 July 2026**
Data updated: 14 Jul 15:30
History updated: 12 Jul 07:00

Two completed weeks are available for a limited Season view.

**Position**
Phase: Base, week 2

**Phases**
28 Jun-4 Jul: Base 1 week
5-11 Jul: no detected phase

**Volume (2 completed weeks)**
Hours: 8h (avg. 4 h/week over 2 completed weeks)
TSS: 320 (avg. 160/week over 2 completed weeks)

**Fitness**
ACWR 0.8 through 1.3: 1
ACWR above 1.3: none
ACWR known: 1 of 2 weeks

**Intensity**
Season zones: unavailable, older history has no multisport intensity block

**Fun facts (cycling, descriptive)**
Max power (1 s): 540 W, 30 Jun, River path (stale, partial coverage: 1 of 2 expected rides, sampled 5 Jul)

Time in the saddle: 7h

**Interpretation**
The completed weeks support a volume summary, with only one known coupled ACWR value. No matched prior-year month is available, and the retained partial power observation is descriptive only.
```

Zero bins, empty Notable lines, absent equivalents and missing metrics are omitted. A phase gap is never bridged. Peaks live in Fun facts, not a separate Best efforts section.

## Synthetic seasonal selection and unmatched sports

In 24 completed weeks, cycling contributes 92% TSS/88% time with twenty 4.4-hour weeks. Four three-hour ski weeks supply 8% TSS/12% time and pass the guarded weekly-winner floor of 2.2 hours. Both sports are selected in report_intensity_season; current cycling primacy does not relabel the ski weeks. Every included observation contributes, even if its sport did not qualify in its own week.

```
Zones (cycling, power, 20/24 weeks; 60/60 sessions): Z1+Z2 90%, Z3 7%, Z4+ 3%
Zones (skiing, HR, 4/24 weeks; 12/12 sessions): Z1+Z2 85%, Z3 10%, Z4+ 5%
Skiing coverage: 4 active weeks; observed sessions only
```

A separate matched-month example has only cycling this year and only skiing last year. Show the independently selected union without pairing unlike sports:

```
Zones (cycling, power, 4 covered weeks; 8/8 sessions): Z1+Z2 90%, Z3 7%, Z4+ 3% (prior unavailable)
Zones (skiing, HR): unavailable (prior Z1+Z2 85%, Z3 10%, Z4+ 5%; 4 covered weeks, 8/8 sessions)
```

Missing sport evidence is not zero. With different mapping versions, show separate labelled observations and mark the comparison unavailable. Never add overlapping monthly tiers or classify Season from these distributions.
