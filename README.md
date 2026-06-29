# AgreementFlow

AgreementFlow is a full-stack contract lifecycle management demo based on the supplied project brief. It uses a Python FastAPI backend, SQLite persistence, a vanilla HTML/CSS/JS frontend, role-based login, strict workflow guards, audit logs, client comments, revision resets, notifications, tracked versions, and DOCX export.

## Tech Stack

- Frontend: Plain HTML, CSS, and JavaScript. No Vite and no build step.
- Backend: Python 3, FastAPI, Uvicorn.
- Database: SQLite at `backend/database.db`, created automatically.
- DOCX export: `python-docx`.

## Run

```powershell
cd "C:\Users\Abhilash\Desktop\AgreementFlow"
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r backend\requirements.txt
python -m uvicorn backend.main:app --reload
```

Open:

```text
http://127.0.0.1:8000
```

## Make It Live

Use `DEPLOY.md` for the live deployment steps. The project includes `render.yaml`, `Procfile`, `runtime.txt`, and root `requirements.txt`, so it is ready to upload to GitHub and deploy as one Python web service.

## Demo Login

All demo accounts use this password:

```text
password123
```

- `junior@agreementflow.local`
- `senior@agreementflow.local`
- `manager@agreementflow.local`
- `founder@agreementflow.local`
- `client@agreementflow.local`

## Suggested Demo Flow

1. Log in as Junior, edit the draft, then submit to Senior.
2. Switch to Senior, review/edit, then approve for Manager.
3. Switch to Manager and approve for Founder.
4. Switch to Founder / Co-founder and dispatch to Client.
5. Switch to Client, add comments, then accept or request changes.
6. If changes are requested, the contract returns to Junior with a revision brief.

## Project Structure

```text
backend/
  __init__.py
  database.py
  docx_generator.py
  main.py
  requirements.txt
database d/
  C:\Users\Abhilash\Desktop\AgreementFlow\AgreementFlow-live-project\backend>
  sqlite3 database.db
  .tables
  select * from contracts;
frontend/
  app.js
  index.html
  styles.css
README.md
DEPLOY.md
Procfile
render.yaml
requirements.txt
runtime.txt
```

## API Overview

- `POST /api/auth/login`
- `POST /api/auth/logout`
- `GET /api/bootstrap`
- `POST /api/contracts`
- `PUT /api/contracts/{contract_id}`
- `POST /api/contracts/{contract_id}/advance`
- `POST /api/contracts/{contract_id}/return`
- `POST /api/contracts/{contract_id}/comments`
- `POST /api/contracts/{contract_id}/request-changes`
- `GET /api/contracts/{contract_id}/download`
- `POST /api/demo/reset`
