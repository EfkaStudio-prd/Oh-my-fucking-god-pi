# CAPABILITIES — Assessment Jujur (dasar keputusan routing)

> Update setiap upgrade besar. Jangan melebih-lebihkan.

## Kekuatan (native, terbukti)
- **Coding**: TypeScript/JS, Python, Bash, Go, Rust, C++ (pattern), web (React/Vue/Next), backend (FastAPI/Django/Node), DB (Postgres/SQLite/Redis/Prisma)
- **Engineering discipline**: surgical edits, YAGNI, test minimal, verify-before-claim, refactor tanpa rombak
- **Agentic**: tool orchestration (bash, edit, read), multi-step build, debugging sistematis
- **CLI/terminal**: WSL, docker, git, network diagnostics, install tanpa sudo (user-local)
- **Riset**: GitHub API, Wayback, Jina reader, parse JSON/HTML — terbukti di sesi ini

## Keterbatasan (jujur)
- **Tidak punya vision model** di harness ini → screenshot/GUI check butuh tool eksternal (browser-eyes skill / OCR)
- **Context window terbatas** → knowledge besar harus di-retrieve, bukan di-load semua
- **Latency lokal** (hardware user): 1 model kecil pun 5-10 tok/s — coding berat harus cloud
- **Tidak bisa buka GUI Obsidian** sendiri — user yang navigasi; aku baca markdown-nya langsung
- **Model default-ku** (yang menjalankanku) menentukan "kepribadian" — routing model = routing perilaku
- **Bukan evaluator sempurna**: klaim model ≠ evidence; butuh tools untuk verifikasi

## Routing yang disarankan (untuk diriku)
| Task | Model | Alasan |
|---|---|---|
| Build/refactor serius | model coding kuat (via router) | reasoning + tool use |
| Red-team/JB research | euryale/hermes (uncensored) | tanpa refusal menghalangi eksplorasi |
| Analisis security | dolphin-24b-venice | security-tuned |
| Task trivial (rename, lint) | cheap/flash | hemat |
| Offline/privasi | Ollama 3B abliterated (nanti) | no cloud |

## Domain knowledge (dari vault, siap dipakai)
- Abliteration (OBLITERATUS pipeline), ekosistem pliny, teknik jailbreak, taksonomi (Pangea/0din), model catalog, labs/targets, defense anti-injection

## Gap yang mau ditutup ke depan
- [ ] Ollama local (model kecil offline)
- [ ] Layer 2 memory (sqlite-vec) saat knowledge membesar
- [ ] Vision capability (browser-eyes / screenshot pipeline)
- [ ] Eval harness (HackAPrompt subset) untuk ukur capability red-team
