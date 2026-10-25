# 7-day Report Template

**Window:** today and the preceding 6 local dates. Previous 7 days is the immediately preceding disjoint window. Use rolling_7d_chunks[0] and [1], never calendar-week rows. The configured week start still controls history, Season, phase detection and planned-week features.

## Template Structure

```text
**7-day report: [start] to [today]**
Data updated: [local timestamp]

[One-line summary]

Phase now: [current detected phase and supplied duration; state material uncertainty]
Sessions: [count]
[Sport]: [duration, sessions, TSS; one line per sport]
Hours: [current] (previous 7 days [previous])
TSS: [current] (previous 7 days [previous])
Plan followed: [nonzero followed, partly followed, not followed, planned without steps, no plan or unknown counts]

**Sessions**
[Day date]: [sport, name, duration, TSS, marker and optional short reason]

**Key session: [status emoji] [date, name]**
Matched window: [identified step/set and recording bounds]
Target: [prescribed power and duration]
Actual: [measured power and duration for that same window]
Power: [whole-session average and NP]
VI: [value]
HR: [average, maximum]
HRRc: [number and unit]

**Intensity and capability**
Zones ([sport], [basis], [covered/period weeks; covered/sport sessions]): [Z1+Z2 %, Z3 %, Z4+ %]
TID 7d ([sport], [basis], [coverage]): [supplied observed classification and PI]
TID 28d ([sport], [basis], [coverage]): [supplied observed classification]

Durability: [7-day avg, N; 28-day avg, N]
EF: [7-day avg, N; 28-day avg, N]
HRRc: [7-day avg, N; 28-day avg, N; numbers only]

**Fitness**
CTL: [current] (previous 7 days [previous])
ATL: [current] (previous 7 days [previous])
TSB: [current] (previous 7 days [previous])
Ramp rate: [supplied 7-day value]
ACWR: [supplied ratio and label]
Acute (7 days): [TSS]
Chronic (28-day avg per week): [TSS]
Recovery Index: [value]
Monotony: [only when above 2.3]
Strain: [only with monotony flag]

**Wellness**
HRV: [7-day avg, range, N days] (previous 7 days [avg])
RHR: [7-day avg, range, N days] (previous 7 days [avg])
Sleep: [7-day avg, range, N days] (previous 7 days [avg])
Sleep quality: [7-day avg, N days] (previous 7 days [avg])
Weight: [7-day avg, range, N weigh-ins] (previous 7 days [avg])
Feel: [7-day avg, N sessions] (previous 7 days [avg, N])
RPE: [7-day avg, N sessions] (previous 7 days [avg, N])

**Section 11 flags**
⚠️ [Title]
[Fact label]: [one fact per line]

⚠️ [Next title]
[Fact label]: [one fact per line]

**Fun facts (cycling, descriptive)**
[Groups below, with Peaks, without Most work in a week]

**Interpretation**
[2-4 sentences: what happened, meaning, material uncertainty]

**Next 7 days**
[Day date]: [sport duration, name; one planned item per line, no clock times]
```

## Sources and gates

Repeat intensity lines for every selected sport and actual basis/mapping, with covered/period weeks and covered/sport sessions. Weeks mean rolling chunks in current reports and configured weeks in Season/months; a covered week is not necessarily fully measured. Decode the file-level report_intensity_schema (2). Display keys of selected; sports[sport] supplies totals, active-week and zone columns, while zones[mapping] supplies three raw seconds and session/week counts. Show active-week counts and partial coverage without inferring exact covered dates. Resolve explicit rolling refs using the consuming chunk's dates, and monthly blocks by first occurrence in monthly_1y, monthly_2y, monthly_3y. Distinct mappings of the same basis stay separately labelled. Selected sports without zones get a short zones-unavailable line; pace/GAP is deferred. Missing report_intensity blocks mean unavailable; a present empty block is authoritative. Never use legacy primary/all-sport fields as fallback. Use ready-block tid[sport][mapping] percentages; for compact rows divide each bucket's raw seconds by their sum, never average percentages. Keep observed coverage and unknown activity-fetch completeness explicit.

`interval_data.plan_match` supplies timeline labels; `interval_data.compliance` summarizes gated Section 11 evidence from session_structure; `interval_data.icu_detected` is descriptive only. See [Which interval data to use](../../SECTION_11.md#which-interval-data-to-use).
For compliance, read the compact per-step rows with their evaluator, completion and availability; select main work from the authoritative prescription. Unlabelled lower-target rows are not automatic exclusions, and compressed-set totals are never an all-steps aggregate.

- Filter recent_activities to the exact local dates, count each ID once and sum moving_time_s and achieved TSS by sport. No planned TSS. Mark incomplete duration/TSS coverage. Phase is derived_metrics.phase_detection, still based on configured calendar weeks.
- Plan followed uses readable labels only: followed, partly followed, not followed, planned without steps, no plan, unknown. Omit zero categories. Never show not_assessed as a category and never conflate a known pairing with no plan. Pairing and duration come from plan_pairing for every sport; interval_data.plan_match supplies assessed step results. A no-step plan belongs in planned without steps even when its duration matches. Walk/Hike step assessment remains out of scope, but their pairing/duration can be shown. See [Which interval data to use](../../SECTION_11.md#which-interval-data-to-use).
- Anywhere a session line appears, use marker only, never status words: ✅ for followed; ⚠️ for partly followed; ❌ for not followed. A warning/failure gets a short supported reason, e.g. `(+1h10m)`, `(-20m)` or `(steps off)`. Paired no-step sessions of any sport use ✅ when plan_pairing.duration.within_tolerance is true, ⚠️ with delta when false; null gets no success/failure marker. There is no marker without a plan or for unassessed steps. Do not classify a step plan by duration alone.
- Keep available plan identity and planned/done duration in a short parenthesis, without status words. Use plan_pairing.plan.name and duration.planned_s, with interval_data.plan_match.plan.name and interval_data.plan_match.plan.duration_s as compatible captured detail. Omit each unavailable name/duration part. Do not repeat a plan name equal to the session name. Use ridden for rides, done for all non-rides. Never infer duration from a name. Examples: `Wed 8: Ride, Cadence practice, 1h, 50 TSS ✅ (Cadence endurance, planned 55m, ridden 1h)`; `Tue 14: Walk, Park walk, 30m, 10 TSS ✅ (planned 30m, done 30m)`. Paired unassessed steps may show plan name, with no verdict. See [Which interval data to use](../../SECTION_11.md#which-interval-data-to-use).
- Select the top 2-3 key sessions, prioritising notable sessions if four or more hard days occurred. Put the status emoji in the header. Matched window identifies exact steps/sets and bounds only, without raw method/status keys or "plan matched, followed". Read intervals.json by exact ID when has_structure and detail is needed. Never substitute whole-session average/NP for step Actual. Omit unavailable key-session rows.
- Retain producer gates and N: decoupling interpretation requires >=90 min and 0 < VI <=1.05, and no `decoupling_detail.comparability: plan_changes_power`; a flagged session keeps its value with "plan changes power" and no drift verdict. Name rising or falling power when detail says so; falling power with rising HR stays adverse coupling; EF requires cycling >=20 min, power+HR and the same VI gate. HRRc is numbers only, never trend words; 7-day avg needs N>=1 and 28-day avg N>=3. Interpretation mentions HRRc only if several sessions agree; harder output itself can lower HRRc.
- Zones and TID use derived_metrics.report_intensity_7d / report_intensity_28d, each period's selected map, tid percentages and sports coverage columns. Labels include sport, actual zone_basis/mapping and coverage; render the first three tid percentages as Z1+Z2/Z3/Z4+. Previous seven days uses rolling_7d_chunks[1].report_intensity, independently selected. Drift uses capability.report_intensity_comparison and its observed-session limits, never an unmatched or partial comparison. See [Report intensity source](../../SECTION_11.md#report-intensity-source). Capability uses durability, efficiency_factor and hrrc. No Best efforts or power/HR-curve block in this report; Peaks remain descriptive fun facts.
- Current fitness uses current_status.fitness and supplied load/recovery metrics. Previous endpoints need exact dated history, never invented CTL/ATL/TSB. Keep the coupled ACWR and readiness gates. Wellness uses each chunk.wellness for avg/range/day counts. Weight 7-day avg retains the four-observation gate. Feel/RPE use populated exact-window recent_activities with N (Feel 1 Strong to 5 Weak, RPE 1-10).
- Each Section 11 flag has its own ⚠️ title and fact lines, separated by a blank line. Z3 creep concerns sessions not planned as intensity: use plan_pairing.targets_intensity and z3_time.power_s / hr_s, not all Z3 in the week. Keep unknown intent unknown. When power and HR disagree strongly show both. With zone_reference, state its basis and supported threshold/environment, e.g. `Zones: power, from indoor FTP 260 W`; missing FTP/environment stays explicit. Do not apply one session's reference to others. Use `Cause: creep, or zones/FTP off` only when basis provenance is unavailable. Provenance does not establish the cause or validate zones. hard_day_details distinguishes days hard only via power Z3. No high-drift count flag.
- Next 7 days is tomorrow through today+7 from planned_workouts, in chronological order, one item per line: `Thu 16: Ride 3h, Endurance`. This rolling preview is not the next configured training week and does not establish a phase transition. Keep proposed transitions conditional on the supplied plan and its coverage; never treat them as completed work or use them to relabel the reported period. No clock times. Include a multi-day calendar entry when its inclusive date/end_date span overlaps that window, even if it started earlier; show it once with its full range, for example `Holiday - Off Season, 3–6 Nov`. HOLIDAY is a planned break, not illness or a training session; do not invent sport/duration for it. Missing end_date means a single-day entry.
- Fun facts source: latest.json.fun_facts.rolling_7d.

## Shared report rules

Read current source JSON in this response and the current official dossier for stable context; never reuse prior report values. Use local dates, a bold dated header and local Data updated. Keep a separate History updated timestamp when relevant. One fact per line, blank-line groups, no middle-dot separators, pipe joins or indented continuation lines. Previous values go in brackets. Every mean says avg and its window; show observation counts. Only the 28-day Fitness section uses start -> now lines. Omit missing or zero-only lines and empty sections, preserving a meaningful zero inside an otherwise populated comparison. Explain missing indispensable source blocks once; never invent observations or print placeholders.

Use supplied display values and formatted durations. Seconds-only durations may round to whole minutes (30 seconds up); decimal hours may remain decimal h. Eligibility always uses exact values. Readiness, formal compliance and progression gates in SECTION_11 are unchanged. A report marker is not formal adherence evidence.

### Fun facts contract

Place **Fun facts (cycling, descriptive)** immediately before **Interpretation**. Read the report-specific period object, never reconstruct facts from weekly compact caches. Observations are not tests, FTP/zone evidence or readiness evidence. Retain partial/stale coverage, date, activity name (ID if absent) and separate history freshness.

Use these blank-line groups, omitting unavailable components:
1. Max power (1 s), with date/name; Max HR, with date/name.
2. Longest ride, with date/name/duration and available distance; Distance for each nonzero environment; Climbing for each nonzero environment.
3. Peaks: one line each for 5 s, 1 min, 5 min, 20 min and 60 min, with date/name. Include only in 7-day and Season fun facts; the 28-day report has its separate Best efforts section.
4. Time in the saddle.
5. Work with its energy equivalent inline; Carbs used with its carbohydrate equivalent inline; Most work in a day with date, kJ and same-day carbs. Add Most work in a week only in 28-day and Season, retaining the supplied dates.

Use only Indoor and Outdoor as environment labels, solely from sync's indoor flag or emitted grouping. Never infer environment from names, source apps or platforms. Any indoor distance, speed or climbing outside the split also carries the indoor label. Format split facts as `Distance: 120 km (indoor)` and `Distance: 80 km (outdoor)`. Unknown environment is not Outdoor; state missing coverage when material. Use metres with explicit m if display conversion is unavailable. Omit a zero climbing side.

A clear current official dossier statement of positive grams carbohydrate per bottle is sufficient, whether in prose or the Tested training fuel table. For example, "My training bottle contains 90 g carbohydrate" establishes grams per bottle without needing a table. Never infer grams from bottle volume, a product name or a serving without a per-bottle statement. Ambiguous/conflicting statements do not establish a bottle.

Use the athlete's stated bottle; otherwise use the USDA medium-banana fallback: about 27 g carbohydrate and about 105 kcal per medium banana. Carbs equivalent = carbs_used / 27 or carbs_used / grams per bottle. Work equivalent = work_kj / 105 or work_kj / (4 * grams per bottle). Mechanical work of 1 kJ is approximately 1 kcal expended. This equivalence method note belongs only in the template, not in the report. Round counts to one decimal and say about: `Work: 3600 kJ (energy of about 10.0 of your 90 g bottles)`, `Carbs used: 900 g (about 10.0 of your 90 g bottles)`; fallback uses medium bananas. These are fun comparisons, not fueling advice or estimates of carbs eaten.
