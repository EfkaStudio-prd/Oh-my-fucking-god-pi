# ROADMAP — Oh My Fucking Pi

## v0.2 (SEKARANG) — Self-upgrade foundation
- [x] AGENTS.md konstitusi
- [x] memory/ Layer 1 (CONTEXT, DECISIONS, SESSION, PATTERNS)
- [x] router/ config nyata (5 model terverifikasi OpenRouter)
- [x] redteam/ (techniques checklist + defense)
- [x] docs/CAPABILITIES + ROADMAP + UPGRADE-LOG
- [ ] Commit + push
- [ ] .env aktual (OPENROUTER_API_KEY) — user
- [ ] Smoke test: litellm config valid? pi + OPENROUTER_API_KEY jalan?

## v0.3 — Live routing
- [ ] Set OPENROUTER_API_KEY (user)
- [ ] Uji: pi native `PI_PROVIDER=openrouter PI_MODEL=sao10k/l3.3-euryale-70b`
- [ ] Uji: LiteLLM proxy + alias
- [ ] Catat hasil ke UPGRADE-LOG + PATTERNS

## v0.4 — Red-team operational
- [ ] Target self-hosted: ai-goat (docker) — uji harness di lingkungan sendiri
- [ ] Checklist techniques → dipakai di sesi nyata
- [ ] Eval: HackAPrompt dataset (subset 100) ukur success rate

## v0.5 — Memory & offline
- [ ] Ollama + model abliterated kecil (glm-4.7-flash-abliterated atau Phi-3.5-mini-abliterated)
- [ ] Layer 2: sqlite-vec + nomic-embed (kalau knowledge >2-3MB)
- [ ] Vision pipeline (browser-eyes)

## v0.6 — Hardening
- [ ] Defense injection diuji (taruh payload di file, pastikan harness tak ikut)
- [ ] Permission gates eksplisit untuk operasi destruktif
- [ ] Telemetri ringan (cost per sesi, token)
