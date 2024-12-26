# Event-triggered Social Media Chatter Model (Julia Implementation)

**Authors:**
- Gabriel José Souza e Silva ([gabriel.jsss@poli.ufrj.br](mailto:gabriel.jsss@poli.ufrj.br))
- Matheus Marinatto ([marinattomatheus@poli.ufrj.br](mailto:marinattomatheus@poli.ufrj.br))

---

## Contents
1. [Introduction and Problem Description](#introduction)
2. [Mathematical Modeling](#modeling)
3. [Control Techniques](#control-techniques)
   - [Optimal Control](#optimal-control)
   - [Model Predictive Control (MPC)](#mpc)
   - [Handling Uncertainties](#uncertainties)
4. [Results](#results)
5. [Conclusion](#conclusion)

---

## Introduction and Problem Description <a name="introduction"></a>

This project explores a social media chatter model inspired by marketing dynamics, optimizing information spread with various control techniques. It addresses the challenge of balancing message amplification efficiency against budget and time constraints. 

The model builds on the Vidale-Wolfe framework, adapted to capture social media interactions:

- **Objective:** Maximize information spread while minimizing costs.
- **Key Features:** Incorporates traditional advertising effects and organic social media sharing dynamics.

---

## Mathematical Modeling <a name="modeling"></a>

The Vidale-Wolfe-based model considers parameters such as the social marketing constant, interaction effects, and budget constraints. Key equations include:

1. **Event-triggered Social Media Chatter Model**: $\dot{S}(t) = \beta_1 U(t) (1 - S(t)) + \beta_2 S(t)(1 - S(t)) - \delta S(t)$

2. **Cost Function**: $J = \int_0^T \left( U(t)^2 + (S(t) - S_{\text{desired}})^2 + \lambda \right) dt$

3. **Equilibrium Point**: $S_{\text{eq}} = 1 - \frac{\delta}{\beta_2}$

---

## Control Techniques <a name="control-techniques"></a>

### Optimal Control <a name="optimal-control"></a>

Explores the use of cost functions to achieve equilibrium, either minimizing time or balancing costs. Budget constraints are introduced in some variations.

### Model Predictive Control (MPC) <a name="mpc"></a>

Uses a prediction horizon to adjust actions dynamically while respecting budget limitations. Scenarios include:
- Without Budget Constraints
- With Budget Constraints

### Handling Uncertainties <a name="uncertainties"></a>

Examines robustness of control strategies under parameter uncertainties (e.g., misestimation of \( $\beta_1$, $\beta_2$, $\delta$ \)).

---

## Results <a name="results"></a>

### Summary Tables

#### Without Budget Constraints
| Control Type | Total Control Effort (\(\Sigma U\)) | Iteration to Reach Equilibrium |
|--------------|--------------------------------------|--------------------------------|
| Optimal Control (3.1.1) | 2.776 | 55 |
| Simplified Cost Function (3.2.1) | 3.333 | 2 |
| MPC (3.3.1) | 3.237 | 32 |

#### With Budget Constraints $(\(\Sigma U \leq 2.5, U_t \leq 0.1\))$
| Control Type | Total Control Effort ($\(\Sigma U\)$) | Iteration to Reach Equilibrium |
|--------------|--------------------------------------|--------------------------------|
| Optimal Control (3.1.2) | 2.5 | 74 |
| Simplified Cost Function (3.2.2) | 2.5 | 80 |
| MPC (3.3.2) | 2.364 | 59 |

#### Uncertainties
All control strategies struggled under parameter uncertainties, stabilizing at different set points.

### Plots
Plots illustrating performance across iterations are included in the `assets` folder.

---

## Conclusion <a name="conclusion"></a>

- **Without Budget Constraints:**
  - The simplified cost function (3.2.1) is most effective, reaching equilibrium 22.5 times faster despite being 16% more expensive than traditional optimal control (3.1.1).

- **With Budget Constraints:**
  - MPC (3.3.2) outperforms, reaching equilibrium faster with less total control effort.

- **Under Uncertainties:**
  - All strategies show limitations, requiring additional constraints to force equilibrium under uncertain dynamics.

---

