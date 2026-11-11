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
| OBDM construction | QuSpin + NumPy | ρ_ij = ⟨GS| c†_i c_j |GS⟩ summed over spin | 
| CTQW centrality | NumPy (spectral decomp.) | Long-time avg. occupation π_j |
| Classical eigenvector centrality | NumPy | Leading eigenvector of ρ |
| Spectral gap | NumPy | λ_1 − λ_2 of ρ |

## Key Results
- |ρ_ij| decreases with U/t and with distance (L=6, open boundaries); even-distance elements vanish by particle-hole symmetry.
- OBDM spectral gap peaks non-monotonically at U/t ≈ 6-8 (8 values sampled). It must vanish as U→0 and U→∞, so the peak alone is not a Mott signature.
- CTQW centrality is more bulk-concentrated than classical EC at every sampled U/t. It is essentially the squared leading eigenvector, which is sharper than the amplitude EC uses.
- ‖CTQW − EC‖₂ varies little (0.071–0.077), with a shallow maximum near U/t = 4. It does not converge at large U/t; CTQW instead approaches the squared leading eigenvector.
## Notebooks
- `ctqw_hubbard.ipynb` — ED, OBDM construction, CTQW analysis, all plots

## Requirements
pip install quspin numpy scipy matplotlib

## References
Shah Ishmam Mohtashim, Manas Sajjan, Sabre Kais (2026)
