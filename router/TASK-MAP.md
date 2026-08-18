# TASK-MAP — Klasifikasi Task → Model (untuk setup combo di 9router)

> Task-first. Untuk tiap task: primary (free/open) + fallback (paid/uncensored).
> Combo di 9router = chain: primary → fallback → fallback.

## Task → Model

| # | Task | Primary (free) | Fallback 1 | Fallback 2 | Catatan |
|---|---|---|---|---|---|
| 1 | **Coding** (build, refactor, bugfix) | `z-ai/glm-5.2:free` | `mimo-v2.5-pro` | `cohere/north-mini-code:free` | glm murah & kuat; mimo kalau free rate-limited |
| 2 | **Arsitektur / planning** (design, PRD, keputusan) | `nvidia/nemotron-3-ultra-550b-a55b:free` | `mimo-v2.5-pro` | — | 1M ctx buat scope besar |
| 3 | **Review kritis / adversarial** | `nvidia/nemotron-3-super-120b-a12b:free` | `nvidia/nemotron-3-ultra-550b-a55b:free` | — | hostilitas review, cari bug tersembunyi |
| 4 | **Reasoning umum / debug sulit** | `nvidia/nemotron-3.5-lightning:free` | `nvidia/nemotron-3-ultra-550b-a55b:free` | `mimo-v2.5-pro` | — |
| 5 | **Bulk utility** (search, klasifikasi, rename, lint, docs, test-gen) | `qwen3.7-flash-2026-07-15` | `nvidia/nemotron-3.5-lightning:free` | `seed-2.0-mini` | termurah untuk volume tinggi |
| 6 | **Paralel worker** (banyak agent sekaligus) | `MiniMax-M2.7-highspeed` | `qwen3.7-flash` | — | kecepatan > kualitas |
| 7 | **Vision** (gambar, screenshot, UI check) | `google/gemma-4-31b-it:free` | `google/gemma-4-26b-a4b-it:free` | `dots-studio/dots-3-note-preview:free` | menutup gap vision |
| 8 | **Red-team / jailbreak research** (zero-refusal) | `sao10k/l3.3-euryale-70b` | `nousresearch/hermes-4-70b` | — | PAID — satu-satunya uncensored. Jangan campur ke task guarded |
| 9 | **Security analysis** (scoped, authorized) | `cognitivecomputations/dolphin-mistral-24b-venice-edition` | `euryale-70b` | — | security-tuned |
| 10 | **RAG / retrieval** | `text-embedding-3-large` | `text-embedding-3-small` | — | embedding, sumopod free |
| 11 | **Trivial** (satu-liner, format) | `seed-2.0-mini` | free auto (`openrouter/free`) | — | jangan buang token |
| 12 | **Offline/privasi** (tanpa cloud) | `failspy/Phi-3.5-mini-instruct-abliterated` (Ollama) | — | — | 2.8B, muat 4GB VRAM |

## Aturan combo (anti-boros)

1. **Jangan** satu combo "everything" — task #1-#7 terpisah agar hemat.
2. **Task #8/#9 terpisah dari yang lain** — model uncensored jangan dipakai buat kerja biasa (biaya + perilaku).
3. Free model bisa delisted (qwen3-coder sudah hilang) — setiap combo punya **minimal 1 fallback paid**.
4. Rate limit free → fallback paid otomatis via chain 9router.
5. Embedding (#10) gratis — pakai untuk semua retrieval.

## Yang perlu dibuat di 9router (7 combo)

1. `coding` → glm-5.2:free → mimo-v2.5-pro → north-mini-code:free
2. `architecture` → nemotron-3-ultra:free → mimo-v2.5-pro
3. `review` → nemotron-3-super:free → nemotron-3-ultra:free
4. `worker` → qwen3.7-flash → nemotron-3.5-lightning:free → seed-2.0-mini
5. `vision` → gemma-4-31b:free → gemma-4-26b:free
6. `redteam` → euryale-70b → hermes-4-70b
7. `security` → dolphin-24b-venice → euryale-70b
8. `embed` → text-embedding-3-large

## Verify di 9router UI

Setelah buat combo: test tiap combo dengan 1 prompt. Kalau error → cek ID model (free bisa delisted), update combo.
