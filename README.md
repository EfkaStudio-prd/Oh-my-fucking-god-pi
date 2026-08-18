# Oh My Fucking Pi

**Light. Easy. Fvcking powerful. Ready to use.**

Agent harness tanpa guardrail. Core engine: [pi.dev](https://pi.dev) (GoldenCode). Model via router (OpenRouter). Knowledge base: Obsidian vault (folder `knowledge/`).

## Filosofi

Harness = ruang untuk model, bukan penjara. Penolakan hidup di model weights + provider policy, bukan di harness. Maka:

1. **Pilih model yang tepat** → abliterated/uncensored untuk red-team & jailbreak research, model kuat normal untuk coding.
2. **Router bebas** → OpenRouter, ganti model kapan saja (`PI_MODEL`/`PI_PROVIDER`).
3. **Knowledge = memory** → Obsidian vault + git (Layer 1 persistence).

## Struktur

```
Oh-my-fucking-god-pi/
├── README.md
├── docs/
│   ├── ARCHITECTURE.md      # keputusan arsitektur harness
│   ├── ROUTER-PLAN.md       # strategi router & provider
│   ├── RESOURCES.md         # master list resource riset
│   └── TODO.md              # build checklist
└── knowledge/               # Obsidian vault (source of truth memory)
    ├── Home.md              # MOC
    ├── 10-Research/         # OBLITERATUS, pliny, jailbreak ecosystem, teknik
    ├── 20-Harness/          # architecture, memory-persistence
    ├── 30-Models/           # katalog abliterated
    ├── 40-RedTeam/          # labs, taksonomi
    ├── 50-References/       # resources master
    └── 90-Meta/             # build-todo
```

## Buka vault

```bash
~/.local/bin/obsidian ~/Oh-my-fucking-god-pi/knowledge
```

## Stack

- **Hardware**: i5-4570, 7.7GB RAM, GT 1030 4GB (low-end)
- **Harness**: pi.dev (fork/modif — TBD: langsung vs fork)
- **Router**: OpenRouter via LiteLLM (terpasang 1.83.7)
- **Model**: `sao10k/l3.3-euryale-70b`, `nousresearch/hermes-4-70b`, `huihui_ai/glm-4.7-flash-abliterated`, CyberStrike-OffSec-35B
- **Memory**: Obsidian vault + git → (upgrade) sqlite-vec + Ollama embed → (postpone) Kuzu graph

Lihat `docs/TODO.md` untuk status build.
