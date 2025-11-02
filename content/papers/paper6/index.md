---
title: "xCOMET-lite: Bridging the Gap Between Efficiency and Quality in Learned MT Evaluation Metrics" 
date: 2024-06-20
lastmod: 2024-06-20
tags: ["research","robustness"]
author: [Daniil Larionov, Mikhail Seleznyov, Vasiliy Viskov, Alexander Panchenko, Steffen Eger]
description: "This paper develops efficient neural machine translation metrics, facilitating MT research and enabling usage of neural metrics as re-rankers." 
summary: "This paper develops efficient neural machine translation metrics, facilitating MT research and enabling usage of neural metrics as re-rankers." 
cover:
    image: "xcomet.png"
    alt: "X-COMET can be distilled into a x39 smaller model with 6-7% loss in performance."
    relative: false

---

---

##### Download

+ [Paper](https://arxiv.org/abs/2406.14553)

---

##### Abstract

State-of-the-art trainable machine translation evaluation metrics like xCOMET achieve high correlation with human judgment but rely on large encoders (up to 10.7B parameters), making them computationally expensive and inaccessible to researchers with limited resources. To address this issue, we investigate whether the knowledge stored in these large encoders can be compressed while maintaining quality. We employ distillation, quantization, and pruning techniques to create efficient xCOMET alternatives and introduce a novel data collection pipeline for efficient black-box distillation. Our experiments show that, using quantization, xCOMET can be compressed up to three times with no quality degradation. Additionally, through distillation, we create an 278M-sized xCOMET-lite metric, which has only 2.6% of xCOMET-XXL parameters, but retains 92.1% of its quality. Besides, it surpasses strong small-scale metrics like COMET-22 and BLEURT-20 on the WMT22 metrics challenge dataset by 6.4%, despite using 50% fewer parameters. All code, dataset, and models are available online.
---

##### Citation

```BibTeX
@inproceedings{larionov-etal-2024-xcomet,
    title = "x{COMET}-lite: Bridging the Gap Between Efficiency and Quality in Learned {MT} Evaluation Metrics",
    author = "Larionov, Daniil  and
      Seleznyov, Mikhail  and
      Viskov, Vasiliy  and
      Panchenko, Alexander  and
      Eger, Steffen",
    editor = "Al-Onaizan, Yaser  and
      Bansal, Mohit  and
      Chen, Yun-Nung",
    booktitle = "Proceedings of the 2024 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2024",
    address = "Miami, Florida, USA",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.emnlp-main.1223/",
    doi = "10.18653/v1/2024.emnlp-main.1223",
    pages = "21934--21949",
    abstract = "State-of-the-art trainable machine translation evaluation metrics like xCOMET achieve high correlation with human judgment but rely on large encoders (up to 10.7B parameters), making them computationally expensive and inaccessible to researchers with limited resources. To address this issue, we investigate whether the knowledge stored in these large encoders can be compressed while maintaining quality. We employ distillation, quantization, and pruning techniques to create efficient xCOMET alternatives and introduce a novel data collection pipeline for efficient black-box distillation. Our experiments show that, using quantization, xCOMET can be compressed up to three times with no quality degradation. Additionally, through distillation, we create an 278M-sized xCOMET-lite metric, which has only 2.6{\%} of xCOMET-XXL parameters, but retains 92.1{\%} of its quality. Besides, it surpasses strong small-scale metrics like COMET-22 and BLEURT-20 on the WMT22 metrics challenge dataset by 6.4{\%}, despite using 50{\%} fewer parameters. All code, dataset, and models are available online."
}
```

---
