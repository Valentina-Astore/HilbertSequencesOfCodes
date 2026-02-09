# README — Magma Implementations for Hilbert Sequences of Codes

## Overview

This repository contains **Magma implementations** supporting the experimental results described in the paper:

**Valentina Astore, Martino Borello, Marco Calderini, Flavio Salizzoni,**
*“A Geometric Invariant of Linear Rank-Metric Codes”* (2024).

The goal of these scripts is to study **$\mathbb{F}_q$-dimension sequences** (also called *Hilbert sequences*) and the **Castelnuovo–Mumford regularity** of linear codes by analyzing the **Schur powers** of their **associated Hamming-metric codes**.

Two related but distinct experimental settings are covered:

* the **rank-metric case** (single block),
* the more general **sum-rank metric case** (multiple blocks).

---

## Repository Contents

The repository currently contains two main Magma scripts.

### `HilbertSequences.mag`

This file corresponds to the original experimental setting of the paper and implements:

* **Rank-metric codes** (single block)

  * Gabidulin codes
  * Random linear codes
* Construction of the **associated Hamming-metric code**
* Computation of:

  * Schur products and Schur powers
  * $\mathbb{F}_q$-dimension (Hilbert) sequences
  * Castelnuovo–Mumford regularity

The experiments in this file reproduce the comparisons between **Gabidulin codes and random codes** appearing, for instance, in **Figure 1 of the paper**.

---

### `HilbertSequencesSumRank.mag`

This file contains an **extended implementation** adapted to the **sum-rank metric** setting.

Implemented constructions include:

* **Multi-block Gabidulin codes**

  * Each block is a Gabidulin code obtained via GF($q$)-linear transformations
* **Linearized Reed–Solomon (LRS) codes**

  * With blockwise evaluation points and multipliers of distinct norms
* Construction of the **associated Hamming-metric code** for sum-rank codes
* Computation of:

  * Schur powers
  * Hilbert (dimension) sequences
  * Castelnuovo–Mumford regularity

---

## Implemented Functions (common to both files)

* **`SchurProduct(C, D)`**
  Computes the componentwise (Schur) product of two linear codes.

* **`SchurPower(C, e)`**
  Computes the *e*-th Schur power of a code by iterated Schur products.

* **`CM_Regularity(C)`**
  Computes the Castelnuovo–Mumford regularity of a code, while printing the dimensions of successive Schur powers until stabilization.

* **`AssociatedHammingCode(...)`**
  Constructs the Hamming-metric code associated with a rank-metric or sum-rank metric code, following the definitions used in the paper.

---

## Usage

1. Open the Magma environment.

2. Load one of the scripts, depending on the setting of interest:

   ```magma
   > load "HilbertSequences.mag";
   ```

   or

   ```magma
   > load "HilbertSequencesSumRank.mag";
   ```

3. Set the global parameters at the beginning of the file (e.g. `q`, `m`, `k`, block sizes).

4. Run the provided test sections or call the functions directly.

### Example (rank-metric case)

```magma
q := 2;
m := 4;
n := 6;
k := 3;

CM_Regularity(GH);
CM_Regularity(RH);
```

---

## Dependencies

* **Magma Computer Algebra System**
  W. Bosma, J. Cannon, C. Playoust,
  *The Magma algebra system I: The user language*,
  Journal of Symbolic Computation 24 (1997).
