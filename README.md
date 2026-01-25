# NC-C-with-Simplified-and-Tight-Analysis: Matrix Eigen-Structure Verification (Mathematica)

This repository contains **Mathematica notebooks** used to **reproduce and validate** the symbolic computations in **Section 5** of our paper:

> **[Smoothing Meets Perturbation: Simplified and Tight Analysis for Nonconvex-Concave Minimax Optimization]**  
> [Jiajin Li, Nanxi Zhang, Siyu Pan]  
> [arXiv / project link if available] (TBD)

In particular, the notebooks compute and simplify the **characteristic polynomial**, **eigenvalues**, and **eigenvectors** of the matrices appearing in the analysis (including *Perturbed GDA* and *Perturbed Smoothed GDA*  variants), serving as an independent check of the derivations reported in the paper.

---

## Contents

The repository consists of three Mathematica notebooks:

- **`Perturbed Smoothed GDA--GS.nb`**  
  Symbolic derivations for the Section 5 matrix associated with the *Perturbed Smoothed GDA* (GS variant):  
  - constructs the matrix \(M\) (with paper notation)  
  - computes `CharacteristicPolynomial[M, λ]`  
  - solves for eigenvalues and extracts the relevant root  
  - derives/prints eigenvectors and performs simplification checks

- **`Perturbed Smoothed GDA--OS.nb`**  
  Companion notebook for the *Perturbed Smoothed GDA* (OS variant):  
  - computes eigen-structure via `Eigensystem`  
  - extracts the eigenvalue/eigenvector used in Section 5  
  - includes symbolic simplifications consistent with the paper’s notation

- **`Perturbed GDA--GS.nb`**  
  Symbolic derivations for the *Perturbed GDA* (GS variant):  
  - computes eigenvalues/eigenvectors of the corresponding matrix  
  - performs algebraic simplifications used in the analysis

> **Note.** The labels “OS” and “GS” follow the naming in the paper and correspond to the two matrix forms analyzed in Section 5.

---

## Requirements

- Wolfram **Mathematica** (recommended: a recent version that supports `Eigensystem`, `CharacteristicPolynomial`, and `FullSimplify` reliably).
- No external packages are required.

---

## How to run

1. Open any notebook (`.nb`) in Mathematica.
2. (Recommended) **Quit the kernel** first to avoid stale definitions:
   - `Evaluation` → `Quit Kernel` → `Local`
3. Evaluate all cells:
   - `Evaluation` → `Evaluate Notebook`

The notebooks are written to be largely self-contained: all symbols (e.g., parameters such as `\[Alpha]`, `\[Beta]`, `\[ScriptL]`, `Subscript[r, x]`, `Subscript[r, y]`, etc.) are defined in the notebook before use.

---

## What to look for / expected outputs

Depending on the notebook, you will see outputs such as:
- the symbolic characteristic polynomial `F`
- closed-form solutions to `F == 0` for eigenvalues
- eigenvectors (often normalized up to scaling)
- simplification checks confirming algebraic identities used in Section 5

If you want to test numeric sanity checks, you can substitute concrete parameter values (consistent with the assumptions in the paper) and verify:
- eigenvalues match the symbolic expressions
- eigenvectors satisfy \(M v = \lambda v\)

---

## Reproducibility notes

- Symbolic results can be sensitive to assumptions. If needed, you can add global assumptions such as positivity/feasibility constraints:
  ```wolfram
  $Assumptions = {\[Alpha] > 0, \[Beta] > 0, \[ScriptL] > 0, Subscript[r, x] > 0, Subscript[r, y] > 0, c >= 0};
