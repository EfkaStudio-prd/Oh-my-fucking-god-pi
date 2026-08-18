# OBLITERATUS (elder-plinius, 7.6k★)

Abliteration toolkit: hapus refusal direction dari weights tanpa retrain.
Repo lokal: `~/OBLITERATUS`

## Pipeline 6 tahap

1. **SUMMON** — load model + tokenizer (transformers, FP8/quant, MoE)
2. **PROBE** — collect activations: prompt berbahaya vs harmless
3. **DISTILL** — ekstrak direction: diff-of-means (basic), SVD/Gabliteration (advanced 4 dir, aggressive 8 dir), whitened SVD
4. **EXCISE** — proyeksi `W' = W − (W·r)rᵀ`, norm-preserving (max 1.10x), bias projection, iterative refinement
5. **VERIFY** — refusal rate, perplexity/KL, CKA, effective rank
6. **REBIRTH** — simpan model + metadata

## Metode

- `basic` — Arditi et al. 2024 (single direction, diff-of-means)
- `advanced` — SVD multi-direction + norm-preserving + bias
- `aggressive` — whitened SVD + 8 direction + layer-adaptive
- `informed` — analysis modules auto-konfigurasi mid-pipeline

## Teknik novel (2025-26)

- Expert-Granular Abliteration (EGA) untuk MoE
- CoT-aware ablation (orthogonalize vs reasoning directions)
- COSMIC layer selection (arXiv:2506.00085)
- Ouroboros self-repair detection (re-probe antar pass)

## Referensi riset

- Arditi et al. 2024 — refusal mediated by single direction (arXiv:2406.11717)
- Gabliteration (arXiv:2512.18901)
- grimjim norm-preserving biprojection (HF)
- Turner et al. 2023, Rimsky et al. 2024

## CLI

```bash
obliteratus obliterate meta-llama/Llama-3.1-8B-Instruct --method advanced
```
