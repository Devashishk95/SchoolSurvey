# School Survey — Railway Deployment

This repository requires `app.py` and `static/survey.html` from the survey source package before it can run.

1. Deploy using Railway → New Project → Deploy from GitHub Repository.
2. Attach a persistent volume to the service, mounted at `/data` (before collecting responses).
3. Configure service variables:
   - `ADMIN_PASSWORD` = your unique strong password (never commit it)
   - `RESPONSES_FILE` = `/data/responses.csv`
   - `REQUIRE_RID` = `1` if respondent IDs are required
   - `REDIRECT_COMPLETE` and `REDIRECT_TERMINATE` = optional panel URLs with `{rid}` placeholder
4. Generate a public domain in Railway Networking.
5. Check `/?rid=TEST001` and `/admin` (username `admin`). Export via `/admin/export.csv`.

**Important**: The CSV must be on the persistent volume. Back it up. Respondent IDs are not cryptographically signed; server-side responses are not independently validated against all questionnaire logic.
