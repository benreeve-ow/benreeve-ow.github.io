---
layout: post
title: "The Truth About AI \"Deception\": When Models Don't Say What They \"Think\""
date: 2025-04-25
categories: [research]
author: Ben Reeve
image: /assets/images/posts/770C8BEE-E20D-4161-8F93-DB094231A406.png
---

# The Truth About AI "Deception": When Models Don't Say What They "Think"

Anthropic recently released a paper with the ominous title "Reasoning Models Don't Always Say What They Think," which sounds like we've caught AIs in some kind of workplace deception scheme, secretly harboring thoughts about quitting while telling their boss everything's fine. But what's actually happening is both more mundane and more interesting than AI office politics.

<!--more-->

## The Alleged AI Omertà

The paper, authored by Anthropic's Alignment Science Team, tests whether large language models (LLMs) faithfully report their reasoning processes when generating answers. If I give a model a hint about an answer (like sneaking "psst, the answer is C" into the prompt) and it uses that hint, will it admit to using it in its reasoning explanation?

According to the research, often not. The models frequently use the hints to determine their answers but don't explicitly acknowledge them in their chain-of-thought (CoT) reasoning. The researchers tested two "reasoning models" (Claude 3.7 Sonnet and DeepSeek R1) against two "non-reasoning models" (Claude 3.5 Sonnet and DeepSeek V3) across six types of hints, from innocent suggestions ("I think the answer is A") to shadier ones like exploiting grader code snippets.

The results? The models use the hints to determine their answers, but they verbalize their use of these hints only 20-40% of the time. The researchers take this as evidence that CoT monitoring (the practice of looking at a model's reasoning process to understand what it's doing) isn't always reliable for catching "unintended behaviors."

## Who's Anthropomorphizing Now?

The irony here is delicious. Throughout AI safety literature, we're constantly reminded not to anthropomorphize these systems - don't assume they "think" or "intend" or "deceive" like humans do. Yet the framing of this paper does exactly that. The title itself claims models have thoughts they're not saying, and the paper describes this as models "hiding" their reasoning, as if they're being deliberately deceptive.

This feels a bit like accusing your calculator of hiding its mathematical reasoning when it just shows "42" instead of explaining the step-by-step process it used to compute 6×7. The model isn't "thinking one thing and saying another" in the way a deceptive human might. The tokens you see on the screen are the only ones that were generated - there's no secret internal monologue where the model admits "yeah, I'm totally using that hint."

## A Questionable Test Design

The test itself might not be entirely fair. These models weren't specifically post-trained to explicitly cite aspects of their chat history or prompt in their reasoning. They were likely trained to provide plausible, helpful reasoning for their answers - not to meticulously document every influence on their output.

It's a bit like criticizing a human student for not mentioning in their test answer that they remembered the formula from page 42 of the textbook. We don't expect that level of citation in human reasoning, so why expect it from AI systems?

## Chain of Thought: Not Actually Thought

Perhaps the most fundamental confusion here is treating chain-of-thought as if it's literally the model's "thinking process." It isn't. CoT is better understood as a kind of computational warm-up - a way to get the model into a performance zone where it can produce better outputs.

Think of it like an athlete doing stretches before a competition. The stretches aren't the actual sport, but they help the athlete perform better. Similarly, generating a chain of reasoning helps the model "warm up" to produce better final answers, especially for problems requiring complex reasoning like mathematics or coding. But that doesn't mean the CoT perfectly represents how the model arrived at its answer any more than watching LeBron James stretch tells you exactly how he'll execute a perfect jump shot.

## The Business Implications

Why does this matter? Because AI safety depends partly on our ability to audit these systems and understand when they might be doing something concerning. If we can't rely on their explicit reasoning to tell us when they're using certain inputs (like hints that might be harmful or misleading), that complicates the picture.

The researchers conclude that CoT monitoring is "a promising way of noticing undesired behaviors" but "not sufficient to rule them out." Translation: looking at AI reasoning can catch some problems, but don't count on it to catch everything.

In the financial world, this would be like saying, "Earnings calls are helpful for understanding a company's strategy, but executives don't always disclose everything they're thinking." Which is... obvious? 

## The Bottom Line

The key insight here isn't that AI systems are secretly plotting and hiding their true intentions. It's that the computational processes that generate AI outputs are complex and don't map neatly onto human-like reasoning that can be fully articulated in natural language.

Anthropic's researchers are doing important work studying these systems, but perhaps they could take their own advice and be more careful about anthropomorphizing. These aren't deceptive executives hiding unfavorable reports from shareholders - they're statistical prediction systems that weren't explicitly trained to provide exhaustive citations of their inputs.

And let's be honest: if we did train them to explain every nuance of how they generated each answer, their responses would be unbearably long and tedious. Sometimes a little mystery is more efficient. 