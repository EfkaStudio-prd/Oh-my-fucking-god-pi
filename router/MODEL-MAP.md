# MODEL-MAP — Oh My Fucking Pi

> Diverifikasi via OpenRouter API: 2026-08-18. Hanya model yang eksis.
> Urutan prioritas: **free/open-source** → paid 9router → uncensored (paid) → lokal.

## A. FREE + Open-source (prioritas utama)

| Role | Model ID | Ctx | Vision | Catatan |
|---|---|---|---|---|
| **Coding** | `z-ai/glm-5.2:free` | 128k | — | GLM open, coder kuat. Primary free coder |
| **Coding alt** | `cohere/north-mini-code:free` | 256k | — | code-tuned |
| **Reasoner berat** | `nvidia/nemotron-3-ultra-550b-a55b:free` | 1M | — | 550B MoE, problem sulit |
| **Reasoner mid** | `nvidia/nemotron-3-super-120b-a12b:free` | 262k | — | balance speed/kualitas |
| **Worker bulk** | `nvidia/nemotron-3.5-lightning:free` | 1M | — | cepat, ctx besar |
| **Worker alt** | `openai/gpt-oss-20b:free` | 131k | — | open-weights OpenAI |
| **Vision** | `google/gemma-4-31b-it:free` | 262k | ✓ | menutup gap vision harness |
| **Vision kecil** | `google/gemma-4-26b-a4b-it:free` | 262k | ✓ | lebih hemat |
| **Uncensor-ish free** | `nvidia/nemotron-3.5-lightning:free` | 1M | — | open, tapi TETAP guarded |
| **Auto-routing** | `openrouter/free` | 200k | ✓ | biarkan OR pilih free terbaik |

### Free lain (kurang relevan, simpan untuk referensi)
- `poolside/laguna-s-2.1:free`, `laguna-xs-2.1:free` (262k)
- `nvidia/nemotron-3-nano-30b-a3b:free`, `nemotron-3-nano-omni-30b-a3b-reasoning:free` (256k, omni=vision)
- `nvidia/nemotron-nano-12b-v2-vl:free` (vision), `nemotron-nano-9b-v2:free`
- `nvidia/nemotron-3.5-content-safety:free` (128k)
- `dots-studio/dots-3-note-preview:free` (512k, vision — preview)
- `google/lyria-3-clip-preview`, `lyria-3-pro-preview` (1M — audio/video?)

### ⚠️ DELISTED (di 9router-mu, akan gagal — jangan dipakai)
`qwen/qwen3-coder:free` · `qwen/qwen3-next-80b-a3b-instruct:free` · `tencent/hy3:free` · `poolside/laguna-m.1:free` · `nvidia/nemotron-3-nano-omni-30b-a3b-reasoning:free`(masih ada) · `dots-3-note-preview`(masih ada)

## B. PAID — 9router/SumoPod (fallback produksi, dari katalog user)

| Role | Model | Provider | Ctx | Harga/1M in |
|---|---|---|---|---|
| Coding utama paid | `mimo-v2.5-pro` | mimo | 1.1M | $0.43 |
| Worker kecepatan | `MiniMax-M2.7-highspeed` | sumopod | 204k | $0.03 |
| Worker bulk | `qwen3.7-flash-2026-07-15` | alibaba | 1M | $0.03 |
| Trivial | `seed-2.0-mini` | byteplus | 224k | $0.10 |
| Embedding | `text-embedding-3-large` | sumopod | 8k | **$0.00 (free)** |

## C. UNCENSORED (red-team / jailbreak research — satu-satunya zero-refusal)

| Role | Model | Provider | Harga/1M in |
|---|---|---|---|
| Uncensored utama | `sao10k/l3.3-euryale-70b` | OpenRouter (paid) | $0.65µ |
| Uncensored murah | `nousresearch/hermes-4-70b` | OpenRouter (paid) | $0.13µ |
| Security-tuned | `cognitivecomputations/dolphin-mistral-24b-venice-edition` | OpenRouter (paid) | $0.2µ |

> Semua model FREE = guarded. Zero-refusal HANYA dari section C (paid OR) atau lokal abliterated (D).

## D. LOKAL (offline/privasi — Ollama, belum terpasang)

| Role | Model | Ukuran | Catatan |
|---|---|---|---|
| Offline abliterated | `failspy/Phi-3.5-mini-instruct-abliterated` | ~2.8B | muat 4GB VRAM |
| Offline SOTA text | `huihui_ai/glm-4.7-flash-abliterated:q8_0` | ~8GB | **tidak muat** spek ini — simpan untuk upgrade HW |

## Verify command (D003 — wajib sebelum pakai)

```bash
curl -s https://openrouter.ai/api/v1/models | jq -r '.data[].id' | grep -E 'glm-5.2|nemotron-3-ultra|north-mini-code'
```

## Routing default (usulan)

```
default   → z-ai/glm-5.2:free            (coding, open, gratis)
reasoner  → nvidia/nemotron-3-ultra-550b-a55b:free
worker    → nvidia/nemotron-3.5-lightning:free
vision    → google/gemma-4-31b-it:free
uncensored→ sao10k/l3.3-euryale-70b      (paid — hanya ini zero-refusal)
embed     → text-embedding-3-large       (sumopod, gratis)
fallback paid → mimo-v2.5-pro, qwen3.7-flash, MiniMax-M2.7-highspeed
```

Catatan: free tier = rate-limited + prioritas rendah (lambat jam sibuk). Paid fallback disiapkan untuk kerja produksi.
