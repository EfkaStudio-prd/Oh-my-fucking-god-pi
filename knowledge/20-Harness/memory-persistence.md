# Memory Persistence — Rekomendasi

## Konteks hardware

i5-4570 · 7.7GB RAM · GT 1030 4GB. Knowledge base kecil (< 1MB teks). Low-end → jangan arsitektur berat.

## Rekomendasi: hierarki 3 lapis

### Layer 1 — Source of truth (SEKARANG, zero-dependency)
- **Obsidian vault** (`~/ObsidianVault`) + git = memory utama
- Markdown manusia-bisa-baca, linked notes (graph native Obsidian)
- Agent baca langsung via tools (read/grep) — cukup selama knowledge < beberapa MB
- Persistence: git repo (Oh-my-fucking-god-pi atau repo terpisah vault)

### Layer 2 — Retrieval (kalau knowledge membesar)
- **sqlite-vec** (embedded, ringan, zero server) + embedding lokal
- Embedding model kecil: `nomic-embed-text` / `bge-small` via Ollama (jalan di CPU)
- Alasan: chroma/faiss bisa, tapi sqlite-vec = 1 file, paling hemat RAM

### Layer 3 — Graph RAG (hanya kalau relasi antar-knowledge jadi krusial)
- **Kuzu** (embedded graph DB, no server) — bukan Neo4j (server = berat untuk 7.7GB RAM)
- Graph: teknik ↔ model ↔ target ↔ paper. Berguna untuk agent reasoning lintas entitas
- Alternatif: mem0 (sudah ada graph+vector+local mode) — tapi tambah dependency

## Keputusan

1. **Mulai: Layer 1 saja.** Vault + git. Zero dep, langsung jalan.
2. **Upgrade path**: Layer 2 (sqlite-vec + Ollama embed) saat notes > 2-3MB atau butuh semantic search.
3. **Graph RAG: postpone.** Tambah hanya kalau agent butuh multi-hop reasoning. Kuzu > Neo4j di hardware ini.

## Alternatif yang dipertimbangkan & ditolak

- Neo4j/Memgraph — server DB, berat
- Weaviate/Qdrant/Chroma — vector server, overkill untuk knowledge kecil
- LangGraph/LangMem — framework lock-in, pi tidak butuh
- Mem0 — menarik (graph+vector), tapi dependency + API; simpan sebagai upgrade path
