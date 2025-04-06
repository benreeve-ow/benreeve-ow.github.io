---
layout: post
title: "Accounting for AI"
date: 2025-04-06
categories: [industry-developments]
author: Ben Reeve
---

![Accounting for AI](/assets/images/posts/839B9CFA-91C9-4F23-B499-35988CB0D385.png){: .align-center style="max-width: 100%;"}

# Accounting for AI

There's a thing that happens in the world of frontier AI models where companies announce how much it cost to train their latest model, and everyone gets excited about the falling costs of artificial intelligence. "Only $X million to train a state-of-the-art model!" the headlines proclaim, and people start updating their spreadsheets about AI democratization timelines. But these numbers have a certain "adjusted EBITDA" quality to them. They're not exactly... lies? But they're certainly selective presentations of cost structures that wouldn't pass muster in an SEC filing.[^1]

The latest example comes from DeepSeek AI, a Chinese AI company that recently released DeepSeek-V3. It's a mixture of experts (MoE) model with 671 billion total parameters but only 37 billion "active" parameters at any given time. Think of it as having 671 billion neurons but only letting 37 billion of them fire simultaneously - a kind of neural timeshare that keeps the compute requirements manageable. The model apparently performs impressively against competitors like Meta's Llama 405B while using far less computational resources.

What got everyone excited was DeepSeek's claim that training this model required only 2.6 million GPU hours, compared to Meta's 30.8 million GPU hours for Llama 3. This efficiency supposedly brought the training cost down to around $5.5 million. "AI is getting so cheap!" everyone exclaimed, and tech Twitter collectively swooned.

But wait. Let's read the footnotes.

DeepSeek acknowledges that this figure "includes only the official training of DeepSeek-V3, excluding the costs associated with prior research and ablation experiments on architectures, algorithms, or data." That's a bit like Apple saying the iPhone 16 only cost $10 million to manufacture, if you don't count the R&D, failed prototypes, or software development.

When you're building frontier AI models, the final training run is just the tip of the iceberg. Before that, you've likely spent vastly more compute on:

1. Thousands of small-scale experiments to test approaches (think 1B-7B parameter models)
2. Mid-sized validation runs to verify your approaches will scale
3. Related models that provide capabilities or data for your main model (DeepSeek used their R1 model for synthetic data)
4. Failed or abandoned approaches that didn't make it into the final model

Then there's the human cost. DeepSeek's paper lists 139 technical authors. Even with China's lower labor costs, that's a substantial payroll. Add in infrastructure costs like electricity (which can exceed $10 million annually for large GPU clusters), cooling, networking equipment, and the capital expenditure on the GPUs themselves, and the real cost starts looking very different.

A more realistic estimate might be $500 million to $1 billion annually for a company operating at DeepSeek's scale - not exactly the democratized AI future some were envisioning after seeing that $5.5 million figure.

## The Balance Sheet Matters

There's also an interesting accounting distinction here between capital expenditures and operating expenses. The $5.5 million figure describes the marginal cost of one training run using already-purchased hardware. But that's like saying it only costs $50 in petrol to drive a Ferrari from New York to Boston, ignoring the $300,000 you spent buying the car.

DeepSeek is reportedly using H800 GPUs, which are "nerfed" versions of Nvidia's H100s created specifically for the Chinese market to comply with U.S. export controls. These GPUs have some limitations on communication speeds between chips, but their raw computing power remains largely intact. Various estimates put DeepSeek's GPU inventory at somewhere between 20,000 and 50,000 A100 equivalents - a substantial asset that would cost billions to acquire at market rates.

## AI Economics and the Chip Geopolitics Premium

There's another subplot here about U.S.-China tech competition. DeepSeek's narrative of "look how much more we can do with less" makes strategic sense for a Chinese company operating under chip export controls. It's a flex aimed at both recruiting talent and demonstrating resilience against Western sanctions.

This is similar to how startups with tough unit economics emphasize their growth rate rather than their burn rate. "Don't look at our massive losses, look at our customer acquisition velocity!" When your access to computing resources is constrained by geopolitics, emphasizing efficiency becomes not just good engineering but good marketing.

The irony is that DeepSeek has likely spent more absolute dollars on this model than they're letting on, precisely because they have to work around chip export controls. The H800s they're using cost more on the secondary market, and the engineering effort required to optimize for their limitations adds another layer of expense.

## Open-Source or Open-Weights?

DeepSeek released their model under an open-weights license, meaning you can download and use the parameters, but you don't get the training code or data. That's like giving someone a compiled program without the source code - useful, but not exactly "open source" in the traditional sense.

This distinction matters for the cost narrative. If DeepSeek had released everything - training data, code, infrastructure optimizations - then others really could replicate their work for closer to that $5.5 million figure. But without those components, anyone wanting to build something similar would need to reinvent much of what DeepSeek built, pushing the real cost back toward the hundreds of millions.

There's a pattern in AI where companies release "open" models with just enough information to be useful but not enough to be truly replicable. It's a bit like investment banks releasing "research" that conveniently supports their trading positions - helpful but carefully curated.

## The Frontier AI Income Statement 

So what does the real income statement of a frontier AI lab look like? Something like this:

- **Revenue**: API calls, enterprise licenses, VC funding (treated as revenue for startups)
- **COGS**: GPU depreciation, electricity, cloud fees if applicable
- **R&D**: Engineering salaries, failed experiments, research computing
- **SG&A**: Executive salaries, offices, legal (especially important for AI safety compliance)
- **Adjusted EBITDA**: Whatever number makes the business look sustainable
- **Actual Net Income**: A number so negative it makes SoftBank investments look prudent

When DeepSeek or any other AI lab announces training costs, they're essentially reporting an adjusted non-GAAP metric that ignores most of these categories. It's the AI equivalent of "we lose money on each unit but make it up in volume."

The good news is that these costs really are falling over time. The learning efficiency of models continues to improve through innovations like DeepSeek's multi-head latent attention, multi-token prediction, and 8-bit native training. In a few years, frontier models might genuinely cost $5-10 million all-in to develop.

But for now, these headline numbers should be treated like crypto whitepaper projections - theoretically possible under ideal conditions that never seem to materialize in practice.

If someone tells you they built a frontier AI model for a few million dollars, ask them if that includes the cost of hiring 139 engineers. If not, you might be looking at AI's version of adjusted, non-GAAP, excluding-stock-based-compensation earnings.

[^1]: Though who knows, maybe they would. We live in a world where companies can go public with "community adjusted EBITDA" metrics that exclude most of their actual expenses. At least AI labs aren't publicly traded yet. 