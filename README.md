# trading_public

Read-only dashboard (GitHub Pages) + Render keep-alive. **No secrets, keys or backend code belong here.**

## Setup
1. Edit `config.js`: set `API_URL` to the Render URL of `trading_private` (public, non-secret). The backend allows CORS only from `https://esrimova.github.io`.
2. Settings -> Pages -> deploy from `main` branch, root.
3. Settings -> Secrets and variables -> Actions -> **Variables** -> `BACKEND_URL` = same Render URL.

## Keep-alive (RF-09) - known ceiling
`.github/workflows/keepalive.yml` pings `/health` every 14 minutes. Render Free spins down after 15 min without traffic, so this is the
agreed mechanism but **not guaranteed**: GitHub may delay or drop scheduled runs (especially at the top of the hour), and scheduled workflows
in public repos are **disabled after 60 days without repository activity** (re-enable in the Actions tab or push a commit).
Render staff have said on the community forum that pinging free services to keep them awake may be considered abuse; this is not stated in the docs.

## Dashboard
Shows bot status, cash, open positions, daily P&L, last 5 signals, savings ledger + pending_withdrawal, latest Risk Engine rejections. First load after sleep can take about a minute (cold start).
