# AI Study Coach — Supabase edition

A Flask backend and Expo/React Native mobile app with study sessions, accounts, group collaboration, AI chat/plans, reminders, alarms, and monitoring routes. `backend/app.py` is the Supabase entry point; `app_sqlite.py` preserves the older SQLite demonstration.

## Configuration and database preparation

Copy root `.env.example` to `.env`. `backend/config.py` loads that exact root file with override enabled, so its values can supersede shell values. Configure `SUPABASE_URL`, `SUPABASE_ANON_KEY`, `SUPABASE_SERVICE_KEY`, `DATABASE_URL`, and a random `SECRET_KEY`. Although validation omits the service key, `supabase_client.py` actually constructs the backend client with it. Keep the service key only on the server.

Set `API_PORT=5000` for local development. `PORT` overrides it when running `app.py`; `FLASK_DEBUG=True` is case-sensitive in this configuration. Use `FLASK_DEBUG=False` for a shared deployment. `GROQ_API_KEY` is used by AI services.

The `database/` directory contains the base schema, study-group/AI additions, and historical fixes. Review `SUPABASE_SETUP.md`, `DATABASE_TABLES_GUIDE.md`, and the SQL files against a disposable project's existing schema before applying them. These are not an automatically ordered migration chain; `drop_tables.sql` is destructive. Do not run every SQL file alphabetically against an existing project.

## Run

```sh
python3 -m venv .venv
.venv/bin/pip install -r backend/requirements.txt
.venv/bin/python backend/app.py
```

In another terminal:

```sh
cd mobile-app
npm install
npm start
```

`mobile-app/config.js` currently targets a hosted backend. For local work, point it at your machine's LAN address on port 5000; confirm that every endpoint matches the selected backend edition. The file retains legacy mobile/session/recommendation routes absent from the current Supabase app, so the existing client/server integration has known mismatches.

## Architecture and contracts

`app.py` coordinates account/session/group operations through service modules. `ai_routes.py` mounts under `/api/ai` and delegates AI chat, reminders, alarms, and monitoring. Group tasks/files/notes/activities/study-hours each have a dedicated service. Persistence is through the server Supabase client; see the route reference and database guides for the corresponding contracts.

Do not infer authorization solely from the presence of login endpoints: audit each route's caller identity and resource ownership before deploying with real users, especially when service-role access is used. This documentation does not certify the existing access controls.

## Tests and deployment

`render.yaml` runs Gunicorn from `backend/`. Its commented environment list omits `DATABASE_URL`, which current startup validation still requires. Configure that variable as well. Mobile builds are configured by `mobile-app/eas.json`.

`backend/test_study_coach.py` still imports SQLite-specific `db` and `StudySession` from `app`, which the Supabase entry no longer exports. Treat it as a legacy test, not a passing suite for this edition. Integration scripts such as `test_supabase.py` need a disposable Supabase project and may write data. Validate health, signup/login, a session, and group ownership with isolated accounts before relying on the deployment.

## More documentation

- [Source, command, and configuration reference](REFERENCE.md)
- [Contributing](../CONTRIBUTING.md)
