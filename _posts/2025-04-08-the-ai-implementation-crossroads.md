---
layout: post
title: "LLMs: To Fine-Tune or Not to Fine-Tune, That Is the Expensive Question"
date: 2025-04-08
categories: [tutorials]
author: Ben Reeve
image: /assets/images/posts/DE154635-2B08-40CE-A990-1C5111751EEB.png
---

Something that happens in corporate life is that your company buys some technology, and then someone from IT starts evangelizing about how it could transform your business. Later, someone else shows up to tell you why the first approach will never work and you need to spend more money on a different approach. Then meetings happen, consultants are hired, and PowerPoints multiply like rabbits. Nowhere is this more true than with large language models.

Let's talk about LLMs and the eternal question: "Should we just use ChatGPT, or should we spend a fortune building our own custom model?"

## What's an LLM and why are there different flavors?

A large language model, or LLM, is essentially a very sophisticated pattern-matching machine that has ingested vast amounts of text data. After enough training, it can predict what words should come next given a certain input, with sometimes uncanny results. It's like if you took the world's best crossword puzzle solver and fed them every book, article, and Reddit thread ever written, then asked them to complete your sentences.

There are two main varieties of these models that you'll encounter in the wild:

1. **Base LLMs**: These are the raw, untamed beasts fresh off their initial training. They've learned language patterns but haven't been specifically taught to be helpful, honest, or harmless. Think of them as brilliant but somewhat feral Ph.D. candidates who never learned social skills.

2. **Post-trained "assistant" models**: These are base LLMs that have gone through finishing school. They've received additional training (often called "instruction tuning" or "RLHF") to follow directions, provide helpful answers, and avoid going off the rails. This is your ChatGPT, Claude, or other consumer-facing AI assistants.

The difference matters because you'll inevitably face a choice: use an existing assistant model off-the-shelf with careful prompting, or take a base model and fine-tune it specifically for your use case.

## "But we're special!" (The siren call of custom fine-tuning)

Every company believes their problems are unique. "Sure, ChatGPT works for regular people," your colleagues will say, "but our credit ratings/legal contracts/medical diagnoses/artisanal cheese descriptions are special and require deep domain expertise."

They're not entirely wrong. Take credit ratings, for example. Moody's doesn't just slap an "A+" on a company because they like the CEO's LinkedIn profile. There are methodologies, ratios, industry comparisons, and regulatory requirements. Using a general-purpose assistant to generate credit ratings by just showing it a few examples ("few-shot prompting") might work surprisingly well, but it won't necessarily apply your proprietary methodology consistently.

This is where fine-tuning a base model on your specific data comes in. You take a raw LLM and teach it all about your credit rating approach by training it on thousands of your past reports and methodologies. In theory, the model internalizes your special sauce.

It's a bit like the difference between hiring a brilliant generalist consultant and giving them your manual, versus hiring someone who's worked in your industry for 20 years. The generalist might get it right with good direction, but the specialist has the patterns baked into their brain.

## The costs of being special (fine-tuning isn't cheap)

Here's where the corporate fantasy of a perfect AI assistant collides with budget reality. Fine-tuning a model has costs that go far beyond the GPU time:

1. **Data collection and preparation**: You need thousands of high-quality examples. Someone has to collect, clean, and label all that data. That "someone" is usually a team of very expensive people.

2. **Technical expertise**: Fine-tuning requires machine learning engineers who understand the nuances of model training, hyperparameters, and evaluation metrics. These people don't work for exposure on your company LinkedIn page.

3. **Maintenance**: Markets change. Regulations update. Your model becomes gradually more outdated with each passing day. Unlike a post-trained assistant that gets regular updates from its provider, your fine-tuned model will need ongoing maintenance.

Meanwhile, using an existing assistant model means you can get started today. Your costs scale with usage rather than requiring a massive upfront investment. You don't need a team of ML PhDs, just some clever people who know how to write effective prompts.

The perfect corporate PowerPoint will always show the fine-tuned model outperforming the off-the-shelf solution. What it won't show is the three failed fine-tuning attempts, the data quality issues, and the six-month timeline slippage.

## Sometimes the special snowflake approach actually makes sense

Despite my skepticism, there are legitimate reasons to consider fine-tuning:

1. **Consistency at scale**: If you're generating thousands of credit reports daily, the consistency of a specialized model might be worth the investment.

2. **Regulatory requirements**: Some industries have strict requirements about how decisions are made and explained. A fine-tuned model might better incorporate these requirements into its very fabric.

3. **Proprietary edge**: If your credit rating methodology truly is superior to everyone else's (sure, why not), embedding it directly into a model could maintain that edge better than prompt-based guidance.

4. **Token efficiency**: Every word in your prompt costs money with commercial APIs. A fine-tuned model doesn't need to be reminded of your methodology every single time.

5. **Control**: With your own model, you're not subject to the whims of OpenAI's content policies or pricing changes.

The truly pragmatic approach would be to start with few-shot prompting, prove the concept works, and only then consider whether the additional investment in fine-tuning is justified. But that rarely happens because it's not as exciting as announcing your company's new "proprietary AI system."

## How to decide without losing your mind (or your budget)

Here's a practical framework that won't make it into the PowerPoint because it's too honest:

1. **How special are you, really?** Be brutally honest. Is your use case genuinely unique, or are you just a unique implementation of a common pattern? Most "special" use cases are actually standard use cases with organization-specific terminology.

2. **What's your volume?** If you're generating 10 reports a month, fine-tuning is probably overkill. If it's 10,000, the efficiency gains might justify the investment.

3. **Do you have the data?** Not just some data, but thousands of consistent, high-quality examples. If not, your fine-tuned model will just learn to replicate your inconsistencies.

4. **What's your tolerance for imperfection?** Fine-tuned models aren't magic. They'll still make mistakes. If your use case requires 100% accuracy, you need humans in the loop regardless of your approach.

5. **How much change do you anticipate?** If your methodology or data changes frequently, maintaining a fine-tuned model becomes increasingly complex.

In the credit rating example, few-shot prompting might get you 80% of the way there with 20% of the effort. Fine-tuning might get you to 95%, but that last 15% comes at 5x the cost and complexity.

## The obligatory "why not both?" conclusion

Like all good consulting advice, I'll end by suggesting you might need both approaches. Start with few-shot prompting to prove the concept and understand the limitations. Identify specific areas where consistency or specialization is lacking. Only then consider targeted fine-tuning to address those gaps.

The truly wise approach is to recognize that LLMs, whether base or post-trained, are tools rather than solutions. The solution emerges from how you integrate them into your processes, the guardrails you put around them, and how you leverage their capabilities while mitigating their weaknesses.

But that kind of nuanced approach doesn't fit neatly into the "build vs. buy" dichotomy that corporate decision-making loves. It's much easier to either embrace the technology as a magical solution or dismiss it as fundamentally flawed.

In the meantime, your competitors are probably experimenting with both approaches while your committee schedules its fourth meeting to discuss whether to create a working group to evaluate potential AI strategies.

Maybe the real fine-tuning was the PowerPoints we made along the way. 