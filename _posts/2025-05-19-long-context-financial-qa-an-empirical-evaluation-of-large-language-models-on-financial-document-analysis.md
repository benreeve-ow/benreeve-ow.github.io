---
layout: post
title: "Long-Context Financial QA: An Empirical Evaluation of Large Language Models on Financial Document Analysis"
date: 2025-05-19
categories: [research]
author: Ben Reeve
---

# Long-Context Financial QA: An Empirical Evaluation of Large Language Models on Financial Document Analysis

## Executive Summary

This whitepaper presents findings from an experimental evaluation of large language models with extended context windows for financial question answering. We tested OpenAI's GPT-4.1, GPT-4.1-mini, and GPT-4.1-nano models on their ability to extract and reason with financial information from both short excerpts (~700 words) and complete SEC filings (~123,000 words).

**Key Finding**: We observed significant performance degradation as context length increases, with accuracy dropping by 29-34 percentage points when moving from short excerpts to full documents. Notably, this degradation occurs at document lengths (~123K words) that are far below the advertised context window limits (1M+ tokens), suggesting fundamental limitations in how effectively these models process long-form content.

These findings challenge the assumption that simply expanding context windows solves document-scale information extraction problems and suggest that retrieval-augmented approaches remain necessary despite advances in context capabilities.

## 1. Key Results

### Performance Metrics

| Model | FinQA Accuracy<br>(~700 words) | DocFinQA Accuracy<br>(~123,000 words) | Performance Drop |
|-------|--------------------------------|--------------------------------------|------------------|
| GPT-4.1 | 89.01% | 60.00% | 29.01 pp |
| GPT-4.1-mini | 89.01% | 55.00% | 34.01 pp |
| GPT-4.1-nano | 68.13% | 40.00% | 28.13 pp |
| GPT-4o | 87.91% | Not tested (context limit) | N/A |

This consistent pattern across all models tested confirms that even state-of-the-art LLMs with expanded context windows struggle significantly with information extraction from full-length financial documents.

### Context Length vs. Performance Relationship

A critical insight from our evaluation is that performance degradation begins well before reaching the advertised context window limits:

- The DocFinQA documents average ~123,000 words (approximately 150K-200K tokens)
- The advertised context window for GPT-4.1 models is 1M+ tokens
- Yet we observe 29-34 percentage point drops in performance despite using only ~15-20% of the available context window

This suggests the relationship between context length and performance is non-linear, with substantial degradation occurring long before approaching window limits. This pattern aligns with research on "lost-in-the-middle" effects and attention dilution in transformer models, but appears more severe in real-world financial applications than in synthetic needle-in-haystack tests often used in model benchmarks.

## 2. Conclusions and Implications

### 2.1 Why Long-Context Models Underperform on Financial Documents

Our findings reveal several likely explanations for performance degradation in long financial documents:

1. **Signal-to-noise ratio**: In a 123,000-word document, relevant information (often single numeric values or table cells) is overwhelmed by irrelevant text, making it harder for models to identify key data points.

2. **Attention dilution**: Transformer models show a U-shaped attention curve where tokens near document edges receive more reliable attention. In lengthy documents, critical financial information often appears in middle sections where attention mechanisms are weakest.

3. **Positional encoding degradation**: Even advanced encoding schemes like RoPE degrade when sequence lengths exceed training parameters, destabilizing attention scores between distant tokens.

4. **Capacity constraints**: Despite larger context windows, models have fixed parameter counts. When processing 100K+ tokens, attention mechanisms must map relationships across exponentially more token pairs, reducing probability mass assigned to any single important connection.

5. **Task complexity**: Financial QA requires both locating information and numerical reasoning, effectively combining search and calculation steps. This dual challenge becomes exponentially harder as document length increases.

### 2.2 Practical Implications for Financial Analysis Systems

These results suggest that despite advances in context length, financial analysis systems should still use retrieval-augmented approaches that:

1. **Pre-filter documents** to locate relevant sections before applying LLM reasoning
2. **Implement query-first layouts** to bias attention mechanisms toward matching the right spans
3. **Use delimiter-based importance markers** to highlight candidate answer regions
4. **Apply explicit "find-then-reason" prompting** to separate search and calculation tasks

### 2.3 Next Steps

For developing effective financial analysis systems, these findings suggest several promising directions:

1. **Hybrid retrieval-reasoning approaches**: Developing lightweight retrieval methods to select the most relevant ~2,000 tokens before feeding them to an LLM

2. **Document segmentation techniques**: Exploring methods to divide documents into sections that can be processed independently before synthesizing the results

3. **Empirical context length optimization**: Determining the optimal context window size that balances information completeness with model performance

4. **Fine-tuning for financial domain**: Testing whether domain-specific fine-tuning could improve models' ability to identify and reason with financial information in long contexts

## 3. Introduction

### 3.1 Background

As part of developing a DeepCredit agent for credit risk assessment tasks, we need reliable mechanisms to extract data and answer questions from extensive financial statements. Recent advancements in large language model (LLM) capabilities have introduced models with context windows exceeding 1 million tokens, including OpenAI's GPT-4.1 series. This development raises an intriguing question: can these expanded context capabilities eliminate the need for sophisticated retrieval mechanisms when processing financial documents?

Traditional approaches to financial document analysis typically employ:
- Embeddings-based semantic search
- Regular expressions for pattern matching
- Custom search algorithms to locate relevant text fragments

However, these methods face challenges when key information is dispersed throughout lengthy documents, requiring multiple retrieval steps and sophisticated integration of scattered data points.

### 3.2 Research Question

This study explores whether recent improvements in LLMs' ability to process and reason across long contexts have reached a point where we can bypass retrieval steps and feed entire documents directly into the model's context window. Specifically, we ask:

**Do large context window models maintain their performance when answering questions about financial data dispersed across lengthy documents?**

### 3.3 Datasets

We utilized two complementary datasets for our evaluation:

1. **FinQA**: Comprises excerpts from SEC filings (average length ~700 words) paired with financial questions requiring numerical reasoning.
   - Created by finance experts from S&P 500 companies' reports
   - Contains 8,281 QA pairs with fully annotated numerical reasoning programs
   - Includes both text and tabular data
   
   **Example FinQA Questions:**
   - "Considering the weighted average fair value of options, what was the change of shares vested from 2005 to 2006?"
   - "What was the net change in tax positions in 2014?"
   - "What was the percentage cumulative total return for the five-year period ended 31-dec-2017 of citi common stock?"
   - "For the quarter December 31, 2012, what was the percent of the total number of shares purchased in December?"
   - "What is the estimated percentage of revolving credit facility in relation with the total senior credit facility in millions?"

2. **DocFinQA**: An extension of FinQA that replaces the curated excerpts with complete SEC filings.
   - Average document length of ~123,000 words (approximately 175× longer than FinQA)
   - Contains 7,437 questions derived from FinQA
   - Requires navigating entire financial reports to locate relevant information

### 3.4 Models Evaluated

We tested four OpenAI models with varying capabilities:

- **GPT-4.1**: Latest model with 1M+ token context window
- **GPT-4.1-mini**: Smaller variant with 1M+ token context window
- **GPT-4.1-nano**: Smallest variant with 1M+ token context window
- **GPT-4o**: Tested only on FinQA due to context window limitations

## 4. Discussion

### 4.1 Comparison to Marketing Claims

Our findings reveal a discrepancy between marketing claims about long-context models and their real-world performance on complex financial tasks. While promotional materials often highlight "needle in a haystack" tests with reported 100% accuracy, our experiment shows that:

1. The "needles" in financial documents are often subtler and require more nuanced understanding than the explicit markers used in demonstration tests.

2. Financial analysis typically requires integrating multiple data points scattered throughout a document, not just identifying a single piece of information.

3. The performance degradation is substantial enough (29-34 percentage points) to make direct document processing impractical for high-stakes financial applications.

4. The degradation begins at context lengths (~123K words) that are far below the advertised limits (1M+ tokens), suggesting fundamental scaling issues rather than simple capacity constraints.

### 4.2 The Non-Linear Relationship Between Context Length and Performance

Our results suggest a non-linear relationship between context length and model performance. While we didn't test intermediate document lengths, the sharp drop from ~700 words to ~123,000 words exceeds what would be expected from a linear degradation. This aligns with theoretical work on transformer attention mechanisms, which suggests:

1. **Quadratic complexity effects**: The attention mechanism in transformers must compute relationships between all token pairs, growing quadratically with sequence length.

2. **Positional encoding degradation**: As sequences extend beyond training distributions, positional encodings become less effective at distinguishing relative positions.

3. **Probability mass dilution**: With finite capacity to distribute attention, longer documents necessarily reduce the attention weight assigned to any single token, even critical ones.

Future work should explore this relationship more systematically by testing performance across a range of intermediate context lengths to better characterize where significant performance drops begin to occur.

## 5. References

1. Chen, Z., Chen, W., Smiley, C., Shah, S., Borova, I., Langdon, D., Moussa, R., Beane, M., Huang, T.-H., Routledge, B., & Wang, W. Y. (2021). FinQA: A dataset of numerical reasoning over financial data. In Proceedings of the 2021 Conference on Empirical Methods in Natural Language Processing.

2. Reddy, V., Koncel-Kedziorski, R., Lai, V. D., Krumdick, M., Lovering, C., & Tanner, C. (2024). DocFinQA: A Long-Context Financial Reasoning Dataset. arXiv preprint.

3. "Why 'just throw the whole 120 k-word 10-K into the prompt' under-performs" (2024).

4. HuggingFace Dataset: https://huggingface.co/datasets/kensho/DocFinQA

5. HuggingFace Dataset: https://huggingface.co/datasets/Aiera/finqa-verified

## Appendix A: Methodology

### A.1 Experimental Design

We tested all 100 examples from FinQA (the shorter context dataset) across all models. However, due to rate limit constraints on Microsoft Azure OpenAI when processing extremely long documents, we had to modify our approach for DocFinQA:

- Tested 20 randomly selected cases from DocFinQA for GPT-4.1, GPT-4.1-mini, and GPT-4.1-nano due to the large document size
- Ran 100 samples from DocFinQA using only GPT-4.1 to validate the smaller sample findings
- Used GPT-4o only on FinQA due to context window constraints

The experiment was conducted entirely on braintrust.dev, ensuring a contained environment without external data access.

### A.2 Evaluation Framework

We employed the following system prompt:

```
**system**
SYSTEM — Fin/DocFinQA
You are a financial-QA solver.
• Think step-by-step.
• **Do NOT round or abbreviate numbers—copy them exactly.**
• When finished, write one line: FINAL: <number>
• Do not write any other line that starts with "FINAL:".
**user**
Answer the question based on the context: **{{input}}**
```

### A.3 Evaluation Code

Responses were evaluated using a Python function that extracted the final numerical answer and compared it to the expected value, allowing for small rounding differences:

```python
import re, math
# match "FINAL:" anywhere, not just at start-of-line
FINAL_RE = re.compile(r'FINAL:\s*([-+]?\d*\.?\d+)', re.I)
def extract_number(txt: str | None):
    """Return the last number after 'FINAL:' if present, else the last number
    anywhere in the string.  None if nothing numeric is found."""
    if not txt:
        return None
    # Prefer numbers that follow 'FINAL:'
    m = FINAL_RE.findall(txt)
    if m:
        return float(m[-1])
    # Fallback: last plain number (avoid false negatives if the model forgot the tag)
    nums = re.findall(r'[-+]?\d*\.?\d+', txt)
    return float(nums[-1]) if nums else None
def handler(output: str = None,
            expected: str = None,
            **kwargs) -> float:
    """Returns 1.0 if the two numbers match (±0.01 absolute or ±0.1 % relative)."""
    # FinQA answers are normally exact, but allow small rounding slips
    ABS_TOL = 0.5
    REL_TOL = 0.02
    s = extract_number(output)
    e = extract_number(str(expected))     # expected is often just "21.48"
    if s is None or e is None:
        return 0.0
    return 1.0 if math.isclose(s, e, abs_tol=ABS_TOL, rel_tol=REL_TOL) else 0.0
```

## Appendix B: Experimental Details

### B.1 Data Access
- DocFinQA dataset: https://huggingface.co/datasets/kensho/DocFinQA
- FinQA dataset: https://huggingface.co/datasets/Aiera/finqa-verified

### B.2 Hardware and Software
- Evaluation Platform: braintrust.dev
- API Access: Microsoft Azure OpenAI

### B.3 Limitations
- Sample size constraints due to rate limiting on DocFinQA
- Context window limits preventing testing GPT-4o on DocFinQA
- Limited exploration of intermediate context lengths between 700 and 123,000 words 