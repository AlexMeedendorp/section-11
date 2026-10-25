# 28-day Report Template

**Window:** today and the preceding 27 local dates. Use only latest.json.rolling_7d_chunks: four supplied disjoint windows, newest first. Display oldest first (4, 3, 2, 1), each as its own dated block. Chunk 1 equals the 7-day report window. Never compute, shift, reconstruct, backfill or substitute calendar weeks. If these chunks are missing/inconsistent, explain the unavailable breakdown and request a compatible current export.

## Template Structure

```text
**28-day report: [chunk 4 start] to [chunk 1 end]**
Data updated: [local timestamp]

[One-line summary]

Phase now: [current detected phase and supplied duration; state material uncertainty]

**Totals**
[Sport]: [time, sessions, TSS; one line per sport]
Total: [time, sessions, TSS]

**Plan**
Rides: [paired of recorded rides] planned ✅
[Other sport plural]: [paired of recorded sessions] planned [✅ only when all paired]
Checked against plan: [followed of assessed sessions] followed [✅ only when all followed]

**Fitness (start of period -> now)**
CTL: [start] -> [now] ([signed delta])
ATL: [start] -> [now] ([signed delta])
TSB: [start] -> [now] ([signed delta])

**[Chunk 4 dates]**
Hours: [supplied hours]
TSS: [supplied TSS]
CTL: [supplied end CTL]
Zones: [Coggan Z1+Z2 %, Z3 %, Z4+ %, basis]
Hard days: [count, dates and supported names/reasons]
Durability: [7-day avg, N]
EF: [7-day avg, N]
HRRc: [7-day avg, N]
HRV: [7-day avg, N days]
RHR: [7-day avg, N days]
Sleep: [7-day avg, N days]

[Repeat one dated block for chunks 3, 2, 1 in order]

**Wellness (28 days)**
HRV: [28-day avg, N days]
RHR: [28-day avg, N days]
Sleep: [28-day avg, N days]
Sleep quality: [28-day avg, N days]
Weight: [latest, date] (28-day avg. [mean], [N] weigh-ins)
Weight trend: [supplied kg/week slope]
Feel: [28-day avg, N sessions]
RPE: [28-day avg, N sessions]

**Intensity**
TID 28d: [supplied Seiler classification, PI, basis]

**Key sessions**
**[Status emoji] [date, name]**
Target: [identified step/set prescription]
Actual: [same-window observed power and duration]

Long ride: [date, name, duration, supported observation]
Tempo whole-ride decoupling: [dated series, each eligible whole-ride value; mark plan_changes_power values "plan changes power"]

**Best efforts (last 28 days, previous 28 days in brackets)**
5 s: [W, date] ([previous W])
1 min: [W, date] ([previous W])
5 min: [W, date] ([previous W])
20 min: [W, date] ([previous W])
60 min: [W, date] ([previous W])
HR [duration]: [current bpm] ([previous bpm])
Shift: [plain words describing the observed change]

**DFA a1 (28 days)**
DFA a1: [28-day avg]
Drift: [28-day avg, eligible N]
Sessions: [sufficient N and available coverage]
Easy-state guard: [eligible estimate and N, descriptive]
[LT1/LT2 only when an estimate exists]

**Section 11 flags**
⚠️ [Title]
[Fact label]: [one fact per line]

**Fun facts (cycling, descriptive)**
[Groups below, without Peaks, with Most work in a week]

**Interpretation**
[Paragraph 1: what happened across the rolling period]

[Paragraph 2: meaning, uncertainty and supported implication]
```

## Sources and gates

`interval_data.plan_match` supplies timeline labels; `interval_data.compliance` summarizes gated Section 11 evidence from session_structure; `interval_data.icu_detected` is descriptive only. See [Which interval data to use](../../SECTION_11.md#which-interval-data-to-use).
For compliance, read the compact per-step rows with their evaluator, completion and availability; select main work from the authoritative prescription. Unlabelled lower-target rows are not automatic exclusions, and compressed-set totals are never an all-steps aggregate.

- Totals by sport use exact-window recent_activities, distinct IDs, moving_time_s and achieved TSS. Total hours/TSS must reconcile with the four supplied chunks, allowing display rounding. Do not reconstruct chunk metrics from activities or history. Missing metrics remove their own lines, not other supplied observations.
- Pairing comes from plan_pairing for every sport. "Rides: 12 of 12 planned ✅" counts paired activities, not adherence. Checked against plan includes assessed step statuses and paired no-step activities with a non-null duration result; only followed steps or within-tolerance no-step durations contribute to its followed numerator. Do not substitute a duration check for a structured plan assessment. Exclude unassessed/unknown results from the checked denominator; never show not-assessed counts. Explain material retained-step coverage without inventing assessments: full detail remains 14 days; older step results are last captured. Pairing identity/duration refresh across 28 days.
- Fitness uses exact dated start-of-period and current CTL/ATL/TSB. Start -> now is allowed here. If the start is missing, show only the dated current value. No seven-day ramp, FTP, eFTP, W/kg, ceilings or separate progression section.
- Each chunk's hours, TSS, ctl_end, zone_distribution, hard_days, hard_day_details, capability means/N and wellness are supplied. Normalize zone hours only against the supplied total. Never infer Seiler TID from Coggan zones. Hard-day reasons use actual rung/basis: e.g. "Hard days: 3 (10 Jul intervals; 12 and 13 Jul by power Z3 only)" only when hard_day_details supports that distinction. No reclassification; unknown plan intensity stays unknown.
- Chunk Durability/EF/HRRc say 7-day avg and N. HRRc only when present, numbers only, no trend words. All producer eligibility gates and per-session decoupling >=90 min/VI <=1.05 and EF cycling >=20 min/power+HR/VI <=1.05 gates remain. A per-session value with `decoupling_detail.comparability: plan_changes_power` stays in the series, marked "plan changes power", without a drift verdict or trend claim from that value; chunk Durability means are unchanged.
- Wellness uses latest.json.wellness_28d, not seven-day wellness_data or a mean of chunk means. Each metric's own observed-day count is authoritative. Weight uses weight_kg.avg/days/latest/latest_date with display conversion; keep the existing current_status.weight slope gate independently. Feel/RPE use available exact-window recent_activities with N; no missing values become zero.
- Intensity uses derived_metrics.seiler_tid_28d with its basis. Phase is current derived_metrics.phase_detection only, still based on configured calendar weeks.
- Key-session header markers and plan identity follow 7_DAY_REPORT_TEMPLATE.md. Use exact identified target/actual windows. Long-ride observations and a tempo whole-ride decoupling series remain clearly distinct from main-set measures. No invented target power from session average/NP.
- Best efforts uses supplied capability.power_curve_delta current/previous anchor watts and hr_curve_delta with their own window. Attribute current dates from matching exact fun_facts.rolling_28d.peaks or exact activity observations; do not attach a date to a different maximum. Missing previous values remove only the bracket. Dates absent from the source are omitted, not guessed. Shift uses words, no percentages or rotation scores.
- Flags follow the 7-day per-flag layout and Z3 intent/basis rules. No high-drift count flag.
- Fun facts source: latest.json.fun_facts.rolling_28d. Most work in a week is the supplied rolling chunk and its dates, never a calendar week. Peaks are omitted here.

## DFA a1 eligibility

Use derived_metrics.capability.dfa_a1_profile_28d, alongside (not in place of) the existing latest-seven-sufficient profile. The 28-day field uses available retained compact summaries with the same eligibility and no backfill. State material incomplete coverage; do not imply 28 full days of recording. Require the cycling block and validated=true.

Show 28-day avg and sufficient n_sessions when supplied, regardless of whether a marker estimate exists. Drift uses drift_delta_mean and drift_sessions only; null is not zero, and numerical eligibility alone does not prove physiological drift or steady workload. Show an easy_guard_estimate whenever present, independent of the coarse confidence field. The easy-state guard at α1 1.0 is descriptive compliance context, NEVER threshold calibration. Include HR and only populated environment values with their own N.

Omit no-estimate LT1/LT2 lines. Existing estimate gates remain authoritative: crossing_sessions means dwell-qualified, eligible_sessions also passed stationarity/quality gates, and estimates require eligible depth. An emitted LT1/LT2 estimate can be shown descriptively; LT1 has no configured comparator. Any separately requested LT2 comparison still requires its estimate, matching depth >=4 (including lt2_estimate.n_sessions_indoor for indoor watts) and configured comparator. No automatic threshold update or progression decision follows. Diagnostic eligibility blockers may be explained when material; they never become pseudo-estimates.

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
