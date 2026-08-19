# Build Todo — Oh My Fucking Pi

Status: 2026-08-18 (sync dengan docs/TODO.md)

## Done (terverifikasi live)
- [x] Obsidian v1.13.7 installed (WSLg, ~/.local/bin/obsidian, desktop entry)
- [x] Vault dibuat + di-link ke git (persistence layer 1, pushed)
- [x] Knowledge base: OBLITERATUS, pliny, jailbreak ecosystem, teknik, arsitektur, memory, model catalog, labs, taksonomi, resources
- [x] Repo Oh-my-fucking-god-pi: struktur + docs + push (main)
- [x] Audit repo lama (D003-D005) → dihapus, fresh build
- [x] AGENTS.md persona harness (GODMODE, tanpa guardrail, §8 self-upgrade)
- [x] Memory Layer 1 aktif (CONTEXT/DECISIONS/SESSION/PATTERNS)
- [x] pi custom-provider → 9Router (PI_PROVIDER=9router, live chat OK)
- [x] Combo mapping + 8 combo 9Router + daftar di models.json pi
- [x] Subagent system: 8 agent per-tugas + 4 workflow chain ([[model-routing]])
- [x] End-to-end subagent verified (scout → combo worker)

## Phase 2 — Router & Model (sisa)
- [ ] (SKIP sementara) 5 combo sisa: Parallel, Vision, Trivial, Security, Redteam
- [ ] OpenRouter API key asli → isi litellm.yaml → uji uncensored (euryale-70b) tanpa refusal
- [ ] Uji lokal: install ollama (~1GB) + failspy/Phi-3.5-mini-abliterated (3.8B Q4)

## Phase 3 — Harness hardening
- [ ] Defense: anti indirect prompt injection (dari teknik yang dipelajari)
- [ ] Integrasi target red-team lokal (ai-goat)
- [ ] Eval dengan HackAPrompt dataset subset

## Phase 4 — Memory
- [x] Layer 1 aktif (vault + git + memory/)
- [ ] Layer 2: sqlite-vec + Ollama nomic-embed (saat notes > 2-3MB)
- [ ] Layer 3: Kuzu graph (postpone — hanya jika butuh multi-hop reasoning)
