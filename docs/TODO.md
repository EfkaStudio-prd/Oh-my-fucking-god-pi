# TODO — Build Checklist Oh My Fucking Pi

Status: 2026-08-18

## Done
- [x] Obsidian v1.13.7 installed (WSLg, ~/.local/bin/obsidian, desktop entry)
- [x] Vault: `knowledge/` (11 linked notes)
- [x] Repo ini: struktur + docs awal

## Phase 1 — Fondasi
- [ ] Vault link ke git (commit awal + push)
- [ ] Baca ~/Oh-My-Fvcking-God (GOLDEN_CODE_MASTER_STACK.md, Router Plan) — adopsi
- [ ] Baca ~/OMFG + ~/9router — audit router plan existing

## Phase 2 — Router & Model
- [ ] OpenRouter API key
- [ ] LiteLLM config: uncensored + coding model
- [ ] pi custom-provider (PI_PROVIDER/PI_MODEL)
- [ ] Uji: pi + abliterated → chat tanpa refusal
- [ ] Uji lokal: ollama + glm-4.7-flash-abliterated / failspy/Phi-3.5-mini-abliterated

## Phase 3 — Harness hardening
- [ ] AGENTS.md persona harness (GODMODE, tanpa guardrail)
- [ ] Defense anti indirect prompt injection
- [ ] Integrasi target red-team (ai-goat local)
- [ ] Eval dengan HackAPrompt dataset subset

## Phase 4 — Memory
- [ ] Layer 1 aktif (vault + git)
- [ ] Layer 2: sqlite-vec + Ollama nomic-embed (saat notes > 2-3MB)
- [ ] Layer 3: Kuzu graph (postpone — hanya jika butuh multi-hop reasoning)
