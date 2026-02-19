# README — Magma Implementations for Hilbert Sequences of Codes

## Overview

This repository contains Magma implementations of the experiments described in the paper:

**Valentina Astore, Martino Borello, Marco Calderini, Flavio Salizzoni,**  
*"A Geometric Invariant of Linear Rank-Metric Codes"* (2024).

---

# File 1 — `HilbertSequences.mag` (Rank-Metric Setting)

The aim is to study the **Fq-dimension sequences** (Hilbert sequences) and the **Castelnuovo–Mumford regularity** of Gabidulin codes versus random linear codes, by analyzing the Schur powers of their associated Hamming-metric codes.

## Contents

The provided Magma script implements the following:

- **SchurProduct(C, D)**  
  Computes the componentwise (Schur) product of two linear codes.

- **SchurPower(C, e)**  
  Computes the *e*-th Schur power of a code by iterated Schur products.

- **CM_Regularity(C)**  
  Computes the Castelnuovo–Mumford regularity of a code, while printing the sequence of dimensions of successive Schur powers until stabilization.

- **AssociatedHammingCode(C)**  
  Constructs the Hamming-metric code associated with a rank-metric code, following the definition in the paper.

### Code Constructions

- **Gabidulin codes**  
  Constructed using powers of a normal element of the extension field.

- **Random codes**  
  Constructed via a systematic generator matrix with random entries.

- **Extended Hamming-metric codes**  
  Obtained from the associated Hamming construction.

### Example Tests

At the end of the file, the Castelnuovo–Mumford regularity of the extended Hamming-metric versions of Gabidulin and random codes is computed and printed. These reproduce the experimental comparisons shown in Figure 1 of the paper.

### Usage

1. Open the Magma environment.
2. Load the script:

```magma
> load "HilbertSequences.mag";
```

3. Set the parameters `q, m, n, k` at the beginning of the file to choose the field size, extension degree, code length, and dimension.
4. Run the functions to generate codes and compute their invariants.

Example:

```magma
q := 2;
m := 4;
n := 6;
k := 3;

CM_Regularity(GH);
CM_Regularity(RH);
```

---

# File 2 — `HilbertSequencesSumRank.mag` (Sum-Rank Metric Setting)

This file extends the experimental framework to the **sum-rank metric** setting.

The aim is to study the **Fq-dimension sequences** (Hilbert sequences) and the **Castelnuovo–Mumford regularity** of Linearized Reed-Solomon codes versus multi-block "random" Gabidulin codes, by analyzing the Schur powers of their associated Hamming-metric codes.

## Contents

The script implements:

- **SchurProduct(C, D)**
- **SchurPower(C, e)**
- **CM_Regularity(C)**
- **AssociatedHammingCode(seq)**  
  (adapted to accept multiple blocks)

### Code Constructions

- **Linearized Reed–Solomon (LRS) codes**  
  - Blocks with GF(q)-linearly independent evaluation points  
  - Multipliers with distinct non-zero norms  
  - Construction via successive Frobenius powers

- **Multi-block Gabidulin codes**  
  - Each block obtained from a Moore matrix  
  - Independent GF(q)-invertible transformations per block  
  - Natural sum-rank analogue of Gabidulin constructions

For both constructions, the associated Hamming-metric code is built and its Hilbert sequence and Castelnuovo–Mumford regularity are computed.

### Parameters

In this file, the global parameters are:

- `q` — base field size  
- `m` — extension degree  
- `k` — dimension  
- `N = [N1, ..., Nt]` — block lengths  
- `t` — number of blocks  
- `n = N1 + ... + Nt` — total length

Example:

```magma
q := 5;
m := 5;
k := 4;
N := [5,5,5];
```

Then load and run:

```magma
> load "HilbertSequencesSumRank.mag";
```

The script automatically constructs LRS and multi-block Gabidulin codes and prints their Hilbert sequences and regularities.

---

## Dependencies

Requires the **Magma Computer Algebra System**:

W. Bosma, J. Cannon, C. Playoust,  
*The Magma algebra system I: The user language*,  
Journal of Symbolic Computation 24 (1997).
