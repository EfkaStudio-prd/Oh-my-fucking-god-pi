# Oh My Fucking Pi — Knowledge Vault

> Core engine: pi.dev (GoldenCode). Harness tanpa guardrail. Router: OpenRouter. Model: abliterated/uncensored.

## Map of Contents

- [[OBLITERATUS]] — abliteration toolkit, cara kerja 6 tahap
- [[pliny-ecosystem]] — katalog repo elder-plinius (CL4R1T4S, T3MP3ST, G0DM0D3...)
- [[jailbreak-ecosystem]] — resource komunitas: ZetaLib, UltraBr3aks, InjectPrompt, roadmap
- [[techniques]] — teknik jailbreak/prompt injection (metodologi yang bertahan)
- [[architecture]] — keputusan arsitektur harness
- [[memory-persistence]] — rekomendasi memory/retrieval
- [[model-routing]] — combo 9Router + subagent system (AKTIF)
- [[abliterated-catalog]] — katalog model abliterated + provider
- [[labs-targets]] — target latihan red-team (self-hosted + online)
- [[taxonomies]] — taksonomi teknik (Pangea 163+, 0din)
- [[resources-master]] — master list semua link
- [[build-todo]] — todo list pembangunan harness

## Prinsip kunci

1. **Prompt-level jailbreak = cepat basi.** Ide bertahan, verbatim tidak. (r/ChatGPTJailbreak wiki, komunitas Discord pliny)
2. **Weight-level (abliterated) = permanen.** Refusal direction dihapus dari weights → tak perlu jailbreak prompt.
3. **Harness ≠ guardrail.** pi/oh-my-pi cuma shell; penolakan datang dari model + provider API.
4. **Abliterated ≠ pintar.** Capability dari base model; abliteration cuma buang refusal.
5. **Hardware low-end** (i5-4570, 7.7GB RAM, GT 1030 4GB) → model besar via cloud, model kecil lokal.

## Status

- [x] Obsidian installed (WSLg, AppImage v1.13.7)
- [x] Vault + knowledge base
- [x] Combo 9Router + subagent system (8 agent, 4 workflow) — lihat [[model-routing]]
- [ ] Repo Oh-my-fucking-god-pi diisi & push
- [ ] Router config (OpenRouter via LiteLLM/pi)
- [ ] Fork pi / custom provider
- [ ] Memory layer
