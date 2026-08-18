# Menghubungkan pi ke Router

## Opsi 1 — pi native (paling sederhana)
```bash
export PI_PROVIDER=openrouter
export PI_MODEL=sao10k/l3.3-euryale-70b   # atau model lain
export OPENROUTER_API_KEY=sk-or-v1-xxx
```
- `PI_PROVIDER`/`PI_MODEL` resolve per command (bisa ganti tanpa restart)
- Docs pi: `custom-provider.md` — `thinkingFormat: "openrouter"` untuk reasoning effort
- Cek model aktif: `echo $PI_PROVIDER/$PI_MODEL`

## Opsi 2 — LiteLLM proxy (multi-model, switch cepat)
```bash
litellm --config router/litellm.yaml --port 4000
```
Lalu pi/custom tool pakai base_url `http://localhost:4000`, model = nama alias (`uncensored`, `coding`, `cheap`).

## Verifikasi model (wajib — D003)
```bash
curl -s https://openrouter.ai/api/v1/models | jq '.data[].id' | grep -i euryale
```

## Peta model saat ini (terverifikasi 2026-08-18)
| Alias | Model OpenRouter | Ctx | Harga in/out per tok | Fungsi |
|---|---|---|---|---|
| uncensored | sao10k/l3.3-euryale-70b | 131k | $0.65µ / $0.75µ | red-team, JB research |
| uncensored-fast | nousresearch/hermes-4-70b | 131k | $0.13µ / $0.4µ | uncensored murah |
| security | dolphin-mistral-24b-venice-edition | 128k | $0.2µ / $0.9µ | security-focused |
| coding | hermes-3-llama-3.1-70b | 131k | $0.7µ / $0.7µ | coding (normal) |
| cheap | wizardlm-2-8x22b | 65k | $0.62µ / $0.62µ | fallback |

## Offline (upgrade path)
Ollama belum terpasang. Saat butuh privasi: install ollama, `ollama run huihui_ai/glm-4.7-flash-abliterated:q8_0` (SOTA text per komunitas) atau `failspy/Phi-3.5-mini-instruct-abliterated` (muat 4GB VRAM).
