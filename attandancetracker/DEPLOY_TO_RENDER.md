# Deploy to Render

1. Push this repo to GitHub.
2. Go to Render and click **New +** → **Blueprint**.
3. Select the repository.
4. Render will read `render.yaml` and create the web service.
5. Add the environment variables from `render.env.example`.
6. Deploy.

## Required Environment Variables
- SESSION_SECRET
- SUPABASE_DB_HOST
- SUPABASE_DB_USER
- SUPABASE_DB_PASSWORD
- SUPABASE_DB_NAME
- SUPABASE_DB_PORT
- TELEGRAM_BOT_TOKEN

## Notes
- The app uses Supabase PostgreSQL.
- Telegram webhook is set automatically on startup using the public Render URL.
- The service binds to the Render-provided `PORT` environment variable.
