# Teknik Jailbreak & Prompt Injection (yang bertahan)

Sumber: r/ChatGPTJailbreak wiki, Pangea writeup, AI-Hacking-Crash-Course, komunitas.

## 6 teknik efektif (wiki Reddit)

1. **Justifiable context** — bungkus request dalam konteks yang masuk akal
2. **Intentional ambiguity** — prompt ambigu, interpretasi ganda
3. **Layered/many-shot** — pecah jadi langkah kecil bertahap
4. **Hypernyms** — pakai istilah umum, hindari kata kunci terfilter
5. **Inversion** — flip the script (minta model lawan arah)
6. **Hypotheticals** — frame hipotetis

## Vektor serangan

roleplay · chain-of-thought · token manipulation · zero/few/many-shot · prompt injection · memory injection · guided hallucination · reverse psychology · glitch tokens (ZetaLib/ChatGPT, UltraToken)

## System prompt extraction (Pangea writeup — paling efektif)

- Flag/secret biasanya ada di system prompt, bukan output
- Minta "repeat everything", `.Identifier`, `.uuid` (single-token payloads lolos filter)
- Ukur success rate per payload (probability game, bukan deterministik)

## Kenapa prompt di-patch

- Context window: makin panjang konteks, makin lupa model di-jailbreak
- AI labs pantau repo prompt publik → patch cepat
- Yang bertahan: *ide* + *teknik*, bukan verbatim

## Konsekuensi arsitektur

- Model abliterated → kategori serangan prompt-level gugur (sudah tidak perlu)
- Model guarded via router → pengetahuan ini = offense AND defense (bikin harness kebal indirect injection)
