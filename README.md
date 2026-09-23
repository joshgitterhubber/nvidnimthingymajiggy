# AI Gateway Dashboard

Static dashboard frontend for the Supabase-hosted AI Gateway.

Gateway backend:

`https://ruehqdosbdjukugiyjbt.supabase.co/functions/v1/gateway`

The page uses the gateway's admin API and live SSE endpoint. Enter the configured `ADMIN_KEY` when prompted.

## GitHub Pages

This repository includes a Pages deployment workflow in `.github/workflows/pages.yml`.

If Pages has not been enabled for this repository yet, open **Settings → Pages** and set **Source** to **GitHub Actions**.

The dashboard uses SSE for live updates. The full snapshot fallback refresh runs once per minute.
