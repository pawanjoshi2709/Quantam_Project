# Grover's Algorithm — 10-Qubit Implementation
**Author:** Pawan Joshi | Quantum Computing Course Project

Implements Grover's quantum search algorithm from scratch using Qiskit, finding 2 marked states across a 1024-state search space with ~99.9% success probability — demonstrating the quadratic speedup over classical search.

---

## What It Does

- Searches a **10-qubit space** (2¹⁰ = 1024 states) for two hidden targets: `0110011010` and `1101010001`
- Builds two oracle types from scratch — **no built-in Grover functions used**
- Runs the algorithm at k = 1, 3, 5, 10, and the optimal k = 17 iterations
- Simulates with 8192 shots using the Qiskit Aer local simulator
- Plots histograms comparing measured vs. theoretical probabilities

---

## Project Structure

| Section | Description |
|---|---|
| Section 1 | Oracle A — IBM-style (MCMTGate + Z) |
| Section 2 | Grover Diffuser — manual H·X·MCZ·X·H |
| Section 3 | Oracle B — Phase Kickback (MCX + ancilla) |
| Section 4–8 | Full circuit runs at various k values with histograms |
| Section 9 | Summary table comparing Part A vs Part B results |

---

## Two Implementations Compared

**Part A — IBM-style Oracle**
- Uses `MCMTGate(ZGate(), ...)` with open-control X gates
- 10 qubits, no ancilla

**Part B — Phase Kickback Oracle**
- Uses `mcx` into an ancilla qubit prepared in |−⟩
- 11 qubits (10 data + 1 ancilla, returned to |0⟩ after use)

Both achieve **P(marked) ≈ 99.9%** at k = 17.

---

## Install

```bash
pip install qiskit qiskit-aer matplotlib
```

## Run

```bash
jupyter notebook Pawan-Joshi-Grovers-Algorithm-Project.ipynb
```

Then run all cells top to bottom.

## Requirements

- Python 3.12+
- Jupyter Notebook / JupyterLab
