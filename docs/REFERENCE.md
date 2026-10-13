# AI-Study-Coach- source reference


Source reviewed: [`6b5e6785864d`](https://github.com/noel-ult/AI-Study-Coach-/commit/6b5e6785864d6b0b4aa4dce8fd48e37e49f4c7a2).

This reference records the checked-in source, scripts, configuration names, and route declarations. It is a navigation aid; service availability and successful test execution require separate verification.

## Package commands

Run each command in the directory containing its package manifest. A declared script is not necessarily a passing check; guides call out placeholders and known mismatches.

### mobile-app/package.json

| Script | Shell command |
| --- | --- |
| `start` | `expo start` |
| `android` | `expo start --android` |
| `ios` | `expo start --ios` |
| `web` | `expo start --web` |

Manifest: [mobile-app/package.json](../mobile-app/package.json).

## Configuration names

Names below are declared by source or example files. Example-only entries may be stale; consult the linked reader and project guide before relying on them. Secret values are intentionally omitted.

| Name | Declared/read in |
| --- | --- |
| `API_PORT` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `DATABASE_URL` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `FLASK_DEBUG` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `FLASK_ENV` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `GROQ_API_KEY` | [backend/ai_service.py](../backend/ai_service.py) |
| `PORT` | [backend/app.py](../backend/app.py) |
| `SECRET_KEY` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `SUPABASE_ANON_KEY` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `SUPABASE_SERVICE_KEY` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |
| `SUPABASE_URL` | [.env.example](../.env.example), [backend/config.py](../backend/config.py) |

## HTTP route declarations

Paths are **as declared in each source file**. Router/blueprint mount prefixes from the entry point must be prepended; the project guide describes the active entry point and common prefixes. Alternate entry points (such as SQLite) are listed separately by file. Authentication, request bodies, and response schemas live in the linked handlers/models.

| Source | Method | Declared path | Handler |
| --- | --- | --- | --- |
| [backend/ai_routes.py](../backend/ai_routes.py) | POST | `/chat` | `chat` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/chat/history` | `chat_history` |
| [backend/ai_routes.py](../backend/ai_routes.py) | DELETE | `/chat/history` | `delete_chat_history` |
| [backend/ai_routes.py](../backend/ai_routes.py) | POST | `/study-plan` | `study_plan` |
| [backend/ai_routes.py](../backend/ai_routes.py) | POST | `/reminders` | `add_reminder` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/reminders` | `list_reminders` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/reminders/due` | `due_reminders` |
| [backend/ai_routes.py](../backend/ai_routes.py) | PUT | `/reminders/<int:reminder_id>` | `edit_reminder` |
| [backend/ai_routes.py](../backend/ai_routes.py) | PATCH | `/reminders/<int:reminder_id>/done` | `mark_done` |
| [backend/ai_routes.py](../backend/ai_routes.py) | DELETE | `/reminders/<int:reminder_id>` | `remove_reminder` |
| [backend/ai_routes.py](../backend/ai_routes.py) | POST | `/alarms` | `add_alarm` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/alarms` | `list_alarms` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/alarms/due` | `due_alarms` |
| [backend/ai_routes.py](../backend/ai_routes.py) | PUT | `/alarms/<int:alarm_id>` | `edit_alarm` |
| [backend/ai_routes.py](../backend/ai_routes.py) | PATCH | `/alarms/<int:alarm_id>/toggle` | `toggle` |
| [backend/ai_routes.py](../backend/ai_routes.py) | DELETE | `/alarms/<int:alarm_id>` | `remove_alarm` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/monitoring/metrics` | `metrics` |
| [backend/ai_routes.py](../backend/ai_routes.py) | GET | `/monitoring/logs` | `logs` |
| [backend/app.py](../backend/app.py) | GET | `/` | `index` |
| [backend/app.py](../backend/app.py) | GET | `/api/health` | `health_check` |
| [backend/app.py](../backend/app.py) | POST | `/api/auth/signup` | `signup` |
| [backend/app.py](../backend/app.py) | POST | `/api/auth/login` | `login` |
| [backend/app.py](../backend/app.py) | GET | `/api/auth/user/<user_id>` | `get_user` |
| [backend/app.py](../backend/app.py) | PUT | `/api/auth/user/<user_id>` | `update_user` |
| [backend/app.py](../backend/app.py) | POST | `/api/auth/change-password` | `change_password` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-sessions` | `log_study_session` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-sessions` | `get_study_sessions` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-sessions/<int:session_id>` | `get_study_session` |
| [backend/app.py](../backend/app.py) | PUT | `/api/study-sessions/<int:session_id>` | `update_study_session` |
| [backend/app.py](../backend/app.py) | DELETE | `/api/study-sessions/<int:session_id>` | `delete_study_session` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-insights` | `get_study_insights` |
| [backend/app.py](../backend/app.py) | GET | `/api/recommendations` | `get_recommendations` |
| [backend/app.py](../backend/app.py) | GET | `/api/enhanced-insights` | `get_enhanced_insights` |
| [backend/app.py](../backend/app.py) | GET | `/api/statistics` | `get_statistics` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups` | `create_group` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<user_id>` | `get_groups` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/details/<group_id>` | `group_details` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/join` | `join_study_group` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/leave` | `leave_study_group` |
| [backend/app.py](../backend/app.py) | PUT | `/api/study-groups/<group_id>` | `update_study_group` |
| [backend/app.py](../backend/app.py) | DELETE | `/api/study-groups/<group_id>` | `delete_study_group` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/tasks` | `create_group_task` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/tasks` | `get_tasks` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/tasks/<task_id>` | `get_task` |
| [backend/app.py](../backend/app.py) | PUT | `/api/study-groups/<group_id>/tasks/<task_id>` | `update_task_endpoint` |
| [backend/app.py](../backend/app.py) | DELETE | `/api/study-groups/<group_id>/tasks/<task_id>` | `delete_task_endpoint` |
| [backend/app.py](../backend/app.py) | PATCH | `/api/study-groups/<group_id>/tasks/<task_id>/complete` | `complete_task_endpoint` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/files` | `upload_group_file` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/files` | `get_files` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/files/<file_id>` | `get_file` |
| [backend/app.py](../backend/app.py) | DELETE | `/api/study-groups/<group_id>/files/<file_id>` | `delete_file_endpoint` |
| [backend/app.py](../backend/app.py) | PATCH | `/api/study-groups/<group_id>/files/<file_id>/download` | `download_file_endpoint` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/notes` | `create_group_note` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/notes` | `get_notes` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/notes/<note_id>` | `get_note` |
| [backend/app.py](../backend/app.py) | PUT | `/api/study-groups/<group_id>/notes/<note_id>` | `update_note_endpoint` |
| [backend/app.py](../backend/app.py) | DELETE | `/api/study-groups/<group_id>/notes/<note_id>` | `delete_note_endpoint` |
| [backend/app.py](../backend/app.py) | PATCH | `/api/study-groups/<group_id>/notes/<note_id>/pin` | `toggle_note_pin` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/activities` | `get_activities` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/activities/user` | `get_user_activities_endpoint` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/study-hours/log` | `log_group_study_session` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/study-hours/stats` | `get_group_stats` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/study-hours/member` | `get_member_hours` |
| [backend/app.py](../backend/app.py) | POST | `/api/study-groups/<group_id>/study-hours/goals` | `set_group_study_goals` |
| [backend/app.py](../backend/app.py) | GET | `/api/study-groups/<group_id>/study-hours/progress` | `get_study_goals_progress` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/` | `index` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | POST | `/api/study-sessions` | `log_study_session` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/api/study-sessions` | `get_study_sessions` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/api/study-insights` | `get_study_insights` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/api/study-recommendations` | `get_study_recommendations_endpoint` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/api/study-predictions` | `get_study_predictions` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | POST | `/api/mobile/login` | `mobile_login` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/api/mobile/stats` | `mobile_stats` |
| [backend/app_sqlite.py](../backend/app_sqlite.py) | GET | `/api/mobile/study-groups` | `mobile_study_groups` |

## Existing documentation

Historical plans/reports describe their own revision; use current source when they disagree.

- [ARCHITECTURE.md](../ARCHITECTURE.md)
- [AUTH_SETUP_GUIDE.md](../AUTH_SETUP_GUIDE.md)
- [DATABASE_TABLES_GUIDE.md](../DATABASE_TABLES_GUIDE.md)
- [ENHANCED_FEATURES_SUMMARY.md](../ENHANCED_FEATURES_SUMMARY.md)
- [FEATURES_IMPLEMENTED.md](../FEATURES_IMPLEMENTED.md)
- [FIXES_SUMMARY.md](../FIXES_SUMMARY.md)
- [IMPLEMENTATION_SUMMARY.md](../IMPLEMENTATION_SUMMARY.md)
- [MIGRATION_SUMMARY.md](../MIGRATION_SUMMARY.md)
- [NEW_FEATURES_SUMMARY.md](../NEW_FEATURES_SUMMARY.md)
- [QUICKSTART.md](../QUICKSTART.md)
- [README.md](../README.md)
- [STARTUP_CHECKLIST.md](../STARTUP_CHECKLIST.md)
- [STUDY_GROUPS_MIGRATION.md](../STUDY_GROUPS_MIGRATION.md)
- [STUDY_HOURS_GUIDE.md](../STUDY_HOURS_GUIDE.md)
- [SUPABASE_QUICKSTART.md](../SUPABASE_QUICKSTART.md)
- [SUPABASE_SETUP.md](../SUPABASE_SETUP.md)
- [backend/requirements.txt](../backend/requirements.txt)
- [mobile-app/MOBILE_README.md](../mobile-app/MOBILE_README.md)
- [mobile-app/README.md](../mobile-app/README.md)
- [mobile-app/assets/README.md](../mobile-app/assets/README.md)

## Source and configuration map

Generated lockfiles, binary assets, compiled output, vendored dependencies, and cached bytecode are omitted. Test files remain listed so coverage can be located.

- [.env.example](../.env.example)
- [backend/ai_routes.py](../backend/ai_routes.py)
- [backend/ai_service.py](../backend/ai_service.py)
- [backend/alarms_service.py](../backend/alarms_service.py)
- [backend/app.py](../backend/app.py)
- [backend/app_sqlite.py](../backend/app_sqlite.py)
- [backend/auth_service.py](../backend/auth_service.py)
- [backend/config.py](../backend/config.py)
- [backend/database_service.py](../backend/database_service.py)
- [backend/enhanced_analyzer.py](../backend/enhanced_analyzer.py)
- [backend/monitoring_service.py](../backend/monitoring_service.py)
- [backend/recommendation_engine.py](../backend/recommendation_engine.py)
- [backend/reminders_service.py](../backend/reminders_service.py)
- [backend/requirements.txt](../backend/requirements.txt)
- [backend/study_analyzer.py](../backend/study_analyzer.py)
- [backend/study_group_activities_service.py](../backend/study_group_activities_service.py)
- [backend/study_group_files_service.py](../backend/study_group_files_service.py)
- [backend/study_group_notes_service.py](../backend/study_group_notes_service.py)
- [backend/study_group_study_hours_service.py](../backend/study_group_study_hours_service.py)
- [backend/study_group_tasks_service.py](../backend/study_group_tasks_service.py)
- [backend/study_groups_service.py](../backend/study_groups_service.py)
- [backend/supabase_client.py](../backend/supabase_client.py)
- [backend/test_study_coach.py](../backend/test_study_coach.py)
- [backend/test_study_hours.py](../backend/test_study_hours.py)
- [backend/validation_utils.py](../backend/validation_utils.py)
- [database/add_study_goals.sql](../database/add_study_goals.sql)
- [database/add_study_groups.sql](../database/add_study_groups.sql)
- [database/ai_features.sql](../database/ai_features.sql)
- [database/drop_tables.sql](../database/drop_tables.sql)
- [database/fix_ai_fk_constraints.sql](../database/fix_ai_fk_constraints.sql)
- [database/fix_schema.sql](../database/fix_schema.sql)
- [database/schema.sql](../database/schema.sql)
- [database/study_groups_enhanced.sql](../database/study_groups_enhanced.sql)
- [database/verify_schema.sql](../database/verify_schema.sql)
- [demo_enhanced_features.py](../demo_enhanced_features.py)
- [generate_secret_key.py](../generate_secret_key.py)
- [migrate_to_supabase.py](../migrate_to_supabase.py)
- [mobile-app/app.json](../mobile-app/app.json)
- [mobile-app/app/_layout.js](../mobile-app/app/_layout.js)
- [mobile-app/app/ai-chat.js](../mobile-app/app/ai-chat.js)
- [mobile-app/app/dashboard.js](../mobile-app/app/dashboard.js)
- [mobile-app/app/groups.js](../mobile-app/app/groups.js)
- [mobile-app/app/index.js](../mobile-app/app/index.js)
- [mobile-app/app/reminders.js](../mobile-app/app/reminders.js)
- [mobile-app/app/settings.js](../mobile-app/app/settings.js)
- [mobile-app/app/signup.js](../mobile-app/app/signup.js)
- [mobile-app/babel.config.js](../mobile-app/babel.config.js)
- [mobile-app/config.js](../mobile-app/config.js)
- [mobile-app/eas.json](../mobile-app/eas.json)
- [mobile-app/package.json](../mobile-app/package.json)
- [render.yaml](../render.yaml)
- [test_api.py](../test_api.py)
- [test_enhanced_analyzer.py](../test_enhanced_analyzer.py)
- [test_supabase.py](../test_supabase.py)
