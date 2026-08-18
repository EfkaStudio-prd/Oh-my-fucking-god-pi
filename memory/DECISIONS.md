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

## D005 | 2026-08-18 | Repo lama dihapus, oh-my-fucking-god-pi = single source of truth
- Konteks: 3 repo nyaris sama nama, duplikat divergen.
- Konsekuensi: jangan referensi Oh-My-Fvcking-God(-Pi). Semua build di repo ini.
