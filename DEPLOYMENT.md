# LUVTrader deployment guide

## Deployment audit result

- **Project type:** Plain static website
- **Actual frontend app folder:** repository root (`.`)
- **Vercel Root Directory:** `.`
- **Framework Preset:** Other / Static
- **Routing model:** Static homepage route (`/`), not React Router or Next.js file-based routing
- **Backend exists:** No backend code is present in this repository
- **Backend required for current deployment:** No

## Exact Vercel settings

| Setting | Value |
| --- | --- |
| Root Directory | `.` |
| Framework Preset | `Other` / `Static` |
| Install Command | Leave empty |
| Build Command | Leave empty |
| Output Directory | Leave empty |
| Node.js Version | Not required for the current static deployment |

The project root contains the production `index.html`, so Vercel should deploy the repository root directly. Do not set the root directory to `frontend`, `client`, `web`, `dist`, or any other folder unless the project structure changes later.

## Environment variables

No environment variables are required for the current static homepage.

If a backend/API is added later, deploy that backend separately and add a public frontend API URL only if browser code needs it. Do not commit private API keys, database URLs, trading-provider secrets, or LLM keys to this repository.

Example future frontend variable:

```text
LUVTRADER_API_BASE_URL=https://your-backend.example.com
```

## Backend deployment

No backend exists in this repository right now. If LUVTrader later needs server-side trading analysis, authentication, database access, or LLM calls, deploy that backend separately on a server platform such as Render, Railway, Fly.io, or Vercel Functions, then point the frontend to the deployed backend URL with an environment variable.

Never point production browser code at:

- `http://localhost:*`
- `http://127.0.0.1:*`
- a local MongoDB URL
- private backend secrets

## Local production test

From the repository root:

```bash
python3 -m http.server 4173
```

Then open:

```text
http://localhost:4173/
```

Verify:

1. The homepage loads.
2. Styling loads from `styles.css`.
3. The script loads from `script.js`.
4. Browser console has no missing asset errors.

## Redeploy steps

1. In Vercel, import or open the LUVTrader project connected to this repository.
2. Set **Root Directory** to `.`.
3. Set **Framework Preset** to **Other** or **Static**.
4. Leave **Install Command**, **Build Command**, and **Output Directory** empty.
5. Confirm no environment variables are required for the current static homepage.
6. Trigger **Redeploy** from the latest commit.
7. Open the assigned Vercel URL and verify `/` loads the LUVTrader homepage.

## If `404: NOT_FOUND` appears again

Check these items in order:

1. Vercel Root Directory must be `.`.
2. `index.html` must exist at the selected Vercel root.
3. Output Directory must be empty for this static root deployment.
4. Build Command must be empty unless a future build system is added.
5. The deployment must use the latest commit that includes `index.html`.

## Notes for future React/Vite migration

If LUVTrader is later converted to React + Vite, update the Vercel settings to:

- **Framework Preset:** Vite
- **Install Command:** `npm install`
- **Build Command:** `npm run build`
- **Output Directory:** `dist`

If that future app uses client-side routing, add a Vercel rewrite to send direct route requests to `/index.html`.
