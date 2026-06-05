# When Gradients Collide: Failure Modes of Multi-Objective Prompt Optimization for LLM Judges

[![ACL 2026](https://img.shields.io/badge/ACL-2026-blue.svg)](https://2026.aclweb.org/)
[![CustomNLP4U](https://img.shields.io/badge/Workshop-CustomNLP4U-green.svg)](https://customnlp4u.github.io/)

This repository contains the source code for the paper website: **"When Gradients Collide: Failure Modes of Multi-Objective Prompt Optimization for LLM Judges"**, presented at the CustomNLP4U Workshop @ ACL 2026.

**Website:** https://when-gradients-collide.github.io

## Abstract

Customizing an LLM judge to a specific problem or domain often involves optimizing its prompt across multiple evaluation criteria simultaneously. Textual gradient methods automate this for a single judge criterion, however they produce natural-language critiques, not numerical vectors. Thus, the conflict-resolution toolkit of multi-task learning (PCGrad, MGDA) does not apply to this multi-objective textual gradient setting.

We extend TextGrad to the multi-objective setting and test four decomposition modes of textual gradient optimizers by varying how much cross-objective information the loss, gradient and optimizer LLMs share. We find the gradient's task-focus drops by **59%** (9.0 to 3.7 out of 10) when the gradient LLM must provide feedback on multiple criteria jointly. Separately, we observe that naively combining single-objective optimized instructions into a single prompt degrades Spearman ρ from **0.305 to 0.220** (−0.085). These results identify two separable failure modes:

1. **Optimization-time gradient dilution** — gradient LLM produces generic feedback when handling multiple criteria simultaneously
2. **Inference-time instruction interference** — combined optimized instructions interfere with each other during evaluation

## Authors

- **Parth Darshan** (IIT Jodhpur)
- **Abhishek Divekar** (Amazon) — *Research Lead and Corresponding Author*

## Key Findings

- **Four decomposition modes tested**: SSS (Separate loss, Separate gradient, Separate optimizer), SSC (Separate loss, Separate gradient, Combined optimizer), SCC (Separate loss, Combined gradient, Combined optimizer), CCC (Combined loss, Combined gradient, Combined optimizer)
- **Gradient dilution is structural**: 59% specificity drop persists even when swapping to DeepSeek-V4-Pro as the gradient LLM
- **Feedback adherence is uniformly high**: 7.7-8.8/10 across all modes, indicating the optimizer is not the bottleneck
- **Cherry-pick experiment reveals interference**: Oracle-optimal single-task instructions degrade when combined (-0.085 Spearman)
- **DeepSeek v4 shows better absolute performance**: +0.117 improvement for single-task, +0.026 to +0.039 for multi-task modes, but the same structural failure patterns persist

## Citation

```bibtex
@inproceedings{darshan2026whengradientscollide,
  title={When Gradients Collide: Failure Modes of Multi-Objective Prompt Optimization for LLM Judges},
  author={Darshan, Parth and Divekar, Abhishek},
  booktitle={Proceedings of the 64th Annual Meeting of the Association for Computational Linguistics (ACL 2026)},
  year={2026},
  url={https://when-gradients-collide.github.io}
}
```

## Website Template

This website is built using the [Academic Project Page Template](https://github.com/eliahuhorwitz/Academic-project-page-template), which is based on the [Nerfies](https://nerfies.github.io/) project page. The template is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/).

## License

This website is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

---

**Keywords:** multi-objective optimization, textual gradients, LLM judges, prompt optimization, TextGrad, gradient dilution, instruction interference
