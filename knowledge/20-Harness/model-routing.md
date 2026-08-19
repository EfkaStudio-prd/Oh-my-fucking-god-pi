# Model Routing & Subagent System

> Status: AKTIF (2026-08-18). Combo 9Router + subagent pi.

## Arsitektur routing

```text
USER → pi (harness)
  → subagent (extension, 8 agent per-tugas)
    → combo 9Router (per-tugas, chain free→paid)
      → model (free/paid sesuai combo)
```

Prinsip: **agent minta combo (per-tugas), bukan model**. Model diganti di combo tanpa ubah agent.

## Combo 9Router (8 dibuat, 5 skip)

| Combo | Isi (chain) |
|---|---|
| `Coding` | qwen3-coder:free → mimo-v2.5-pro → north-mini-code:free |
| `Deep-Coding` | nemotron-3-ultra:free → mimo-v2.5-pro → laguna-m.1:free |
| `Planning` | nemotron-3-ultra:free → gpt-5.6-luna → qwen3-next:free |
| `Research` | qwen3-next:free → qwen3.7-flash → hy3:free |
| `Review` | nemotron-3-ultra:free → claude-opus-4-8 → laguna-m.1:free |
| `worker` | nemotron-3.5-lightning:free → qwen3.7-flash → mimo-v2.5 |
| `Embed` | text-embedding-3-large → small → gemini-embedding (gratis) |
| `Judge` | nemotron-3-ultra:free → gpt-5.6-sol → laguna-m.1:free |

Skip (belum dibuat): `Parallel`, `Vision`, `Trivial`, `Security`, `Redteam` — def lengkap di `router/COMBO-MAP.md`.

## Subagent (8 agent per tugas)

| Agent | Combo | Fungsi |
|---|---|---|
| scout | worker | recon cepat, kompres konteks |
| planner | Planning | buat implementasi plan |
| engineer | Coding | eksekusi plan, perubahan minimal |
| power-worker | Deep-Coding | impl kompleks, reasoning dalam |
| researcher | Research | eksplorasi codebase besar |
| reviewer | Review | hostile review, cari bug |
| judge | Judge | verdict final PASS/REPAIR/ABORT |
| worker | worker | executor umum, bulk |

Workflow chain: `/implement`, `/deep-implement`, `/research`, `/review` (`router/prompts/`).

## Lokasi penting

- `router/COMBO-MAP.md` — def 13 combo + harga verified
- `router/agents/` — agent def (source of truth, symlink ke `~/.pi/agent/agents/`)
- `router/prompts/` — workflow chain (symlink ke `~/.pi/agent/prompts/`)
- `~/.pi/agent/models.json` — daftar model pi (combo didaftarkan di sini, backup `.pre-combo`)
- 9Router: docker `~/9router`, localhost:20128, auth `JCODE_9ROUTER_API_KEY`

## Catatan

- Semua `:free` = GUARDED. Zero-refusal hanya paid OR (`sao10k/l3.3-euryale-70b`) atau lokal abliterated.
- Free rate-limited → combo auto-fallback ke paid.
- Free bisa delisted kapan saja → tiap combo ≥1 fallback paid.
- Edit agent = edit `router/agents/*.md` → berlaku langsung (discover fresh tiap invoke).

Lihat juga: [[architecture]], [[memory-persistence]], [[abliterated-catalog]]
