# Universal Semantic Manifold (USM)

Research code and notebooks for **The Universal Semantic Manifold**: explicit semantic geometry on the Poincaré ball, compared to a Euclidean baseline on ConceptNet, cross-lingual pairs, SNLI, and CIFAR-100.

## Repository layout

| Path | Contents |
|------|----------|
| [`paper/`](paper/) | LaTeX source (remove when you only ship the PDF) and **where the compiled PDF belongs** |
| [`notebooks/`](notebooks/) | Runnable experiments: small-scale validation vs. large-scale cloud run |

## Notebooks

- **`notebooks/usm_small-scale.ipynb`** — Validation-scale run where the hyperbolic (Poincaré) model beats the Euclidean baseline on KG link prediction (e.g. MRR) and hierarchy depth metrics.
- **`notebooks/usm_big-scale.ipynb`** — Large-scale A100-style run; documents optimisation challenges when scaling hyperbolic training.

## Paper (PDF)

**Put your compiled PDF here:** `paper/usm_paper.pdf` (same directory as the `.tex`, recommended filename so links stay stable).

Build from the LaTeX in `paper/` with `pdflatex` (or your usual toolchain). You can remove `paper/usm_paper.tex` after publishing if you only want the PDF in the repo.

## Requirements

The notebooks assume a Python environment with PyTorch, transformers, datasets, CLIP / OpenCLIP, geoopt (or equivalent Riemannian ops), and standard scientific stack. Exact versions depend on your machine; inspect imports at the top of each notebook.

## Citation

If you use this work, please cite the paper once it is public (see `paper/usm_paper.pdf` when available).

## License

See [LICENSE](LICENSE). The LaTeX/paper text may carry separate terms; the notebooks and supporting files are offered under the repository license unless you state otherwise.
