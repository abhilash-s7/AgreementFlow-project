# Deploy AgreementFlow Live

This project is ready to deploy as one Python web service. The backend serves the vanilla frontend, so you do not need Vite, Node, or a separate static hosting service.

## Recommended: Render

1. Create a GitHub repository and upload this project folder.
2. Go to Render and create a new Blueprint from the repository.
3. Render will read `render.yaml`.
4. Wait for the deploy to finish.
5. Share the generated `https://your-service-name.onrender.com` URL with your friend.

The included `render.yaml` uses:

- Build command: `pip install -r requirements.txt`
- Start command: `uvicorn backend.main:app --host 0.0.0.0 --port $PORT`
- Health check: `/api/health`
- SQLite file path: `/var/data/database.db`
- Persistent disk mount: `/var/data`

## Demo Logins

Password for every account:

```text
password123
```

- `junior@agreementflow.local`
- `senior@agreementflow.local`
- `manager@agreementflow.local`
- `founder@agreementflow.local`
- `client@agreementflow.local`

## Local Run

```powershell
cd "C:\Users\indrajith\Documents\abhi project"
.\.venv\Scripts\Activate.ps1
python -m uvicorn backend.main:app --reload
```

Open:

```text
http://127.0.0.1:8000
```

## Temporary Free Demo Note

For a quick temporary demo, you can remove the `disk:` block and change `plan: starter` to `plan: free` in `render.yaml`. The app will still run, but SQLite data can reset when the service restarts or redeploys.

