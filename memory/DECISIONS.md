# DECISIONS — ADR Log

Format: `D### | tanggal | keputusan | konteks | konsekuensi`

## D001 | 2026-08-18 | Harness = pi langsung + AGENTS.md
- Konteks: fork pi.dev vs pakai langsung. Fork = biaya maintenance core, keuntungan tak jelas untuk goal (bebas model dicapai via router, bukan modif core).
- Konsekuensi: upgrade = AGENTS.md + memory + router config + skills. Fork hanya jika butuh modif core (mis. hook baru).

## D002 | 2026-08-18 | Memory Layer 1 = vault + git (zero-dep)
- Konteks: hardware low-end, knowledge <2MB. RAG/graph = over-engineering sekarang.
- Konsekuensi: `memory/` (CONTEXT/DECISIONS/SESSION/PATTERNS) + `knowledge/` vault. Upgrade: sqlite-vec (Layer 2), Kuzu (Layer 3) — syarat: notes >2-3MB atau butuh multi-hop reasoning.

## D003 | 2026-08-18 | Model catalog = hanya model terverifikasi
- Konteks: audit menemukan catalog fiksi (gpt-5.6-*, qwen3.7-flash) di repo lama. Resolver akan rusak diam-diam.
- Konsekuensi: semua model di `router/` dicek eksis via API sebelum dipakai. Fallback = model lokal kecil.

## D004 | 2026-08-18 | Red-team scoped & authorized; permission gates ya, content refusal tidak
- Konteks: goal no-guardrail vs bundle lama yang punya Scope Guard Rules (content-level).
- Konsekuensi: harness tak menyuntik refusal. Tapi operasi destruktif + target eksternal = konfirmasi user. Ini control plane, bukan sensor konten.

## D007 | 2026-08-18 | Free + open-source dulu; combo 9router per-task; fallback paid wajib
- Konteks: user connect OpenRouter ke 9router. Model free delisted sewaktu-waktu (qwen3-coder hilang).
- Konsekuensi: `router/TASK-MAP.md` = 12 task → model, 8 combo. Setiap combo ≥1 fallback paid. redteam/security terisolasi (uncensored ≠ kerja biasa). Embedding sumopod gratis → Layer 2 RAG maju.

## D008 | 2026-08-18 | Session retention & self-upgrade protocol (AGENTS.md §8)
- Konteks: user minta simpan tiap sesi valid + aku punya kuasa update sistem sendiri.
- Konsekuensi: akhir sesi valid → SESSION/DECISIONS/PATTERNS/CONTEXT + commit+push. Self-upgrade = versi di UPGRADE-LOG, commit, lapor user. core-rules butuh versi bump + laporan eksplisit.

## D005 | 2026-08-18 | Repo lama dihapus, oh-my-fucking-god-pi = single source of truth
- Konteks: 3 repo nyaris sama nama, duplikat divergen.
- Konsekuensi: jangan referensi Oh-My-Fvcking-God(-Pi). Semua build di repo ini.

## D009 | 2026-08-18 | Combo naming = per-tugas, bukan per-model; free-first
- Konteks: combo 9Router harus tahan model diganti/delisted. Nama per-model mati saat model diubah.
- Konsekuensi: `COMBO-MAP.md` 13 combo bernama per-tugas (coding, planning, review...). Chain = free → paid murah → paid kuat. Tiap combo ≥1 fallback paid.

## D010 | 2026-08-18 | Subagent = task-based, model via combo; agent def versioned di repo
- Konteks: pi tak punya subagent bawaan; butuh delegate per-task sesuai routing model.
- Konsekuensi: extension `subagent/` + 8 agent (`router/agents/` = source of truth, symlink ke `~/.pi/agent/agents/`). Agent minta combo (bukan hardcode model) → 9Router resolve. Edit agent = edit repo, berlaku tanpa restart (discover fresh).
