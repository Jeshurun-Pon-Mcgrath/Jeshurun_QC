# Sensor Fault Detection with Deutsch’s Algorithm

Quantum Computing — Third Internal Project. A self-contained Google Colab and Qiskit implementation of all four Boolean sensor oracles and their classification with one logical oracle query per execution.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Jeshurun-Pon-Mcgrath/Jeshurun_QC/blob/main/jeshurun.ipynb)

## Run the project

Open [jeshurun.ipynb](jeshurun.ipynb) in Colab, select a Python 3 CPU runtime, and choose **Runtime → Run all**. The first code cell installs pinned dependencies; internet is required for installation. If packages were imported before installation, restart the runtime and run all again. No credentials, hardware backend, external dataset, or additional project files are needed.

The notebook contains the entire codebase and report. Saved outputs include circuit diagrams, result tables, and static graphs. An optional widget explorer reruns experiments; the static sections work independently of widgets. Change `SHOTS`, `NOISE_SHOTS`, or `ERROR_RATES` to regenerate results. Seeds are fixed for reproducibility within the recorded package environment.

For local use, open the notebook in Jupyter with a Python kernel and run its setup cell. Validation was performed with Python 3.12 and the pinned versions printed in the notebook; the Google Colab service itself was not used for validation.

## Expected ideal results

| Sensor rule | f(0) | f(1) | Class | Measured input bit | Diagnosis | Queries per execution |
|---|---:|---:|---|---:|---|---:|
| f(x) = 0 | 0 | 0 | Constant | 0 | Faulty | 1 |
| f(x) = 1 | 1 | 1 | Constant | 0 | Faulty | 1 |
| f(x) = x | 0 | 1 | Balanced | 1 | Working | 1 |
| f(x) = 1 XOR x | 1 | 0 | Balanced | 1 | Working | 1 |

At 1024 ideal shots per oracle, the expected bit occurs 1024 times. Each shot is a separate one-query execution: the four-oracle batch uses 4096 queries in total. One query refers to coherent access to a reversible oracle, not to a physical classical sensor or the complete repeated simulation.

## Notebook contents

- Problem definition, assumptions, and syllabus mapping.
- All four reversible oracles and 16 computational-basis mapping checks.
- Unitarity checks, phase-kickback derivation, and four Deutsch circuit diagrams.
- Exact statevector probabilities and Aer measurement results with assertions.
- Ideal probability and classical-versus-quantum query-count graphs.
- Bloch-component state evolution and global-phase equivalence checks.
- Synthetic readout-noise sweep, theoretical accuracy, and Wilson confidence intervals.
- Optional interactive sensor, shot-count, and noise controls.
- Analysis, resource accounting, limitations, references, and viva prompts.

## Syllabus alignment

The core covers Module 1 (state vectors and superposition), Module 2 (X, H, CX and circuits), Module 3 (measurement and the distinction between superposition and entanglement), and Module 4 (Deutsch’s algorithm and query complexity). The readout-noise extension connects to Module 6’s error-related topics without claiming to implement error correction. QFT and phase estimation in Module 5 are outside the assigned problem.

## Interpretation and individual study

The ideal algorithm exactly classifies constant versus balanced rules; it does not identify the particular rule within a class. The optional noise experiment models only symmetric readout errors, with expected per-shot accuracy 1 − p. It is not a hardware benchmark or a real sensor deployment.

Understand every cell before presenting. Add your student details, rerun the experiments, record your own observations, and follow your institution’s assistance-disclosure rules. The notebook includes self-check questions to support an individual explanation.
