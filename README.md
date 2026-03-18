# 🧬 Molecular Interaction Fingerprinting & Pharmacophore Analysis

> **Reproducible, beginner-friendly Jupyter notebooks for PLIP-based protein–ligand interaction fingerprinting and SMILES-driven pharmacophore feature extraction — with built-in reproducibility validation at every stage.**

---

## 📦 Repository Contents

```
├── notebooks/
│   ├── 01_PLIP_Fingerprinting.ipynb        # Protein–ligand interaction fingerprinting & clustering
│   └── 02_Pharmacophore_Analysis.ipynb     # SMILES-based pharmacophore feature visualization
├── sample_pdbs/                            # Fallback PDB complexes for Notebook 1
└── README.md
```

> **Note:** Only the notebooks, sample PDB files, and this README are shared in this repository.
> Output files are generated locally upon running the notebooks.

---

## 🔄 Repository Updates

This repository is actively maintained.
Any new notebooks or pipelines developed under the themes of **interaction fingerprinting** and **pharmacophore analysis** will be added here, along with updated documentation and README files.
Watch or star the repository to stay notified of new additions.

---

## 📓 Notebook 1 — PLIP Interaction Fingerprinting & Clustering

### Overview

This notebook performs **protein–ligand interaction fingerprinting** on a set of PDB co-crystal complexes using [PLIP (Protein–Ligand Interaction Profiler)](https://github.com/pharmai/plip). It is designed to be fully self-contained, beginner-friendly, and reproducible.

### Input

A folder of `.pdb` complex files named in the format:

```
C1_3PXY.pdb
C2_4ABC.pdb
```

The folder can be supplied via a **Google Drive path** (for Colab users). If no folder is available, a set of **sample PDB files** is included in the repository and configured as an automatic fallback within the notebook.

> 💡 All sections requiring user edits are clearly marked inside the notebook with `# ✏️ EDIT HERE` comments.

### Outputs

| File | Description |
|------|-------------|
| `PLIP_heatmap_total.png` | Aggregated interaction fingerprint heatmap across all complexes |
| `PLIP_stacked_bar.png` | Stacked bar chart of interaction type distribution per complex |
| `PLIP_per_target_heatmaps.png` | Individual per-target interaction heatmaps |
| `PLIP_full_fingerprints.xlsx` | Full interaction fingerprint matrix (Excel) |

### Reproducibility Validation

The notebook includes structured reproducibility checks to ensure consistent outputs across environments:

| Check | Method |
|-------|--------|
| Identical PDB inputs | Same input files verified before processing |
| Dependency versioning | Environment snapshot with pinned versions |
| Deterministic processing | No random seeds involved; processing is fully deterministic |
| Dataframe equality | Output DataFrames compared element-wise across runs |
| Hash-based comparison | MD5 hashes computed on fingerprint outputs |
| Output file consistency | File-level consistency checks on all generated outputs |

**Structural Validation Steps:**

- Verified presence of protein (`ATOM`) and ligand (`HETATM`) records in each PDB
- Ensured interaction detection consistency across complexes
- Compared interaction patterns across targets for cross-target coherence

---

## 📓 Notebook 2 — SMILES-Based Pharmacophore Feature Visualization

### Overview

This notebook accepts a **SMILES string** as input and performs pharmacophore feature extraction using RDKit. It generates an annotated visual map of the key chemical features present in the molecule — rendered as a downloadable PNG image.

### Input

- User-provided SMILES string entered interactively within the notebook
- No file upload required

### Output

- **Pharmacophore feature image (PNG)** — an annotated 2D depiction of the molecule with pharmacophore features labeled and color-coded, including:
  - 🔵 Hydrogen Bond Donors (HBD)
  - 🔴 Hydrogen Bond Acceptors (HBA)
  - 🟡 Hydrophobic Centers
  - 🟢 Aromatic Rings

  The image renders inline within the notebook and can be downloaded directly to the local system.

### Reproducibility Validation

To ensure that pharmacophore results are consistent and input-independent across runs, five validation checks are embedded directly within the notebook.

**Check 1 — Canonical SMILES Consistency**

The input SMILES is parsed and re-canonicalized twice independently using RDKit. Both outputs are compared to confirm that the molecular structure is interpreted identically on every execution, regardless of input formatting variation.

**Check 2 — Pharmacophore Feature Extraction Consistency**

Pharmacophore features (family type and contributing atom indices) are extracted in two independent passes from the same molecule object. The resulting feature lists are compared element-wise to confirm that RDKit's feature factory produces deterministic output for a given structure.

**Check 3 — Hash-Based Fingerprint Verification**

MD5 hashes are computed over the serialized feature lists from both extraction passes. A matching hash pair confirms bit-level reproducibility of the pharmacophore profile — providing a compact, shareable fingerprint of the result for cross-environment validation.

**Check 4 — Reference Molecule Sanity Check**

Ethanol (`CCO`) is used as a minimal, well-characterized reference molecule to verify that the RDKit parsing and atom-counting pipeline is functioning correctly in the current environment before processing the user-supplied compound.

**Check 5 — Feature Detection Confirmation**

The total count of detected pharmacophore features is reported and checked against a non-zero threshold. This guards against silent failures in feature extraction — for example, malformed SMILES or unsupported functional groups — and prompts the user to review their input if no features are returned.

---

## 🛠️ Dependencies

### Notebook 1 — PLIP Fingerprinting

- `plip`
- `biopython`
- `pandas`, `numpy`
- `matplotlib`, `seaborn`
- `openpyxl`

### Notebook 2 — Pharmacophore Feature Visualization

- `rdkit`
- `matplotlib`

> Install all dependencies via the first cell of each notebook, or use the provided `requirements.txt`.

---

## 🚀 Quick Start

### Notebook 1

1. Upload your folder of `.pdb` complex files to Google Drive (or use the included sample PDBs)
2. Open `01_PLIP_Fingerprinting.ipynb` in Google Colab or JupyterLab
3. Edit only the clearly marked `# ✏️ EDIT HERE` cells (Google Drive path or local folder path)
4. Run all cells — outputs are saved automatically

### Notebook 2

1. Open `02_Pharmacophore_Analysis.ipynb`
2. Enter your SMILES string when prompted
3. Run all cells — the pharmacophore feature image renders inline and can be downloaded to your local system

---

## 💬 Questions & Discussions

Doubts, questions, and feedback are very welcome.
Feel free to raise an issue in this repository or reach out directly at:

📧 **abhirami.insightgenomics@gmail.com**

---

## 📌 Citation

If you use these notebooks in your research, thesis, or project, please cite this repository:

```
Thoughtsofabhirami (2025). Molecular Interaction Fingerprinting & Pharmacophore Analysis —
Reproducible PLIP and RDKit Notebooks. GitHub.
https://github.com/Thoughtsofabhirami/fingerprint-pharmacophore-toolkit
```

Attribution is not mandatory under the MIT License, but it is greatly appreciated and helps support open research.

---

## 📄 License

This repository is released under the [MIT License](LICENSE).

You are free to use, modify, and distribute this work for any purpose — academic, research, or commercial — with no restrictions beyond retaining the original copyright notice.

---

## 🔖 Topics

`plip` · `pharmacophore` · `protein-ligand-interactions` · `cheminformatics` · `molecular-docking` · `structural-bioinformatics` · `jupyter-notebook` · `reproducible-research` · `drug-discovery` · `rdkit`

---

## 🙏 Acknowledgements

- [PLIP — Protein–Ligand Interaction Profiler](https://github.com/pharmai/plip) (Salentin et al.)
- [RDKit — Open-Source Cheminformatics](https://www.rdkit.org/)
