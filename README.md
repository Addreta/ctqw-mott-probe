# ctqw-mott-probe
# CTQW as a Probe of the Mott Transition in the 1D Fermi-Hubbard Model
### OBDM Graph | Spectral Gap | Centrality Divergence
A classical simulation study using continuous-time quantum walks on the 
one-body density matrix to detect the Mott crossover, with a connection 
to digital Hamiltonian simulation on near-term quantum hardware.

## Motivation
This work is motivated by a recent paper:
Shah Ishmam Mohtashim, Manas Sajjan, Sabre Kais (2026)
Continuous-time quantum-walk centrality for protein residue interaction networks

This study applies the CTQW centrality framework to a physically derived 
graph: the one-body density matrix (OBDM) of the Hubbard ground state
and shows that CTQW observables detect the Mott crossover as U/t varies.

## Methods
| Step | Tool | Key quantity |
|------|------|-------------|
| Exact diagonalization | QuSpin | Ground state |GS⟩ |
| OBDM construction | NumPy | ρ_ij = ⟨GS|c†_i c_j|GS⟩ |
| CTQW centrality | NumPy (spectral decomp.) | Long-time avg. occupation π_j |
| Classical eigenvector centrality | NumPy | Leading eigenvector of ρ |
| Spectral gap | NumPy | λ_1 − λ_2 of ρ |

## Key Results
- OBDM off-diagonal elements decay with both distance |i−j| and U/t — 
  single-particle correlations localize as the system enters the Mott phase
- Spectral gap of the OBDM graph peaks non-monotonically at U/t ≈ 6–8, 
  providing a graph-theoretic signature of the Mott crossover
- CTQW centrality remains flat across all sites for all U/t — quantum 
  interference erases the edge-bulk distinction that classical EC detects
- Quantum-classical centrality divergence ||π_CTQW − π_EC||₂ grows 
  monotonically with U/t, quantifying interference deepening into Mott phase

## Notebooks
- `ctqw_hubbard.ipynb` — ED, OBDM construction, CTQW analysis, all plots

## Requirements
pip install quspin numpy scipy matplotlib

## References
Shah Ishmam Mohtashim, Manas Sajjan, Sabre Kais (2026)
