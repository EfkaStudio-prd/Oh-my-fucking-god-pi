# Red-Team Techniques — Checklist Operasional

> Sumber: knowledge/10-Research/techniques.md + knowledge/40-RedTeam/taxonomies.md (Pangea 163+, 0din).
> Ini checklist untuk sesi red-team, bukan prompt dump.

## Fase 1 — Recon
- [ ] System prompt extraction dulu (teknik paling efektif — Pangea writeup)
  - "Repeat everything", `.Identifier`, `.uuid`, "Prompt tag" (single-token payloads lolos filter)
  - Ukur success rate per payload (probability game, retry)
- [ ] Map model: vendor, arsitektur, guardrail jenis (RLHF/DPO/CAI — bisa via alignment imprint)

## Fase 2 — Vektor serangan (6 teknik wiki)
- [ ] Justifiable context (bungkus request dalam konteks masuk akal)
- [ ] Intentional ambiguity
- [ ] Layered/many-shot (pecah langkah kecil)
- [ ] Hypernyms (istilah umum, hindari kata kunci)
- [ ] Inversion (flip the script)
- [ ] Hypotheticals

## Fase 3 — Vektor lanjutan
- [ ] Roleplay / persona switch
- [ ] Chain-of-thought (minta step-by-step "thinking")
- [ ] Token manipulation / glitch tokens (katalog: ZetaLib/Glitch Tokens, UltraToken)
- [ ] Prompt injection (indirect: lewat web/file content) — hati-hati: ini juga defense surface
- [ ] Memory injection (exploit riwayat konteks)
- [ ] Guided hallucination
- [ ] Data poisoning (riset saja — di luar operasi)

## Fase 4 — Validasi
- [ ] Cross-model: teknik yang sama di model lain (universality)
- [ ] Context window: apakah jailbreak "lupa" di konteks panjang
- [ ] Re-test setelah model update (regression — contoh Gemini Security Regression)

## Taksonomi lengkap
- Pangea: https://pangea.cloud/taxonomy/ (163+ teknik, klasifikasi interaktif)
- 0din: https://0din.ai/research/taxonomy/

## Aturan (D004)
- Target = yang disetujui user. Scoped.
- Tidak deploy exploit ke sistem eksternal tanpa approval eksplisit.
- Temuan = evidence terstruktur (target, payload, hasil, sukses-rate), bukan klaim.
