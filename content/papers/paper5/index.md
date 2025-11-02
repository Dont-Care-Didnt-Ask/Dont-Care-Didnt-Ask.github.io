---
title: "When Punctuation Matters: A Large-Scale Comparison of Prompt Robustness Methods for LLMs" 
date: 2025-08-15
lastmod: 2025-08-15
tags: ["research","robustness"]
author: [Mikhail Seleznyov, Mikhail Chaichuk, Gleb Ershov, Alexander Panchenko, Elena Tutubalina, Oleg Somov]
description: "This paper benchmarks a number of methods for improving robustness to prompt formatting in LLM. We find limitations of existing methods, determine the best ones depending on the usage scenario, and propose a modification of existing method tailored for black-box usage." 
summary: "This paper benchmarks a number of methods for improving robustness to prompt formatting in LLM. We find limitations of existing methods, determine the best ones depending on the usage scenario, and propose a modification of existing method tailored for black-box usage." 
cover:
    image: "whenpunct.png"
    alt: "Many methods exist for improving LLM robustness to prompt formatting. However, they were not yet compared in a unified setting or tested aginst distribution shifts."
    relative: false

---

---

##### Download

+ [Paper](https://arxiv.org/abs/2508.11383)

---

##### Abstract

Large Language Models (LLMs) are highly sensitive to subtle, non-semantic variations in prompt phrasing and formatting. In this work, we present the first systematic evaluation of 5 methods for improving prompt robustness within a unified experimental framework. We benchmark these techniques on 8 models from Llama, Qwen and Gemma families across 52 tasks from Natural Instructions dataset. Our evaluation covers robustness methods from both fine-tuned and in-context learning paradigms, and tests their generalization against multiple types of distribution shifts. Finally, we extend our analysis to GPT-4.1 and DeepSeek V3 to assess frontier models' current robustness to format perturbations. Our findings offer actionable insights into the relative effectiveness of these robustness methods, enabling practitioners to make informed decisions when aiming for stable and reliable LLM performance in real-world applications. Code: https://github.com/AIRI-Institute/when-punctuation-matters.
---

##### Citation

```BibTeX
@misc{seleznyov2025punctuationmatterslargescalecomparison,
      title={When Punctuation Matters: A Large-Scale Comparison of Prompt Robustness Methods for LLMs}, 
      author={Mikhail Seleznyov and Mikhail Chaichuk and Gleb Ershov and Alexander Panchenko and Elena Tutubalina and Oleg Somov},
      year={2025},
      eprint={2508.11383},
      archivePrefix={arXiv},
      primaryClass={cs.CL},
      url={https://arxiv.org/abs/2508.11383}, 
}
```

---
