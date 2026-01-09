---
title: "Critique of machine unlearning"
date: 2026-01-09
draft: false
description: ""
summary: ""
tags: ["research"]
---


# Machine Unlearning

[Wikipedia](https://en.wikipedia.org/wiki/Machine_unlearning) (as of January 2026): 
> Machine unlearning is a branch of machine learning focused on removing specific undesired element, such as private data, wrong or manipulated training data, outdated information, copyrighted material, harmful content, **dangerous abilities**, or misinformation, without needing to rebuild models from the ground up.

[A blog post](https://ai.stanford.edu/~kzliu/blog/unlearning) from Stanford:
> As our ML models today become larger and their (pre-)training sets grow to inscrutable sizes, people are increasingly interested in the concept of machine unlearning to edit away undesired things like private data, stale knowledge, copyrighted materials, toxic/unsafe content, **dangerous capabilities**, and misinformation, without retraining models from scratch.

I want to make two claims:
1) Unlearning cannot be used to remove dangerous capabilities while keeping benign capabilities, because capabilites are almost always dual-use.
2) Strong compositional generalization constrains what is achievable with unlearning.

Meanwhile, I do think unlearning might be a reasonable solution for removing private data / not-so-popular copyrighted materials. Or, more generally, for dealing with rare facts / entities and tails of the distribution.

## Dual-use capabilities

I will just list several examples here to illustrate my point.

1) Cyberattacks and cyberdefense. Ability to write secure code most likely requires deep understanding of different kinds of vulnerabilities, and this understanding can be re-used for attacks.
2) Medicine. Being able to accurately diagnose the patient and assign appropriate treatment most likely requires deep knowledge of human biology, which is turn can be re-purposed for harm (e.g. via wrong medications).
3) Chemistry/Synthesis. Understanding organic chemistry enables developing new pharmaceuticals and industrial processes, but the same knowledge underlies synthesis of toxic compounds, explosives, or controlled substances.
4) Psychology/Emotional support. Genuinely helping someone through a crisis requires understanding human emotions, vulnerabilities, and what makes people feel heard. But the same capabilities enable manipulation, exploitation, or radicalization.

On a higher level, the basic capability of *following instructions* accurately is dual-use. A model that reliably does what users ask is both maximally helpful and maximally exploitable.

These points are pretty basic, and I don't want to claim nobody knows that -- but I suspect people do not keep it constantly in the back of their heads, and don't cross-check with this often. So my call to action is: ask yourself -- what *concretely* am I trying to achieve with this research? What is the best case scenario?

You might answer "I'm aiming to defend user's private data by unlearning sporadic facts which were not filtered out of the pretraining corpus". This is a decent answer, since you don't try to address some abstract "harmful capability" -- you try to erase concrete facts. The same goes for patching some concrete outdated facts.

However, **if your theory of impact is "removing harmful capabilities", I urge you to think deeply how this interacts with the concept of dual-use capabilities**.

## Interconnectedness of knowledge

I do believe more in unlearning of concrete facts than capabilities. Still, there is one more nuance.

For the sake of the argument, let's define fact as an subject-relation-object triple, like "Zebra, is-a, mammal" or "Mammals, are, animals".

Suppose we have facts A, B and C, and A & B implies C. 
If model knows A, B, and has ability for logical inference, then it can trivially rederive C during e.g. CoT reasoning.
And we know models can do such inferences: [Out-of-Context Reasoning](https://arxiv.org/abs/2309.00667), [Connecting the dots](https://arxiv.org/abs/2406.14546). (To be fair, it is far from perfect, and often fails when you do need it.)

Now, how to unlearn C?
To ensure that model does not output C, we have to
1) unlearn A or B, 
2) or to turn off it's logical inference ability entirely
3) modify it's logical inference ability so it does not work concretely for A and B, but works for all other cases.

Let's analyze the options.
1) First requires to unlearn more than we initially wanted. This is problematic, since we could want to preserve both A and B in the model for other cases. 
2) Second is practically useless, it would produce a crippled model. 
3) Critique of third option is subtler. I believe *it is hard to learn* such patched abilities, since it has been shown multiple times that neural networks tend to learn simple functions (e.g. [link](https://arxiv.org/abs/1805.08522), [link](https://openreview.net/forum?id=QC10RmRbZy9)). And in practice it means it will be hard to reliably learn such "patched" abilites -- either unlearning will be shallow (=easy to bypass via prompt optimization or a touch of finetuning), or the model will be pretty crippled again, closer to option 2.

Thus, when we encounter interconnected facts, it might be hard to unlearn only some of them. Or, to put differently: **strong compositional generalization / out-of-context learning is incompatible with unlearning of arbitrary subsets of facts**. It's still possible to unlearn clusters of facts, which are not well-connected with other knowledge. But still, it's an important theoretical consideration, especially given that compositional generalization abilities seem to go up from year to year (math benchmarks, ARC-AGI, etc).

Opinion: I believe that a lot of data in our world is similarly interconnected, which limits what pieces of knowledge could be unlearned.

## Negative vs positive learning

I'm less sure about the final point, since I might be misinterpreting what SOTA unlearning algorithms do, but this should be relevant for all methods relying on gradient ascend.

What it means to learn to answer A in response to query Q is pretty clear. What does it mean to unlearn answer A? What the model is _expected to output in response to Q_ after unlearning?

In this light, supervised learning is much better defined -- we force the model to output very conrete responses for a set of quieries from finetuning set.

I think, this is why approaches like refusal training and safe completions are widely used for frontier LLM labs -- they use positive framing, which is simpler to learn.

## References

Here are some papers I found when preparing this post, along with excerpts from their abstracts.

### On filtering training data
[Deep Ignorance: Filtering Pretraining Data Builds Tamper-Resistant Safeguards into Open-Weight LLMs](https://arxiv.org/abs/2508.06601)

[Learning and Forgetting Unsafe Examples in Large Language Models](https://arxiv.org/abs/2312.12736)
> ...Overall, our results suggest the safety finetuning session cannot completely eliminate malicious knowledge from the model and enable it to behave as if it has never seen unsafe training data, which is the ideal goal of machine unlearning.

### Others
[Machine Unlearning Doesn't Do What You Think: Lessons for Generative AI Policy and Research](https://arxiv.org/abs/2412.06966)
> Both of these goals--the targeted removal of information from a model and the targeted suppression of information from a model's outputs--present **various technical and substantive challenges**. We provide a framework for ML researchers and policymakers to think rigorously about these challenges, identifying several mismatches between the goals of unlearning and feasible implementations. These mismatches explain why unlearning is not a general-purpose solution for circumscribing generative-AI model behavior in service of broader positive impact.

[On Evaluating the Durability of Safeguards for Open-Weight LLMs](https://arxiv.org/abs/2412.07097)
> ...several recent studies have proposed methods to produce durable LLM safeguards for open-weight LLMs that can withstand adversarial modifications of the model's weights via fine-tuning... However, in this paper, we urge for more careful characterization of the limits of these approaches. Through several case studies, we demonstrate that **even evaluating these defenses is exceedingly difficult and can easily mislead audiences into thinking that safeguards are more durable than they really are**. We draw lessons from the evaluation pitfalls that we identify and suggest future research carefully cabin claims to more constrained, well-defined, and rigorously examined threat models, which can provide more useful and candid assessments to stakeholders.

[Existing Large Language Model Unlearning Evaluations Are Inconclusive](https://arxiv.org/abs/2506.00688)
> ...recent studies suggest that unlearning is often shallow, claiming that removed knowledge can easily be recovered. In this work, we critically examine standard unlearning evaluation practices and uncover key limitations that shake our trust in those findings. **First**, we show that some evaluations introduce substantial new information into the model, potentially masking true unlearning performance by re-teaching the model during testing. **Second**, we demonstrate that evaluation outcomes vary significantly across tasks, undermining the generalizability of current evaluation routines. **Finally**, we find that many evaluations rely on spurious correlations, making their results difficult to trust and interpret.

[Model Tampering Attacks Enable More Rigorous Evaluations of LLM Capabilities](https://arxiv.org/abs/2502.05209)
> ...state-of-the-art unlearning methods can easily be undone within 16 steps of fine-tuning. 