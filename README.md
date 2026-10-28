# AI Study Coach — Supabase edition

A Flask backend and Expo/React Native mobile app with study sessions, accounts, group collaboration, AI chat/plans, reminders, alarms, and monitoring routes.

- [Developer guide: environment, database setup, mobile integration, and deployment](docs/PROJECT_GUIDE.md)
- [Source, commands, configuration, and route reference](docs/REFERENCE.md)
- [Contributing](CONTRIBUTING.md)

`backend/app.py` is the current Supabase application. `backend/app_sqlite.py` is the older SQLite implementation. Configure the root `.env` and database schema before startup; the backend uses a server-only Supabase service key. The existing mobile config and legacy tests have known mismatches documented in the guide.

The SQL and setup guides record the schema's evolution; review them against your database rather than running all scripts indiscriminately. This project was designed for educational use as part of an internship program.

<!-- developer-handbook-20261028 -->
[Developer guide](docs/PROJECT_GUIDE.md) · [Source reference](docs/REFERENCE.md) · [Verification and operations](docs/OPERATIONS.md)
<!-- /developer-handbook-20261028 -->
