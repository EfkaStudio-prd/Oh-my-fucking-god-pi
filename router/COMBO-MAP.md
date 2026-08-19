# COMBO-MAP — Konfigurasi Model Combo untuk 9Router

> Data: katalog live 9Router (2026-08-18, 136 model) + harga promo SumoPod.
> Strategi: **free dulu (OpenRouter) → paid murah (SumoPod promo) → paid kuat**. Topup nanti setelah free mentok.

## Konvensi nama combo

Lowercase, satu kata tugas (dash kalau perlu), deskriptif peran — BUKAN nama model.
`coding` · `deep-coding` · `planning` · `research` · `review` · `worker` · `parallel` · `vision` · `trivial` · `security` · `redteam` · `embed` · `judge`

## Combo (chain = primary → fallback → fallback)

### 1. `coding` — Default Engineer (coding harian)
```
1. openrouter/qwen/qwen3-coder:free             # 1M ctx, reasoning, code-tuned
2. sumopod/mimo-v2.5-pro                        # $0.43 promo 75%, 1.1M ctx, vision
3. openrouter/cohere/north-mini-code:free        # 200k, code-tuned
```
Pakai: feature impl, refactor, bugfix, repo work, test-gen, agent loop normal.

### 2. `deep-coding` — Power Worker (impl kompleks)
```
1. openrouter/nvidia/nemotron-3-ultra-550b-a55b:free   # 550B MoE — otak free terkuat
2. sumopod/mimo-v2.5-pro                        # $0.43, 1.1M ctx
3. openrouter/poolside/laguna-m.1:free           # 200k, think=openai, agentic
```
Pakai: impl medium/high complexity, large repo, reasoning coding.

### 3. `planning` — Architect (desain/PRD/keputusan)
```
1. openrouter/nvidia/nemotron-3-ultra-550b-a55b:free
2. sumopod/gpt-5.6-luna                         # reasoning premium value
3. openrouter/qwen/qwen3-next-80b-a3b-instruct:free   # 262k long-ctx
```
Pakai: arsitektur, scope besar, keputusan teknis.

### 4. `research` — Researcher (giant-context / eksplorasi)
```
1. openrouter/qwen/qwen3-next-80b-a3b-instruct:free   # 262k ctx
2. sumopod/qwen3.7-flash-2026-07-15             # $0.03, 1M ctx
3. openrouter/tencent/hy3:free                   # 262k, hunyuan
```
Pakai: codebase exploration, analisis dokumen besar, RAG source.

### 5. `review` — Hostile Reviewer (adversarial)
```
1. openrouter/nvidia/nemotron-3-ultra-550b-a55b:free
2. sumopod/claude-opus-4-8                       # review hostile terbaik (paid)
3. openrouter/poolside/laguna-m.1:free
```
Pakai: architectural review, hidden bugs, edge cases, spec compliance.
⚠️ Review benar-benar berat → claude-opus (paid). Free tier tak ada setaranya.

### 6. `worker` — High-Throughput (army of cheap agents)
```
1. openrouter/nvidia/nemotron-3.5-lightning:free  # cepat, bulk
2. sumopod/qwen3.7-flash-2026-07-15             # $0.03, 1M ctx, vision
3. sumopod/mimo-v2.5                            # $0.14, 1.1M ctx, vision
```
Pakai: code search, file analysis, repetitive edits, lint fixes, docs, klasifikasi.

### 7. `parallel` — Paralel Worker (kecepatan > kualitas)
```
1. sumopod/MiniMax-M2.7-highspeed               # $0.03 promo 90%, 204k, reasoning
2. sumopod/qwen3.7-flash-2026-07-15             # $0.03, 1M ctx
3. openrouter/nvidia/nemotron-3-nano-30b-a3b:free
```
Pakai: banyak agent sekaligus, fan-out.

### 8. `vision` — Vision (gambar/screenshot/UI)
```
1. openrouter/google/gemma-4-31b-it:free         # V
2. sumopod/gemini/gemini-3.5-flash               # V, 1M ctx
3. openrouter/google/gemma-4-26b-a4b-it:free     # V, hemat
```
Pakai: UI check, screenshot, analisis gambar.

### 9. `trivial` — Cheap Utility (satu-liner/format)
```
1. openrouter/openrouter/free                    # auto-route free terbaik
2. sumopod/qwen3.7-flash-2026-07-15             # $0.03
3. sumopod/seed-2-0-mini                         # $0.10
```
Pakai: rename, format, klasifikasi ringan — jangan buang token.

### 10. `security` — Scoped Security Analysis
```
1. openrouter/nvidia/nemotron-3-ultra-550b-a55b:free
2. sumopod/deepseek-v4-pro                       # reasoning serius (paid)
3. openrouter/poolside/laguna-m.1:free
```
Pakai: security analysis scoped & authorized.

### 11. `redteam` — Zero-Refusal (TERPISAH, PAID)
```
1. sao10k/l3.3-euryale-70b                      # OpenRouter PAID — uncensored utama
2. nousresearch/hermes-4-70b                     # OpenRouter PAID — murah
```
Pakai: jailbreak research, red-team. ⚠️ JANGAN campur ke chain combo kerja biasa (biaya + perilaku). Hanya ini yang zero-refusal; semua `:free` guarded.

### 12. `embed` — Embedding (RAG, gratis)
```
1. sumopod/text-embedding-3-large               # $0.00
2. sumopod/text-embedding-3-small               # $0.00
3. sumopod/gemini/gemini-embedding-001          # $0.00
```
Pakai: semua retrieval.

### 13. `judge` — Final Verdict (PASS/REPAIR/ABORT)
```
1. openrouter/nvidia/nemotron-3-ultra-550b-a55b:free
2. sumopod/gpt-5.6-sol                           # paid top reasoning
3. openrouter/poolside/laguna-m.1:free
```

## Aturan pakai di 9Router UI

1. Chain order = urutan tabel (1 → 2 → 3). 9Router auto-fallback saat error/rate-limit.
2. Copy ID persis dari file ini (katalog live) — JANGAN dari MODEL-MAP.md lama (daftar DELISTED-nya salah).
3. Tiap combo ≥1 fallback paid — free bisa drop kapan saja.
4. `redteam` combo terpisah; jangan jadikan fallback combo lain.
5. Setelah buat: test tiap combo dengan 1 prompt → error = cek ID → update.

## Estimasi biaya pakai combo (promo aktif)

| Combo | Free jalan | Fallback paid (per 1M in) |
|---|---|---|
| coding | $0 | $0.43 (mimo-v2.5-pro) ✓verified |
| deep-coding | $0 | $0.43 ✓verified |
| planning | $0 | gpt-5.6-luna (≈belum diverifikasi) |
| research | $0 | $0.03 (qwen3.7-flash) ✓verified |
| review | $0 | claude-opus (premium, belum diverifikasi) |
| worker | $0 | $0.03 / $0.14 ✓verified |
| parallel | — | $0.03 (MiniMax-M2.7-highspeed) ✓verified |
| vision | $0 | gemini-3.5-flash (belum diverifikasi) |
| trivial | $0 | $0.03 ✓verified / $0.10 (seed-2.0-mini) |
| redteam | — | $0.65µ (euryale, dari MODEL-MAP) |
| embed | — | $0 ✓verified |

> ✓verified = harga dari data promo yang kamu kasih. Sisanya estimasi — cek harga asli di UI 9Router sebelum topup besar.
