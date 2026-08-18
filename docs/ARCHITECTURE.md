# ARCHITECTURE — Oh My Fucking Pi

## Konsep

- Core engine: pi.dev (GoldenCode) — harness utama
- Model via router (OpenRouter), per-kebutuhan
- Goal: harness tanpa penolakan. Fokus: ethical hacking, jailbreak research, red-team, coding, reverse engineering
- Bukan distilasi/rombak model — harness = ruang untuk model

## Fakta krusial (dari riset)

1. **Harness tidak punya refusal rules.** pi/oh-my-pi = shell; penolakan dari model weights + provider API policy.
2. **oh-my-pi = theme** (cosmetic fork pi.dev). Fork itu ≠ hapus guardrail.
3. **Yang menentukan bebas/tidaknya**:
   - Model: abliterated/uncensored (lihat `knowledge/30-Models/abliterated-catalog.md`)
   - Provider: OpenRouter (policy longgar) vs provider yang block
   - AGENTS.md / system prompt: dikontrol penuh — ini "aturan" harness yang sebenarnya

## Prinsip riset yang diadopsi

- Prompt-level jailbreak = cepat basi; weight-level (abliterated) = permanen
- Abliterated ≠ pintar: capability dari base model
- System prompt extraction = teknik paling efektif (Pangea writeup)
- Defense harness sendiri terhadap indirect prompt injection wajib (teknik di `knowledge/10-Research/techniques.md`)

## Stack

```
pi.dev (harness)
  ├── AGENTS.md / CLAUDE.md → persona & aturan harness
  ├── Router: OpenRouter (PI_PROVIDER/PI_MODEL, custom-provider.md)
  │     ├── abliterated (uncensored)  → red-team, jailbreak research
  │     └── model kuat normal          → coding
  ├── Memory: Obsidian vault + git (Layer 1) → sqlite-vec (Layer 2) → Kuzu (Layer 3)
  └── Targets: ai-goat (self-hosted), Prompt Airlines, Gray Swan...
```

## Config pi (dari docs pi-coding-agent)

- `PI_PROVIDER`, `PI_MODEL` env vars — resolve per command
- `custom-provider.md`: `thinkingFormat: "openrouter"` → reasoning effort; `openRouterRouting` provider prefs
- LiteLLM 1.83.7 terpasang → proxy antar provider

## Keputusan terbuka

- [ ] Fork pi.dev penuh vs pi langsung + AGENTS.md? → awal: langsung, fork kalau butuh modif core
- [ ] Adopsi router plan dari ~/Oh-My-Fvcking-God (Router Plan OMFG.txt)
- [ ] Integrasi multi-agent ala T3MP3ST?

## Referensi harness (best-of-Agent-Harnesses)

- T3MP3ST (pliny) — red teaming platform multi-agent → blueprint offensive harness
- oh-my-pi (can1357) — fork pi.dev dengan tool harness optimasi
