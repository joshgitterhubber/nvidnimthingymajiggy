# AI Gateway Dashboard

Static dashboard frontend for the Supabase-hosted AI Gateway.

Gateway backend:

`https://ruehqdosbdjukugiyjbt.supabase.co/functions/v1/gateway`

The page uses the gateway's admin API and live SSE endpoint. Enter the configured `ADMIN_KEY` when prompted.

## Providers

The dashboard supports Gemini, NVIDIA NIM, OpenRouter, Routeway, and **OVHcloud AI Endpoints (anonymous)**.

OVHcloud appears in the provider switcher. Select a model in the OVHcloud model picker and press **Apply**. The client-facing virtual model name is:

```json
{ "model": "ovh" }
```

The gateway resolves `ovh` to the model selected in this dashboard. The initial selection is **Qwen3.8-27B**.

Direct model aliases are also available:

| Alias | Model |
| --- | --- |
| `ovh-qwen38` | Qwen3.8-27B |
| `ovh-qwen36` | Qwen3.6-27B |
| `ovh-qwen35-397b` | Qwen3.5-397B-A17B |
| `ovh-qwen35-9b` | Qwen3.5-9B |
| `ovh-gptoss120` | GPT-OSS-120B |
| `ovh-gptoss20` | GPT-OSS-20B |
| `ovh-mistral32` | Mistral Small 3.2 |
| `ovh-llama33-70b` | Llama 3.3 70B |

OVH uses its anonymous, keyless endpoint. Rate limits are enforced upstream; HTTP 429 responses are returned without automatic retries.

## GitHub Pages

This repository includes a Pages deployment workflow in `.github/workflows/pages.yml`.

Pages source is configured for **GitHub Actions**. The frontend is kept in sync with the gateway's generated dashboard HTML.

The dashboard uses SSE for live updates. The full snapshot fallback refresh runs once per minute.

## Runtime config editor

The dashboard includes an authenticated JSON editor for the gateway's runtime proxy configuration. Saved overrides are stored in `gateway_settings` in Supabase and applied without redeploying the Edge Function. Other warm instances refresh the stored override on a 30-second cache interval. Credentials remain in Supabase Edge Function Secrets and secret-like fields are rejected by the config endpoint.
