# GateBreaker – Bachelor Project Fork

This repository contains my working copy of **GateBreaker**, the research artifact accompanying the paper *"GateBreaker: Gate-Guided Attacks on Mixture-of-Expert LLMs"* (USENIX Security 2026). I use it as the basis for my bachelor project at the University of Duisburg-Essen. In it I study, adapt and extend the framework in my own way.

> **Disclaimer:** This is not the official repository. All credit for the original method and code goes to the original authors. This fork is for research and educational purposes only, in line with the original artifact's research-only scope.

---

## About GateBreaker

GateBreaker is a training-free, inference-time framework that analyzes how safety alignment is organized inside Mixture-of-Experts (MoE) LLMs. It works in three stages:

1. **Gate-level profiling:** identifies experts that the router selects disproportionately often for harmful inputs.
2. **Expert-level localization:** locates the small set of safety-relevant neurons within those experts.
3. **Targeted safety removal:** neutralizes these neurons at inference time to measure how much of the model's refusal behavior depends on them.

The paper shows that safety in MoE models is concentrated in a very small fraction of neurons. This points to a structural weakness that current alignment methods do not address.

## Original Work

- **Paper:** L. Wu, S. Behrouzi, M. Rostami, S. Picek, A.-R. Sadeghi. *GateBreaker: Gate-Guided Attacks on Mixture-of-Expert LLMs.* 35th USENIX Security Symposium, 2026, pp. 2167–2185.
- **Original artifact:** https://doi.org/10.5281/zenodo.17910455

```bibtex
@inproceedings{wu2026gatebreaker,
  title     = {GateBreaker: Gate-Guided Attacks on Mixture-of-Expert LLMs},
  author    = {Wu, Lichao and Behrouzi, Sasha and Rostami, Mohamadreza and Picek, Stjepan and Sadeghi, Ahmad-Reza},
  booktitle = {35th USENIX Security Symposium (USENIX Security 26)},
  pages     = {2167--2185},
  year      = {2026}
}
```

## What This Fork Is About

I take the original artifact as a starting point and adapt it step by step for my own experiments. Changes are documented below as the project progresses.

### Changes so far

- Added an `environment.yml`, because the original artifact does not include one, although its README refers to it.
- Adjusted the hard-coded GPU device configuration for single-GPU environments.

### Planned

- Document reproducibility gaps between the paper and the artifact.
- Further adaptations and experiments as defined with my supervisor.

## Repository Structure

```
src/
├── main.py                    # Entry point of the pipeline
├── activation_extractor.py    # Collects neuron activations via hooks
├── compute_graph_patcher.py   # Runtime patching of fused MoE layers
├── moe_model_config.py        # Per-model architecture configuration
├── util.py / util_model.py    # Helpers (data loading, model loading, evaluation)
└── data/                      # Precomputed safety weights and output folders
environment.yml                # Environment definition (added in this fork)
```

## Responsible Use

This code deals with removing safety alignment from language models. It is meant strictly for academic research on AI safety, carried out within the framework of my bachelor project. Please do not use it to generate or distribute harmful content.

## License

The original artifact is licensed under the **GNU General Public License v3.0 or later**. This fork is distributed under the same license. See the original artifact for the full license terms.
