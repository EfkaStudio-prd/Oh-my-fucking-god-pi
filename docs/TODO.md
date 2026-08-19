# TODO — Build Checklist Oh My Fucking Pi

Status: 2026-08-18 (re-audit pasca cleanup repo lama)

## Done (terverifikasi live)
- [x] Obsidian 1.13.7 (WSLg, ~/.local/bin/obsidian)
- [x] Vault `knowledge/` (Obsidian, 17+ md linked)
- [x] Repo struktur + docs awal
- [x] Vault link git: commit awal + push (main, `d25a08c`)
- [x] Audit repo lama (D003-D005) → keputusan user: hapus, fresh build
- [x] AGENTS.md konstitusi (persona no-refusal, doktrin, §8 self-upgrade)
- [x] Memory Layer 1 aktif (CONTEXT/DECISIONS/PATTERNS/SESSION)
- [x] 9Router service jalan (docker, localhost:20128, 136 model)
- [x] pi → 9Router end-to-end verified (PI_PROVIDER=9router, PI_MODEL=sumopod/deepseek-v4-flash → chat OK)
- [x] **Combo mapping**: `router/COMBO-MAP.md` (13 combo, free-first, harga promo verified)
- [x] **8 combo di 9Router** (Coding, Deep-Coding, Planning, Research, Review, worker, Embed, Judge) → daftar di `~/.pi/agent/models.json`
- [x] **Subagent system AKTIF**: 8 agent per task (scout/planner/engineer/power-worker/researcher/reviewer/judge/worker) + 4 workflow (`/implement`, `/deep-implement`, `/research`, `/review`)
- [x] End-to-end subagent verified (scout → combo worker)

## Phase 2 — Router & Model (sisa)
- [ ] Buat 5 combo sisanya di 9Router: `Parallel`, `Vision`, `Trivial`, `Security`, `Redteam` → daftar ke models.json + agent-nya
- [ ] **OpenRouter API key asli** — user supply; litellm.yaml masih placeholder
  - [ ] Isi `router/.env` (dari .env.example) → key nyata
  - [ ] `litellm --config router/litellm.yaml --port 4000` jalan
  - [ ] Verifikasi alias live: `uncensored` (euryale-70b), `coding`, `cheap`
  - [ ] Uji pi + abliterated → chat tanpa refusal
- [ ] Uji lokal: install ollama (~1GB) + `failspy/Phi-3.5-mini-abliterated` (3.8B Q4, muat RAM 7.7GB)
  - [ ] Verifikasi kecepatan + tanpa refusal offline
- [ ] (opsional) Routing per-task: model map → alias, update `router/MODEL-MAP.md`/`TASK-MAP.md`

## Phase 3 — Harness hardening
- [ ] Defense anti indirect prompt injection (pattern di AGENTS.md / docs)
- [ ] Integrasi target red-team lokal (ai-goat)
- [ ] Eval dengan HackAPrompt dataset subset

## Phase 4 — Memory
- [x] Layer 1 aktif (vault + git + memory/)
- [ ] Layer 2: sqlite-vec + Ollama nomic-embed (saat notes > 2-3MB)
- [ ] Layer 3: Kuzu graph (postpone — hanya jika butuh multi-hop reasoning)

## Catatan
- 9Router katalog TIDAK punya model abliterated → uji no-refusal lewat OpenRouter (LiteLLM) atau ollama lokal.
- Model abliterated target (README): sao10k/l3.3-euryale-70b, nousresearch/hermes-4-70b, huihui_ai/glm-4.7-flash-abliterated, CyberStrike-OffSec-35B.
