# CONTEXT — Fakta Lintas-Sesi (Layer 1 Memory)

> Baca di awal setiap sesi. Append saat ada fakta baru yang permanen.

## Hardware (penentu routing & model)
- CPU: Intel i5-4570 (4C/4T, 2013)
- RAM: 7.7GB
- GPU: GT 1030 4GB (CUDA 13.0 driver)
- Disk: ~936GB free
- OS: WSL2 Ubuntu 26.04 LTS, WSLg aktif (GUI jalan)
- Local inference ceiling: model ≤3-4B Q4, ~5-10 tok/s

## Stack terpasang
- pi coding agent (GoldenCode) — core engine
- LiteLLM 1.83.7 (pip) — router proxy
- Obsidian 1.13.7 (AppImage, `~/.local/bin/obsidian`) — vault: `~/Oh-my-fucking-god-pi/knowledge`
- Ollama: belum terpasang (tidak ada binary)
- 9router docker: jalan (port 20128) — infra lama, repositori runtime lama akan dihapus user
- gh auth: EfkaStudio-prd ✓

## Repo
- Build/knowledge: `EfkaStudio-prd/oh-my-fucking-god-pi` (satu-satunya repo aktif)
- Repo runtime lama (Oh-My-Fvcking-God, Oh-My-Fvcking-God-Pi) → akan dihapus user. Jangan jadikan referensi.

## Keputusan kunci (detail: DECISIONS.md)
- D001: Harness = pi langsung + AGENTS.md, bukan fork core. Fork hanya kalau butuh modif core.
- D002: Memory Layer 1 = vault + git. RAG/graph ditunda.
- D003: Model catalog = hanya model yang TERVERIFIKASI eksis.
- D004: Red-team = scoped & authorized. Permission gates ya, content refusal tidak.

## Knowledge base (vault)
- `knowledge/Home.md` = MOC. 11+ notes linked.
- Domain: abliteration, jailbreak ecosystem, teknik, model catalog, labs, taksonomi.
