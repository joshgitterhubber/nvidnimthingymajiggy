# AI Gateway Dashboard

Static dashboard frontend for the Supabase-hosted AI Gateway.

Gateway backend:

`https://ruehqdosbdjukugiyjbt.supabase.co/functions/v1/gateway`

The page uses the gateway's admin API and live SSE endpoint. Enter the configured `ADMIN_KEY` when prompted.

## GitHub Pages

This repository includes a Pages deployment workflow in `.github/workflows/pages.yml`.

Pages source is configured for **GitHub Actions**.

The dashboard uses SSE for live updates. The full snapshot fallback refresh runs once per minute.

## Runtime config editor

The dashboard includes an authenticated JSON editor for the gateway's runtime proxy configuration. Saved overrides are stored in `gateway_settings` in Supabase and applied without redeploying the Edge Function. Other warm instances refresh the stored override on a 30-second cache interval. Credentials remain in Supabase Edge Function Secrets and secret-like fields are rejected by the config endpoint.
