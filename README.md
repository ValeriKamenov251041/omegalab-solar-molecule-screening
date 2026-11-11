# Solar-cell molecule screening

Machine learning that predicts the properties of candidate molecules for organic solar cells from
their structure, so that a lab can rank candidates before spending days synthesising them.

Individual project by Valeri Kamenov for OMEGALAB, Applied Data Science & AI, Breda University of
Applied Sciences, Year 1 Block B (November 2025 to January 2026).

## Approach

1. Read each molecule as a SMILES string and compute 217 molecular descriptors with RDKit.
2. **Classification:** sort molecules into high, medium and low stability.
3. **Regression:** predict the HOMO and LUMO energy levels (in eV), which set the voltage a cell can deliver.
4. Cluster the molecules to see where the predictions can be trusted, because the training sets come
   from different chemical families.

## Results

| Task | Result |
|---|---|
| Stability classification | F1 0.89 in cross-validation (0.95 on the held-out test set) |
| HOMO / LUMO regression | mean absolute error of 0.04 to 0.08 eV in cross-validation |

The presentation and report in `docs/` explain the results, limitations (444 molecules, mixed
chemical families) and next steps (more data, graph neural networks) for a non-technical client.

## Repository layout

| Path | Content |
|---|---|
| `notebooks/classification_training.ipynb`, `classification_inference.ipynb` | Final stability model and how to use it |
| `notebooks/regression_training.ipynb`, `regression_inference.ipynb` | Final HOMO/LUMO models |
| `notebooks/clustering.ipynb` | Chemical clustering |
| `notebooks/iterations/` | Earlier iterations |
| `docs/` | Client presentation and report |

## Data

The notebooks use the public [HOPV15 dataset](https://figshare.com/articles/dataset/HOPV15_Dataset/1610063)
and a course database, neither of which is included here. Notebook outputs are cleared.

Built with Python, pandas, RDKit and scikit-learn.
