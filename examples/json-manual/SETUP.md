# Manual JSON Export

Export Intervals.icu data locally for different time ranges.

## Prerequisites

- Python 3.8+
- `requests` library: `pip install requests`
- [Intervals.icu](https://intervals.icu) account with training data

## First-Time Setup

Download sync.py from the [Section 11 repository](https://github.com/CrankAddict/section-11/tree/main/examples):

```bash
curl -O https://raw.githubusercontent.com/CrankAddict/section-11/main/examples/sync.py
```

Then configure your credentials:

```bash
python3 sync.py --setup
```

Enter your Intervals.icu credentials when prompted. Config saves to `.sync_config.json`.

**Finding your credentials:**
- **Athlete ID**: Intervals.icu → Settings → bottom of page (e.g., `i123456`)
- **API Key**: Intervals.icu → Settings → Developer Settings → API Key

## Usage

### Export to local file

```bash
# Last 7 days (default)
python3 sync.py --output latest.json

# Last 14 days
python3 sync.py --days 14 --output 14days.json

# Last 90 days
python3 sync.py --days 90 --output 90days.json
```

### Common time ranges

| Days | Use case |
|------|----------|
| 7 | Weekly review |
| 14 | Two-week block |
| 42 | 6-week training block |
| 90 | Quarterly / build cycle |
| 180 | Season review |

### Repository delivery

Use [GitHub sync](../json-auto-sync/SETUP.md) or [On-demand sync](../json-on-demand/SETUP.md) for repository delivery through the shared workflow. The legacy direct API publisher is not one of the four supported setup paths.

## Generated Files

The script creates/maintains these files:

| File | Purpose | When created |
|------|---------|--------------|
| `latest.json` | Training data export | Every run with `--output` |
| `history.json` | Longitudinal data: daily (90d), weekly (180d), monthly (3y) | First run, regenerates when outdated |
| `intervals.json` | Per-interval data for structured sessions | Every run (incremental, 14-day retention) |
| `routes.json` | Route/terrain data for events with GPX/TCX attachments | When attachments exist |
| `saved_workouts.json` | Read-only mirror of the athlete's Intervals.icu saved workouts | First run, then on its own 6-hour refresh throttle |
| `ftp_history.json` | FTP progression tracking | Automatically on first run |
| `route_eta_history.json` | Retained 180-day outdoor ETA calibration | Normal sync/history updates |
| `maps/weather/` | Up to four ordered PNG pages per ride, six rides (24 pages), for chat | Fresh eligible route-weather briefs |
| `.sync_config.json` | Your credentials + preferences (local only) | After `--setup` |

### FTP History

`ftp_history.json` tracks indoor and outdoor FTP changes over time. Updated automatically when FTP changes. Used to calculate **Benchmark Index** (8-week FTP progression). Keep this file if you want continuous tracking. See [auto-sync SETUP](../json-auto-sync/SETUP.md#ftp-history-tracking) for details on the Benchmark Index.

### History Data

`history.json` provides longitudinal context with tiered granularity:

| Tier | Granularity | Range |
|------|-------------|-------|
| `daily_90d` | Day-by-day | Last 90 days |
| `weekly_180d` | Week-by-week | Last 180 days |
| `monthly_1y/2y/3y` | Month-by-month | Up to 3 years |

Also includes period summaries, FTP timeline, and data gap detection. Generated automatically on first run and regenerated when outdated.

## What's Included

The export includes pre-calculated **derived metrics** for Section 11 compliance. AI should use these, not calculate its own. Key metrics: ACWR, Recovery Index, Monotony/Strain, Grey Zone %, Quality Intensity %, Easy Time Ratio, Benchmark Index, Phase Detection, Seiler TID, Aggregate Durability, and TID Drift.

See [examples/README.md](../README.md#derived-metrics) for the full derived metrics table.

## Use with AI

**Calendar naming:** To let the calendar support a deload week, name its sessions with "Deload" or "Recovery week", for example "Recovery week - easy ride". Single recovery rides inside normal weeks are not read as a deload week. Names support the phase assessment; they do not establish it on their own.

Date-only/exact-midnight workouts use labelled 10:00 local by default. Optional `route_weather_default_start` in the existing config or `SECTION11_ROUTE_WEATHER_DEFAULT_START` in the export environment changes it. The AI asks for the actual start or asks you to set it in Intervals.icu; the next normal export picks it up. See [departure handling](../../README.md#route-weather-departure). The overview sits directly after READ_THIS_FIRST, or first when absent.

No extra Manual export steps are needed for 11.80. Sync writes companions next to the latest export, including when `--output` names another directory; retain that folder between exports. The AI reads `latest.json.data_overview` first for presence, file-write times, relative locations and per-ride route/weather/map status. Resolve paths against that export's source; if uploads lose folders, match filenames and verify brief binding. The AI reads and shows matching PNG pages in their listed order only if it can already access them; missing pages remain explicit. Otherwise use the text brief, never describe an unseen map or ask the user to download/upload one. Maps are not part of the download artifact ZIP. Weather times use local zone labels and compass directions.

**Option 1: Upload files**: Upload `latest.json` and `history.json` to your AI platform for a complete analysis with longitudinal context. Upload `intervals.json` when you want detailed post-workout analysis of structured sessions. Upload `routes.json` (if present) when you want terrain-aware coaching for planned events. Upload `saved_workouts.json` on demand, when you want to select, reuse, or discuss one of your saved workouts.

**Option 2: Repository delivery**: Follow the GitHub or On-demand setup above, then the [main README setup guide](../../README.md#web-chat-setup) for configured AI access.

**Option 3: Use with agentic platforms**: Claude Code, Claude Cowork, OpenAI Codex CLI, Gemini CLI, OpenClaw, and Hermes read files directly from whatever filesystem their runtime can reach; where that runtime is the machine holding your exported files, no GitHub is needed. Point the agent at the folder containing your exported JSON files. Grok Bot is **experimental** and its filesystem is provider-hosted, so the data reaches it by connector or authenticated repository rather than from your disk; capability class is not a support promise. See the [agentic setup guide](../../README.md#agentic-setup).

### Automate it

Want sync.py to run automatically on a timer? See [json-local-sync](../json-local-sync/SETUP.md).

---

## Options Reference

| Flag | Description | Default |
|------|-------------|---------|
| `--setup` | Run setup wizard | - |
| `--days N` | Days of data to export | 7 |
| `--output FILE` | Save to local file | - |
| `--week-start DAY` | Training week start day (mon/tue/wed/thu/fri/sat/sun) | mon |
| `--debug` | Show API field debug info | off |

**Note:** `--week-start` can also be set in `.sync_config.json` (`"week_start": "sun"`) or via `WEEK_START` environment variable. Config file setting persists across runs: no need to pass the flag every time.

**Note:** Only `metadata.athlete_id` is redacted. The output is not anonymized. See [Privacy & Security](../../README.md#privacy--security).

---

## Troubleshooting

### "Config not found" error
Run `python3 sync.py --setup` first.

### Empty or missing data
- Check your API key is valid
- Verify you have activities in the requested date range
- Run with `--debug` to see API responses

### FTP history not updating
FTP history only adds entries when FTP **changes**. If your FTP is the same, no new entry is added.

For general AI platform issues (data not fetching, AI fabricating metrics, connector problems), see the [main README troubleshooting guide](../../README.md#troubleshooting).
