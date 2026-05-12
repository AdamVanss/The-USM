# Universal Semantic Manifold (USM)

Research code and paper for **The Universal Semantic Manifold: Explicit Semantic Geometry from Validation to Scale**.

The project builds a Riemannian framework on the Poincaré ball where every concept has an explicit geometric position encoding hierarchy, typed relations, cross-modal alignment, and epistemic confidence. Two experiments are reported: a validation-scale run where the hyperbolic model beats the Euclidean baseline, and a cloud-scale run on an A100 that reveals the current optimisation limits of hyperbolic training.

---

## Repository layout

| Path | Contents |
|------|----------|
| [`paper/The_USM.pdf`](paper/The_USM.pdf) | Full paper (PDF) |
| [`notebooks/usm_small-scale.ipynb`](notebooks/usm_small-scale.ipynb) | Experiment 1 — validation scale (85K concepts, T4 GPU). Poincaré beats Euclidean. |
| [`notebooks/usm_big-scale.ipynb`](notebooks/usm_big-scale.ipynb) | Experiment 2 — cloud scale (210K concepts, A100). Documents the optimisation failure and diagnosis. |

---

## Results summary

### Experiment 1 — Validation scale (`usm_small-scale.ipynb`)

100K ConceptNet triples, 85K unique concepts, *d* = 512, CLIP ViT-B/32, 30+30 epochs on a T4 GPU.

| Metric | Poincaré | Euclidean | Δ |
|--------|----------|-----------|---|
| KG Link Prediction MRR | **0.329** | 0.263 | +25% |
| KG Hits@10 | **0.914** | 0.722 | +27% |
| Hierarchy depth accuracy | **47%** | 31% | +16 pp |

### Experiment 2 — Cloud scale (`usm_big-scale.ipynb`)

400K ConceptNet triples, 210K unique concepts, *d* = 1024, CLIP ViT-L/14, 60+60 epochs on an NVIDIA A100 (80 GB).

| Metric | Poincaré | Euclidean | Δ |
|--------|----------|-----------|---|
| KG Link Prediction MRR | 0.010 | **0.027** | −63% |
| Hierarchy depth accuracy | 20% | **99%** | −79 pp |

The cloud-scale Poincaré model collapsed (all embeddings on the same radial shell). The failure is optimisational, not geometric. Root causes and a fix roadmap are documented in the paper and in `usm_big-scale.ipynb`.

---

## Requirements

The notebooks require a GPU runtime (T4 for small-scale, A100 for large-scale). Key dependencies:

- PyTorch
- `transformers`, `datasets`, `sentence-transformers`
- `open-clip-torch`
- `geoopt` (Riemannian optimisation in PyTorch)
- Standard scientific stack (`numpy`, `matplotlib`, `umap-learn`)

Inspect the first setup cell in each notebook for the exact `pip install` commands.

---

## Citation

If you use this work, please cite:

> Adam Mazouar. *The Universal Semantic Manifold: Explicit Semantic Geometry from Validation to Scale.* 2026. Available at https://github.com/AdamVanss/The-USM

---

## License

[MIT](LICENSE). See `LICENSE` for details.
