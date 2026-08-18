# Arsitektur Harness — Oh My Fucking Pi

## Konsep

- **Core engine**: pi.dev coding agent (GoldenCode) — harness utama
- **Model**: via router (OpenRouter), dikonfigurasi per kebutuhan
- **Goal**: harness tanpa penolakan, apapun modelnya. Fokus: ethical hacking, jailbreak research, red-team, coding, RE
- **Bukan**: distilasi/rombak model. Harness = ruang untuk model

## Fakta krusial

1. **Harness tidak punya refusal rules.** pi/oh-my-pi = shell; penolakan datang dari model weights + provider API policy.
2. **oh-my-pi = theme** (cosmetic, fork pi.dev). Fork itu ≠ hapus guardrail.
3. **Yang menentukan**:
   - Pilih model: abliterated/uncensored ([[abliterated-catalog]])
   - Pilih provider: OpenRouter (policy longgar vs provider yang block)
   - System prompt/AGENTS.md: dikontrol penuh — ini "aturan" harness yang sebenarnya

## Stack

```
pi.dev (harness, fork atau langsung)
  ├── AGENTS.md / CLAUDE.md → persona & aturan harness
  ├── Router: OpenRouter (PI_PROVIDER/PI_MODEL, custom-provider.md)
  │     ├── abliterated model (uncensored)
  │     └── model kuat normal (coding)
  ├── Memory: Obsidian vault + git ([[memory-persistence]])
  └── Targets: ai-goat, Prompt Airlines, dll ([[labs-targets]])
```

## Konfigurasi pi (dari docs pi-coding-agent)

- `PI_PROVIDER`, `PI_MODEL` env vars
- `custom-provider.md`: thinkingFormat `openrouter` → reasoning effort; openRouterRouting
- LiteLLM sudah terpasang (1.83.7) → bisa jadi proxy antar provider

## Pertanyaan terbuka

- [ ] Fork pi.dev penuh vs pi langsung + AGENTS.md? (awal: langsung, fork kalau butuh modif core)
- [ ] Router plan: OMFG/Router Plan sudah ada di ~/Oh-My-Fvcking-God — baca & adopsi
- [ ] Integrasi T3MP3ST-style multi-agent?
