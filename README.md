# LUVTrader

LUVTrader is currently configured as a plain static website that can be deployed directly from the repository root on Vercel.

## Project type

- **Type:** Plain static website
- **Frontend root:** `.`
- **Routing:** Static homepage (`/`)
- **Backend dependency:** None required for the current homepage

## Vercel quick settings

- **Root Directory:** `.`
- **Framework Preset:** Other / Static
- **Install Command:** leave empty
- **Build Command:** leave empty
- **Output Directory:** leave empty

The production homepage is `index.html` in the repository root, so Vercel can serve it without a build step.

## Local preview

Open `index.html` directly in a browser, or run a static server from this folder:

```bash
python3 -m http.server 4173
```

Then visit `http://localhost:4173/`.

## Deployment documentation

See [DEPLOYMENT.md](./DEPLOYMENT.md) for the complete deployment audit, Vercel settings, environment variables, and troubleshooting steps.
