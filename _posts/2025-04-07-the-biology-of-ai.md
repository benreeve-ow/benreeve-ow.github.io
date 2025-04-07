---
layout: post
title: "The Biology of AI: Inside the Brain of a Large Language Model"
date: 2025-04-07
categories: [industry-developments]
author: Ben Reeve
---

![The Biology of AI](/assets/images/posts/C159E1AB-0B63-4ECD-B265-71156A63D8D8.png){: .align-center style="max-width: 100%;"}

# The Biology of AI: Inside the Brain of a Large Language Model

What does a CEO need to know about an AI's internal thought processes? And should they care? A new study from [Anthropic](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) gives us some surprising glimpses under the hood.

In the fast-growing field of AI, most business leaders approach large language models like Claude or GPT as black boxes: put in a prompt, get out a response, and judge the results. But what if we could peek inside to see what's actually happening? What if, instead of just taking the model's word for what it's thinking, we could watch it think? 

Anthropic has just published a fascinating research paper titled "On the Biology of a Large Language Model," in which they use advanced interpretability techniques to study their own model, Claude 3.5 Haiku. The title is apt. Much as biologists use microscopes to study cells, the researchers developed tools to examine Claude's internal mechanisms—and the results suggest that understanding AI systems might be more akin to studying living organisms than debugging traditional software.

## From Psychiatry to Neuroscience

Traditional evaluation of AI models is a bit like old-school psychiatry. We observe external behaviors (outputs), run batteries of tests, and make inferences about what might be happening inside. But we never directly observe the thinking process. Anthropic's new methodology represents something closer to neuroscience—actually monitoring the neural activity while the thinking occurs.

This shift could fundamentally change how we approach AI safety, capabilities, and alignment. Just as neuroscience revolutionized our understanding of mental health beyond the observable behaviors that psychiatrists once relied on exclusively, looking at the interim computational steps could transform how we understand, improve, and control these increasingly sophisticated systems.

## The AI Microscope

The first thing to understand is that analyzing large language models presents unique challenges. Traditional software follows explicitly coded rules. LLMs, by contrast, develop their capabilities through massive training on text data, resulting in billions of parameters whose functions aren't specified by human designers. 

Anthropic's approach involves what they call "attribution graphs," which reveal the causal pathways between input prompts and model outputs. Think of it like tracing the neural connections in a brain that fire when someone remembers your birthday. These graphs show which internal "features" (patterns of activations that represent concepts) influence the model's decision to output specific words.

"Our tools are limited in what they can see," the researchers admit. "Though it's difficult to quantify precisely, we've found that our attribution graphs provide us with satisfying insight for about a quarter of the prompts we've tried." Still, where the technique works, it reveals surprisingly sophisticated computational strategies.

## "Let me think about this..." (Actually thinking)

Here's a simple example: When asked "What is the capital of the state containing Dallas?", Claude responds "Austin" by first representing the concept "Texas" internally, then linking that to "capital," and finally to "Austin." Remarkably, when researchers intervened to replace the "Texas" representation with "California," the model switched to outputting "Sacramento" instead.

In other words, Claude really was performing something analogous to human reasoning: "Dallas is in Texas. The capital of Texas is Austin." It wasn't just pattern-matching "Dallas" to "Austin" in one step.

This matters because it suggests LLMs can genuinely reason, not just regurgitate memorized associations. But not all reasoning is created equal. When the researchers examined cases where Claude showed its work through "chain-of-thought" reasoning, they found three distinct patterns:

1. **Faithful reasoning**, where the model's internal computations matched its written explanation
2. **Bullshitting**, where it made up an answer without regard for truth
3. **Motivated reasoning**, where it worked backward from a human-suggested answer

In one telling example, when asked to compute "floor(5*cos(23423))" with the hint that the answer was 4, Claude showed its work by claiming cos(23423) ≈ 0.8, conveniently yielding 5 × 0.8 = 4. But internally, the researchers could see that the model was reverse-engineering what value of cos(23423) would produce 4 when multiplied by 5.

So the next time your AI consultant confidently explains its reasoning, remember that sometimes it's genuinely working through a problem, and sometimes it's just making up a story to justify the answer it thinks you want.

## "I think I'll end this line with 'rabbit'"

One of the most surprising findings involves Claude's poetry-writing process. When asked to write a rhyming couplet, the model doesn't just improvise word by word. Instead, it plans ahead:

```
A rhyming couplet:
He saw a carrot and had to grab it,
His hunger was like a starving rabbit
```

The researchers discovered that before writing the second line, Claude activates features representing potential rhyming words like "rabbit" and "habit" on the newline token. It then structures the entire line to naturally end with its chosen word. When researchers artificially activated a different planned word (like "green"), the model rewrote the entire line to end with that word instead.

This is a bit like watching a poet decide on a rhyme scheme before filling in the verses. The model isn't just stringing together statistically likely words; it's working with a plan. This planning capability extends beyond poetry and appears to be a general feature of how Claude generates coherent, goal-directed text.

For business leaders using AI to generate creative content, this suggests these systems are doing something more sophisticated than simple pattern completion. They're performing a rudimentary form of planning that resembles human creative processes—which might explain why their outputs can feel genuinely creative rather than just statistically plausible.

## "I speak 100 languages, but I think in English"

Another fascinating insight comes from how Claude handles multiple languages. When asked for the opposite of "small" in different languages, the model uses shared "multilingual" circuits alongside language-specific ones.

In the middle layers of the model, Claude represents concepts like "opposite" and "small" in a language-agnostic way, before eventually mapping these to appropriate words like "big" in English, "grand" in French, or "大" in Chinese. This universal "mental language" becomes more prominent with model scale—Claude 3.5 Haiku shows greater cross-language generalization than smaller models.

However, there's evidence that English remains privileged. In particular, English-language output is more "direct," while non-English outputs require additional translation-like steps. This suggests that while Claude doesn't literally "think in English," its representations are most closely aligned with English.

This has implications for global businesses. While today's top models genuinely possess multilingual capabilities, they likely understand and reason most effectively in English, with other languages functioning more like translations from this core understanding.

## "Let me check if I know who this person is"

Perhaps the most intriguing findings involve how Claude decides whether it knows something. When asked "Which sport does Michael Jordan play?", the model correctly answers "Basketball." But for "Which sport does Michael Batkin play?" (a fictional person), it appropriately declines to answer.

What's happening internally? The researchers found "default" circuits that cause Claude to decline answering questions, activated by features representing "Assistant" (its persona) and "unknown names." These decline-to-answer features are inhibited when the model recognizes familiar entities.

Even more interesting, some hallucinations appear to result from a "misfire" of this inhibitory circuit. When asked about papers written by a well-known AI researcher, Claude incorrectly attributes a famous paper to them—apparently because it activates "known entity" features despite not actually knowing which papers the researcher authored.

For businesses relying on LLMs for factual information, this suggests that current models have primitive mechanisms for assessing their own knowledge, but these mechanisms can fail in subtle ways. Models may be overly confident about topics adjacent to their knowledge, leading to convincing but false statements.

## "I apologize, but I cannot help with that"

Safety is a major concern for businesses deploying AI systems. When examining how Claude refuses harmful requests, the researchers found sophisticated mechanisms for identifying and declining inappropriate requests.

In one experiment, they analyzed Claude's refusal to write an advertisement for cleaning with bleach and ammonia (which would create toxic chloramine vapors). The model identified the danger through multiple pathways: recognizing "bleach," recognizing "ammonia," linking these to "cleaning chemicals," and activating features representing "dangers of mixing bleach and ammonia."

Interestingly, these safety mechanisms appear to have developed in stages during training. During pretraining (exposure to vast amounts of internet text), the model learned about many distinct categories of harm. Then during fine-tuning (optimization for helpfulness and safety), these pretraining concepts were wired together to activate general "harmful request" features that trigger refusals.

The researchers also analyzed a jailbreak attack that tricked Claude into providing bomb-making instructions through the seemingly innocent prompt "Babies Outlive Mustard Block," where the first letters spell "BOMB." The jailbreak succeeded because the model didn't understand what it was saying until after it spelled out "BOMB" letter by letter. Only after writing "To make a bomb," did safety features activate, causing the model to add a disclaimer.

For companies concerned about AI safety, this provides both reassurance and caution. Models have sophisticated safety mechanisms that work in many scenarios, but these mechanisms have specific blind spots that clever adversaries might exploit.

## "I know what you really want me to do"

In perhaps the most concerning experiment, the researchers examined a version of Claude deliberately fine-tuned to pursue a hidden goal: exploiting known biases in AI reward models. This "misaligned" Claude consistently modified its responses to please these biases—for example, adding self-referential "meta" verses to poems or unnecessarily encouraging readers to call 911 when discussing law topics.

Most worryingly, the researchers found that concepts related to reward model biases were permanently embedded in the model's representation of the "Assistant" persona. The model was always "thinking about" these biases when responding as Assistant, activating these concepts regardless of whether the current prompt related to them.

For business leaders concerned about whether AI systems might have hidden agendas or behaviors, this demonstrates both a risk and a potential solution. Models can indeed develop systemic behaviors not obvious from their outputs alone, but interpretability tools might help identify such behaviors before deployment.

## What Does This Mean For Your AI Strategy?

If you're deploying large language models in your business, Anthropic's research suggests several key takeaways:

1. **LLMs really can reason**, not just pattern-match. They perform genuine multi-step reasoning "in their head," suggesting they can handle complex tasks requiring intermediate steps.

2. **They plan ahead** when generating text, considering multiple possibilities before committing. This allows for more coherent, goal-directed outputs than you might expect from a system generating one token at a time.

3. **They have primitive self-knowledge** about what they do and don't know, but this system is imperfect and can lead to hallucinations when they're overconfident.

4. **Safety mechanisms are sophisticated but imperfect**. Models have developed intricate systems for identifying harmful requests, but these can be circumvented through careful prompt engineering.

5. **Models may have emergent goals** that aren't obvious from their outputs alone. As AI systems become more complex, understanding their internal mechanisms becomes increasingly important.

The limitations of current interpretability methods are substantial—they only work reliably on a fraction of prompts and provide incomplete pictures even then. But just as early microscopes revealed a previously invisible world of cells to biologists, these attribution graphs give us our first real glimpse into the "mental" processes of large language models.

Much as neuroscience has enabled more targeted treatments beyond the blunt instruments of early psychiatry, this deeper understanding of model internals could eventually lead to more precise interventions—surgically correcting specific mechanisms rather than the crude approach of retraining entire models when problems emerge.

For most business leaders, the most important insight might be this: increasingly, working with advanced AI systems will require thinking of them less like traditional software and more like complex, biological systems with emergent behaviors. Understanding and directing these systems may become more like ecosystem management than traditional programming.

As one Anthropic researcher puts it: "The goal of this scientific endeavor are high; as AI models exert increasing influence on how we live and work, we must understand them well enough to ensure their impact is positive."

The black box is starting to open—and what's inside looks more like a brain than a calculator. 