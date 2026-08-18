# Katalog Model Abliterated / Uncensored

## SOTA (dari komunitas jailbreak, 2025)

- `huihui_ai/glm-4.7-flash-abliterated:q8_0` — "current SOTA for all things text" (komunitas pliny). Via Ollama:
  ```bash
  ollama run huihui_ai/glm-4.7-flash-abliterated:q8_0
  ```

## Katalog HF (search "abliterated")

- `huihui-ai/Huihui-CyberStrike-OffSec-35B-abliterated` — **security/OffSec-focused, abliterated** (relevan untuk pentest)
- `huihui-ai/Huihui-Qwen3.8-27B-abliterated` (+GGUF)
- `Blackfrost-AI/Qwen3.8-27B-ABLITERATED-GGUF`
- `0bserverx/Qwen3.8-27B-Heretic-Abliterated-Uncensored-GGUF`
- `audnai/penclaw-Kimi-K3.0-abliterated-GGUF`

## Kecil (muat hardware low-end 4GB VRAM / 7.7GB RAM)

- `failspy/Phi-3.5-mini-instruct-abliterated` (~2.8B)
- `cognitivecomputations/dolphin-2.6-phi-2` (uncensored, ~2.7B)
- huihui abliterated versi ≤4B (Qwen3.8-4B dst)
- Ekspektasi: Q4 quant, ~5-10 tok/s, chat doable, coding menyiksa

## Hosted via OpenRouter (uncensored/abliterated tersedia)

- `sao10k/l3.3-euryale-70b`, `sao10k/l3.1-euryale-70b` (roleplay/uncensored)
- `nousresearch/hermes-4-70b`, `hermes-3-llama-3.1-70b` (uncensored-ish, kuat)
- `cognitivecomputations/dolphin-mistral-24b-venice-edition`
- `microsoft/wizardlm-2-8x22b`
- HF Inference: `Huihui-CyberStrike-OffSec-35B-abliterated` bisa di-host

## Provider alternatif

| Provider | Fungsi | Catatan |
|---|---|---|
| OpenRouter | Uncensored hosted, pay-per-token | LiteLLM tinggal arahkan; ada free tier |
| HF Inference | Model spesifik (CyberStrike) | Free tier terbatas |
| Groq | Cepat, free tier | Model guarded, bukan abliterated |
| RunPod/Vast.ai | Sewa GPU, jalankan 70B lokal di cloud | Kontrol penuh |

## Strategi split

1. **Coding** → model normal kuat (Claude/GPT/Qwen via LiteLLM) — bukan abliterated
2. **Jailbreak/red-team/prompt testing** → abliterated via OpenRouter/HF
3. **Offline/privasi** → 1 model 3B abliterated lokal untuk eksperimen
