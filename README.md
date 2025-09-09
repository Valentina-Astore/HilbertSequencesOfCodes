# README — Magma Implementations for Hilbert Sequences of Codes

## Overview

This repository contains Magma implementations of the experiments described in the paper:

**Valentina Astore, Martino Borello, Marco Calderini, Flavio Salizzoni,
"A Geometric Invariant of Linear Rank-Metric Codes" (2024).**

The aim is to study the **Fq-dimension sequences** (Hilbert sequences) and the **Castelnuovo–Mumford regularity** of Gabidulin codes versus random linear codes, by analyzing the Schur powers of their associated Hamming-metric codes.

## Contents

The provided Magma script implements the following:

* **SchurProduct(C, D)**
  Computes the componentwise (Schur) product of two linear codes.

* **SchurPower(C, e)**
  Computes the *e*-th Schur power of a code by iterated Schur products.

* **CM\_Regularity(C)**
  Computes the Castelnuovo–Mumford regularity of a code, while printing the sequence of dimensions of successive Schur powers until stabilization.

* **AssociatedHammingCode(C)**
  Constructs the Hamming-metric code associated with a rank-metric code, following the definition in the paper.

* **Code constructions**

  * *Gabidulin codes*: constructed using powers of a normal element of the extension field.
  * *Random codes*: constructed via a systematic generator matrix with random entries.
  * *Extended Hamming-metric codes*: obtained from the associated Hamming construction.

* **Example tests**
  At the end of the file, the Castelnuovo–Mumford regularity of the extended Hamming-metric versions of Gabidulin and random codes is computed and printed. These reproduce the experimental comparisons shown in Figure 1 of the paper.

## Usage

1. Open the Magma environment.
2. Load the script:

   ```magma
   > load "filename.m";
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

## Dependencies

* Requires the **Magma Computer Algebra System**:
  W. Bosma, J. Cannon, C. Playoust, *The Magma algebra system I: The user language*, J. Symbolic Computation 24 (1997).
