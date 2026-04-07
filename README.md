# ICML-rebuttal for Paper 12031

### Controlled analysis on MVTec-AD with a fixed anomaly-free training set and varying test-set proportion

Numbers denote the performance gain of RAD over Dinomaly.

| Method | Train proportion | Test proportion | P-AUROC | P-AP | P-F1 | AUPRO |
|---|---:|---:|---:|---:|---:|---:|
| Dinomaly | 100% | 100% | 98.4 | 69.3 | 69.2 | 94.8 |
| RAD | 100% | 40% | +0.1 | +6.8 | +2.7 | +1.6 |
| RAD | 100% | 60% | +0.2 | +6.9 | +2.6 | +1.5 |
| RAD | 100% | 80% | +0.1 | +6.2 | +2.0 | +1.2 |
| RAD | 100% | 100% | +0.1 | +6.3 | +2.1 | +1.0 |


### Sensitivity sweeps on MVTec-AD

#### Top-K sweep (ρ=1, ω<sub>l</sub>=[1,1,1,1])

| Setting | I-AUROC | I-F1 | P-AP | P-F1 |
|---|---:|---:|---:|---:|
| K=5 | 98.6 | 97.7 | 72.9 | 69.3 |
| K=10 | 99.1 | 98.1 | 74.1 | 70.1 |
| K=20 | 99.3 | 98.4 | 74.8 | 70.7 |
| K=50 | 99.4 | 98.7 | 75.3 | 71.1 |
| K=100 | 99.5 | 98.8 | 75.5 | 71.2 |
| **K=150** | 99.6 | 99.0 | 75.6 | 71.3 |
| K=200 | 99.5 | 98.9 | 75.6 | 71.3 |

#### Radius sweep (K=150, ω<sub>l</sub>=[1,1,1,1])
The radius ρ is defined on the discrete patch grid and therefore only takes integer values.

| Setting | I-AUROC | I-F1 | P-AP | P-F1 |
|---|---:|---:|---:|---:|
| ρ=0 | 98.9 | 98.3 | 74.9 | 70.5 |
| **ρ=1** | 99.6 | 99.0 | 75.6 | 71.3 |
| ρ=2 | 99.5 | 98.9 | 75.5 | 71.2 |
| ρ=3 | 99.5 | 98.9 | 75.5 | 71.2 |
| ρ=4 | 99.4 | 98.9 | 75.4 | 71.2 |
| ρ=6 | 99.3 | 98.8 | 75.3 | 71.1 |
| ρ=8 | 99.2 | 98.7 | 75.2 | 70.9 |
| ρ=10 | 98.9 | 98.4 | 74.9 | 70.6 |

#### Layer-fusion sweep (K=150, ρ=1)
The single-layer results(first four lines) are provided only as ablations, as RAD is fundamentally a multi-layer method. Here, ω<sub>l</sub> = [x₁, x₂, x₃, x₄] denotes the score weights assigned to layers 4, 7, 10, and 12, respectively.
| Setting | I-AUROC | I-F1 | P-AP | P-F1 |
|---|---:|---:|---:|---:|
| ω<sub>l</sub>=[1,0,0,0] | 96.6 | 96.5 | 65.5 | 64.1 |
| ω<sub>l</sub>=[0,1,0,0] | 99.2 | 98.4 | 71.0 | 68.6 |
| ω<sub>l</sub>=[0,0,1,0] | 99.4 | 98.8 | 72.3 | 68.9 |
| ω<sub>l</sub>=[0,0,0,1] | 99.5 | 99.0 | 71.2 | 66.9 |
| **ω<sub>l</sub>=[1,1,1,1]** | 99.6 | 99.0 | 75.6 | 71.3 |
| ω<sub>l</sub>=[4,1,1,1] | 99.4 | 98.6 | 76.0 | 71.7 |
| ω<sub>l</sub>=[1,4,1,1] | 99.4 | 98.7 | 74.4 | 70.8 |
| ω<sub>l</sub>=[1,1,4,1] | 99.5 | 98.8 | 74.2 | 70.4 |
| ω<sub>l</sub>=[1,1,1,4] | 99.6 | 99.0 | 75.2 | 70.5 |
| ω<sub>l</sub>=[4,4,1,1] | 99.4 | 98.6 | 74.7 | 71.1 |
| ω<sub>l</sub>=[1,4,4,1] | 99.5 | 98.8 | 74.0 | 70.5 |
| ω<sub>l</sub>=[1,1,4,4] | 99.5 | 98.9 | 75.2 | 70.7 |
| ω<sub>l</sub>=[1,2,3,4] | 99.5 | 98.9 | 75.4 | 70.9 |
| ω<sub>l</sub>=[4,3,2,1] | 99.4 | 98.6 | 74.9 | 71.2 |
