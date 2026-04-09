# MITS Realtime Attendance Tracker

A Flask web application that tracks student attendance for Madanapalle Institute of Technology & Science (MITS). It scrapes the official MITS SIMS portal and provides attendance analysis with skip/attend recommendations to help students maintain the 75% threshold.

## Project Structure

```
attandancetracker/
  attandancetracker/
    telegrambot.py     # Main Flask application (all routes + logic)
    templates/
      index.html       # Main UI
      admin.html       # Admin panel
    static/
      js/app.js        # Frontend JavaScript
      manifest.json    # PWA manifest
      sw.js            # Service worker
  pyproject.toml       # Python dependencies (uv)
  uv.lock
```

## Tech Stack

- **Language**: Python 3.12
- **Framework**: Flask
- **Database**: PostgreSQL (Replit managed via DATABASE_URL / PG* env vars)
- **Scheduling**: APScheduler (daily Telegram updates at 8:30 AM IST)
- **Bot**: Telegram Bot API (optional, configure via TELEGRAM_BOT_TOKEN secret)
- **Production server**: Gunicorn

## Running the App

Workflow: `Start application`
Command: `cd attandancetracker/attandancetracker && python telegrambot.py`
Port: 5000

## Deployment

Configured for VM deployment (always-running) using gunicorn:
```
cd attandancetracker/attandancetracker && gunicorn --bind=0.0.0.0:5000 --reuse-port telegrambot:app
```

## Environment Variables

- `DATABASE_URL` — Replit-managed PostgreSQL connection string (auto-set)
- `PGHOST`, `PGPORT`, `PGDATABASE`, `PGUSER`, `PGPASSWORD` — Auto-set by Replit
- `TELEGRAM_BOT_TOKEN` — Optional: Telegram bot token for daily alerts

## Features

- Student login with MITS roll number + password
- Real-time attendance scraping from mitsims.in
- Per-subject attendance analysis with skip/attend recommendations
- 75% threshold tracking
- Telegram bot integration for daily 8:30 AM alerts
- PWA support (installable on mobile)
- Admin panel at /admin
- PDF/CSV export
