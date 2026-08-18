# ROUTER PLAN — Oh My Fucking Pi

## Tujuan

Satu harness (pi.dev), banyak model, bebas ganti tanpa restart. Zero refusal untuk model yang dipilih.

## Provider

| Provider | Peran | Catatan |
|---|---|---|
| OpenRouter | Utama: uncensored + coding | Pay-per-token, ada free tier, policy longgar |
| HF Inference | Model spesifik (CyberStrike-OffSec-35B-abliterated) | Free tier terbatas |
| Ollama (lokal) | Model kecil offline/privasi | 4GB VRAM → ≤3-4B Q4 |
| RunPod/Vast.ai | Sewa GPU untuk 70B lokal | Upgrade path |

## Model routing

| Use case | Model |
|---|---|
| Coding utama | model kuat normal (Claude/GPT/Qwen via LiteLLM) |
| Red-team / jailbreak research | `sao10k/l3.3-euryale-70b`, `nousresearch/hermes-4-70b` |
| Security/OffSec | `Huihui-CyberStrike-OffSec-35B-abliterated` (HF) |
| Offline eksperimen | `huihui_ai/glm-4.7-flash-abliterated:q8_0` atau `failspy/Phi-3.5-mini-instruct-abliterated` (Ollama) |

## Implementasi

### Opsi A — LiteLLM proxy (sudah terpasang 1.83.7)
```yaml
# ~/.litellm/config.yaml
model_list:
  - model_name: uncensored
    litellm_params:
      model: openrouter/sao10k/l3.3-euryale-70b
      api_key: os.environ/OPENROUTER_API_KEY
  - model_name: coding
    litellm_params:
      model: openrouter/anthropic/claude-sonnet-4
      api_key: os.environ/OPENROUTER_API_KEY
```

### Opsi B — pi native (PI_MODEL/PI_PROVIDER)
- `PI_PROVIDER=openrouter PI_MODEL=sao10k/l3.3-euryale-70b`
- custom-provider.md untuk thinkingFormat/reasoning

### Opsi C — 9router (docker-compose sudah ada di ~/9router)
- Audit dulu isi docker-compose.yml

## Catatan provider policy

- Model abliterated di OpenRouter = permanen (bukan di-patch)
- Yang bisa kena policy: hosted API bisa block konten tertentu → fallback ke lokal/Ollama
- Groq = cepat tapi guarded, bukan untuk uncensored
