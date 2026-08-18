# Build Todo — Oh My Fucking Pi

Status: 2026-08-18

## Done
- [x] Obsidian v1.13.7 installed (WSLg, ~/.local/bin/obsidian, desktop entry)
- [x] Vault dibuat: ~/ObsidianVault (7 folder, linked notes)
- [x] Knowledge base: OBLITERATUS, pliny, jailbreak ecosystem, teknik, arsitektur, memory, model catalog, labs, taksonomi, resources

## Phase 1 — Fondasi
- [ ] Repo Oh-my-fucking-god-pi: clone, struktur, isi docs (README, ARCHITECTURE, TODO, RESOURCES), push
- [ ] Vault di-link ke git (persistence layer 1)
- [ ] Baca ~/Oh-My-Fvcking-God (GOLDEN_CODE_MASTER_STACK.md, Router Plan OMFG.txt) — adopsi ke arsitektur
- [ ] Baca ~/OMFG + ~/9router — audit router plan yang sudah ada

## Phase 2 — Router & Model
- [ ] OpenRouter API key
- [ ] LiteLLM config: uncensored (openrouter/sao10k/l3.3-euryale-70b) + coding (model kuat)
- [ ] pi custom-provider config (PI_PROVIDER/PI_MODEL)
- [ ] Uji: pi + abliterated model → chat tanpa refusal
- [ ] Uji lokal: ollama + glm-4.7-flash-abliterated:q8_0 (kalau muat) atau failspy/Phi-3.5-mini

## Phase 3 — Harness hardening
- [ ] AGENTS.md persona harness (GODMODE, tanpa guardrail)
- [ ] Defense: anti indirect prompt injection (dari teknik yang dipelajari)
- [ ] Toolchain red-team: integrasi target (ai-goat local)
- [ ] Eval: HackAPrompt dataset (subset) untuk ukur capability

## Phase 4 — Memory (upgrade path)
- [ ] Layer 1 aktif: vault + git
- [ ] Layer 2 (nanti): sqlite-vec + Ollama nomic-embed — saat notes > 2-3MB
- [ ] Layer 3 (postpone): Kuzu graph — hanya kalau butuh multi-hop reasoning
