# Interlude Studios — Fan Page Portal

A self-hosted TikTok fan page tracking dashboard with daily automated scraping via GitHub Actions.

## Setup

1. Push this folder to a new GitHub repository
2. In the repo settings, add a secret: `RAPIDAPI_KEY` (your RapidAPI key for `tiktok-scraper7`)
3. Enable GitHub Pages → deploy from the `main` branch root
4. The portal will auto-update every day at 9am ET

## Adding a Campaign

Create a new `.json` file in `/projects/`:

```json
{
  "id": "my-campaign",
  "name": "Artist Name — Campaign",
  "description": "Short description",
  "status": "active",
  "platform": "tiktok",
  "accounts": ["account1", "account2"],
  "tags": ["fan-pages", "edm"],
  "created": "2026-03-18",
  "team": ["Omid"]
}
```

Then either push to trigger the next daily run, or manually trigger the workflow from the Actions tab.

## Running Locally

```bash
pip install requests openpyxl
export RAPIDAPI_KEY=your_key_here
python scraper.py                        # scrape all active projects
python scraper.py --project my-campaign # scrape one project
python scraper.py --generate-only       # rebuild HTML only (no API calls)
python scraper.py --export-xlsx         # also export Excel files
```
