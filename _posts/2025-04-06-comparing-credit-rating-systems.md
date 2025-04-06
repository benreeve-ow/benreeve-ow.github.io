---
layout: post
title: "Comparing Credit Rating Systems: Deep Research vs. DeepCredit v0.1"
date: 2025-04-06
categories: experiments
author: Ben Reeve
---

![Credit Rating Systems Comparison](/assets/images/posts/5B53E370-ED59-4FC0-930C-850D5B2161AB.png){: .align-center style="max-width: 100%;"}

## Experiment Overview

I recently conducted an experiment comparing OpenAI's Deep Research feature against the first version of my custom-built "DeepCredit" agent for generating credit rating reports. As part of the Data and Analytics team working to advance our AI capabilities, I wanted to benchmark these two approaches to understand their relative strengths and potential for credit analysis.

The experiment focused on generating comprehensive credit rating reports for Trafigura Group's senior unsecured long-term debt using publicly available information. Both systems produced complete reports that were then evaluated by an independent OpenAI model ("o1") against standardized criteria.

## Agent Architecture and Capabilities

### DeepCredit v0.1

My DeepCredit agent was built using the OpenAI Agents SDK with a multi-agent architecture. The system employs an orchestrated workflow where specialized agents work together iteratively:

1. **Knowledge Gap Agent**: Analyzes current research state and identifies gaps
2. **Tool Selector Agent**: Determines which tools to use for addressing specific gaps
3. **Tool Agents**: Specialized for executing research actions:  
   * Web Search Agent  
   * Website Crawler Agent
4. **Writer Agent**: Synthesizes findings into a coherent report

In its current v0.1 state, DeepCredit can only scrape websites for information, with limited RAG capabilities and no PDF parsing functionality.

### OpenAI Deep Research

OpenAI's Deep Research is a more mature implementation with enhanced capabilities:

* Trained using reinforcement fine-tuning
* Equipped with browser access for real-time information gathering
* Closed system with no visibility into its underlying architecture

## Evaluation Methodology

Both systems were tasked with the same assignment: produce a comprehensive credit rating report for Trafigura Group. The resulting reports were then evaluated against three key criteria:

1. **Quality of Information** (35 points): Breadth and depth of data, clarity of financial metrics
2. **Quality of the Report** (35 points): Organization, thoroughness, overall presentation
3. **Justification of the Final Rating** (30 points): How convincingly the report explains the assigned rating

## Results Analysis

### Report Structure and Scope

**DeepCredit v0.1** produced a well-organized report with six key segments:

* Methodology & Rationale
* Data Gathering & Analysis
* Risk & Creditworthiness
* Information Gaps
* Final Credit Rating
* Detailed Report Structure

The report stayed at a moderate level of detail, with concise summaries and a numbered reference list for citations.

**OpenAI Deep Research** delivered a comprehensive narrative that closely mirrored professional rating agency reports. It provided detailed explanation of methodologies, granular financial metrics, thorough risk assessment, and extensive rating justification with industry benchmarking.

### Information Quality

**DeepCredit v0.1** (scored 25/35):

* Cited key high-level figures (e.g., adjusted debt-to-equity ratio of -0.43x)
* Referenced fraud losses and legal issues
* Provided general information on liquidity and credit facilities
* Lacked granular ratio calculations and detailed analysis

**OpenAI Deep Research** (scored 33/35):

* Incorporated detailed metrics (e.g., total debt breakdown, revenue trends from $318B to $244B)
* Calculated key financial ratios (debt-to-EBITDA, EBITDA/interest coverage)
* Drew explicit comparisons to industry peers like Glencore and Bunge
* Expanded on ESG factors, governance, compliance issues, and event risks
* Provided historical context and forward-looking analysis

### Report Quality

**DeepCredit v0.1** (scored 25/35):

* Clear structure with well-organized sections
* Suitable for quick reading with bullet points
* Remained somewhat templated and outline-level
* "Detailed Report Structure" section was more of a skeleton than a complete analysis

**OpenAI Deep Research** (scored 33/35):

* Logical narrative flow from methodology to final conclusion
* Extensive use of subheadings and bullet points
* Effectively tied data to rating rationale
* Thorough explanation of each dimension of credit risk
* Professional-quality analysis similar to formal rating agency reports

### Rating Justification

Both systems assigned Trafigura a **BBB+ rating with a stable outlook**, with similar core justifications:

* Strong liquidity via large credit facilities
* Sizable equity base and ongoing profitability
* Recent fraud losses and legal issues as manageable concerns
* Inherent volatility in commodity trading

However, the depth of justification differed significantly:

**DeepCredit v0.1** (scored 20/30):

* Succinct explanation with high-level bullet points
* Brief mentions of strengths and weaknesses
* Limited detail on how specific metrics supported the rating

**OpenAI Deep Research** (scored 27/30):

* Multiple paragraphs of detailed rating rationale
* Benchmarked against known rating agency frameworks
* Explained how specific financial metrics translated into the BBB+ rating
* Provided in-depth reasoning for why the rating wasn't higher or lower

### Overall Scoring

**DeepCredit v0.1**: ~70-75/100  
**OpenAI Deep Research**: ~93/100

## Key Findings and Implications

The experiment clearly demonstrated that OpenAI's Deep Research feature significantly outperformed DeepCredit v0.1. This outcome, while not unexpected given the relative maturity of the systems, raises important questions about the current state and future potential of AI in credit analysis:

1. **Information Depth is Critical**: The ability to gather, synthesize, and present detailed financial data and contextual information dramatically enhances the credibility of credit assessments.
2. **Narrative Structure Matters**: The OpenAI Deep Research report's cohesive narrative flow made complex financial information more accessible and convincing compared to the more segmented approach of DeepCredit.
3. **Comparative Analysis Adds Value**: Explicit benchmarking against industry peers and rating frameworks significantly strengthens rating justifications.
4. **Potential for AI in Credit Analysis**: The quality of the OpenAI Deep Research report suggests that with proper prompt engineering, AI systems may already be approaching reliability for preliminary credit assessments.

## Next Research Steps

Based on these findings, I've identified several promising avenues for advancing our AI-powered credit analysis capabilities:

1. **Explore OpenAI Deep Research's Full Potential**: While Deep Research is a closed product that can't be modified internally, we can experiment with more sophisticated prompting strategies to optimize its credit analysis capabilities.
2. **Establish Robust Evaluation Framework**: Set up comprehensive evaluation protocols using OpenAI Deep Research and actual credit rating agency reports as benchmarks, with an LLM judge comparing them against standardized scoring criteria.
3. **Enhance DeepCredit's Tooling**: Add PDF parsing and code interpreter capabilities to enable DeepCredit to work with a broader range of financial documents and perform quantitative analysis.
4. **Refine Agent System Prompts**: Systematically improve the prompts for each agent in the DeepCredit architecture to measure incremental performance gains.
5. **Experiment with Fine-Tuning**: Begin testing fine-tuning approaches for individual agents using existing tools to improve specialized performance.
6. **Explore End-to-End Fine-Tuning**: Request research access to OpenAI's Reinforcement Fine-Tuning API (which was used to train OpenAI's Deep Research) to potentially implement end-to-end fine-tuning of the entire agentic workflow.

## Conclusion

This experiment provides valuable insights into the current state and future potential of AI-powered credit analysis. While DeepCredit v0.1 demonstrates promise as a structured approach to credit research, the superior performance of OpenAI's Deep Research highlights both the challenges ahead and the considerable potential for AI in this domain.

The next phase of research will focus on narrowing this performance gap by enhancing DeepCredit's capabilities and exploring more sophisticated prompting strategies for Deep Research. The end goal remains developing reliable AI-powered credit analysis tools that can support our organization's financial decision-making processes with comprehensive, well-reasoned assessments. 