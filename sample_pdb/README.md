# Sample PDB Dataset

This folder contains example protein–ligand complexes for testing the fingerprint analysis notebook.

## Dataset Description

- Total complexes: 16
- Format: `.pdb`

## Compounds

| Code | Name |
|------|------|
| C1 | Tofacitinib |
| C2 | Indicine |
| C3 | Apigenin |
| C4 | Disulfiram |

## Proteins (Targets)

| PDB ID | Description |
|--------|------------|
| 3PXY | Protein target 1 |
| 6GGH | Protein target 2 |
| 4O75 | Protein target 3 |
| 1SQN | Protein target 4 |

## File Naming Convention

Each file follows:

<Compound>_<Protein>.pdb

### Example:
C1_3PXY.pdb

## Notes !

- Each file should contain both:
  - `ATOM` records (protein)
  - `HETATM` records (ligand)

- These are **docked complexes**, suitable for interaction analysis.

## Usage

This dataset is used as a **demo mode** in the notebook when no user data is provided.