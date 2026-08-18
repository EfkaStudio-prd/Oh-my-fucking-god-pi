# PATTERNS — Pola yang Terbukti

> Hanya pola yang terbukti berulang & berguna. Bukan diary.

## Riset/lookup
- GitHub API lebih andal daripada scrape HTML untuk repo info (desc, tree, stars).
- Reddit block IP → pakai Wayback Machine (`web.archive.org/web/2024/URL`).
- SPA (React) → cari API di bundle JS (`grep fetch(` / `"/api/..."`), contoh: jailbreak-roadmap `/api/resources`.
- Repo 301/moved → cek via `curl -o /dev/null -w "%{http_code}"`.

## Install GUI di WSL
- AppImage butuh libfuse2 (Ubuntu 24.04+ cuma fuse3): `sudo apt-get install -y libfuse2`.
- WSLg aktif → DISPLAY=:0, GUI jalan. Error WebGL blocklisted = normal (software rendering), jangan panik.
- AppImage tanpa FUSE: `--appimage-extract` lalu jalankan binary langsung.

## Arsitektur
- Harness tak punya refusal; refusal di model+provider. Jangan boros waktu cari guardrail di harness.
- Model catalog harus diverifikasi eksis via API — catalog fiksi = resolver rusak diam-diam.

## Domain
- Prompt jailbreak cepat basi; teknik + system prompt bocor bertahan. Abliterated = permanen (weights-level).
- System prompt extraction > direct attack (flag biasanya di system prompt).
