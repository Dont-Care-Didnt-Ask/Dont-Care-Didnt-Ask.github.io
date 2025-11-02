---
title: "Obfuscated Activations Bypass LLM Latent-Space Defenses" 
date: 2021-04-06
lastmod: 2024-10-18
tags: ["research","robustness","adversarial"]
author: ["Luke Bailey", "Alex Serrano", "Abhay Sheshadri", "Mikhail Seleznyov", "Jordan Taylor", "Erik Jenner", "Jacob Hilton", "Stephen Casper", "Carlos Guestrin", "Scott Emmons"]
description: "This paper introduces obfucated activations phenomenon, which poses a significant challenge for monitors/detectors relying on LLMs latent space." 
summary: "This paper introduces obfucated activations phenomenon, which poses a significant challenge for monitors/detectors relying on LLMs latent space." 
cover:
    image: "obfact.png"
    alt: "Obfuscation attacks achieve a high degree of control over how a harmfulness monitor classifies activations while also controlling model outputs."
    relative: false
# editPost:
#     URL: "https://github.com/pmichaillat/hugo-website"
#     Text: "Journal of Socio-Experimental Psychology"

---

---

##### Download

+ [Paper](https://arxiv.org/abs/2412.09565)
<!-- + [Raw data](https://github.com/pmichaillat/recession-indicator) -->

---

##### Abstract

Recent latent-space monitoring techniques have shown promise as defenses against LLM attacks. These defenses act as scanners that seek to detect harmful activations before they lead to undesirable actions. This prompts the question: Can models execute harmful behavior via inconspicuous latent states? Here, we study such obfuscated activations. We show that state-of-the-art latent-space defenses -- including sparse autoencoders, representation probing, and latent OOD detection -- are all vulnerable to obfuscated activations. For example, against probes trained to classify harmfulness, our attacks can often reduce recall from 100% to 0% while retaining a 90% jailbreaking rate. However, obfuscation has limits: we find that on a complex task (writing SQL code), obfuscation reduces model performance. Together, our results demonstrate that neural activations are highly malleable: we can reshape activation patterns in a variety of ways, often while preserving a network's behavior. This poses a fundamental challenge to latent-space defenses.
---

##### Citation

```BibTeX
@misc{bailey2025obfuscatedactivationsbypassllm,
      title={Obfuscated Activations Bypass LLM Latent-Space Defenses}, 
      author={Luke Bailey and Alex Serrano and Abhay Sheshadri and Mikhail Seleznyov and Jordan Taylor and Erik Jenner and Jacob Hilton and Stephen Casper and Carlos Guestrin and Scott Emmons},
      year={2025},
      eprint={2412.09565},
      archivePrefix={arXiv},
      primaryClass={cs.LG},
      url={https://arxiv.org/abs/2412.09565}, 
}
```

---
