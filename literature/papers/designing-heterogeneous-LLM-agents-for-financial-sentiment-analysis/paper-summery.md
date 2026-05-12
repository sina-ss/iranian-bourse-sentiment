# Designing Heterogeneous LLM Agents for Financial Sentiment Analysis

## 1. Article Overview

**Title:** Designing Heterogeneous LLM Agents for Financial Sentiment Analysis

**Author:** Frank Xing, Department of Information Systems and Analytics, National University of Singapore

**Publication Details:** ACM Transactions on Management Information Systems, Vol. 16, No. 1, Article 5, February 2025, 24 pages

**Main Research Domain:** Financial sentiment analysis (FSA) within AI/Natural Language Processing, specifically focusing on multi-agent large language model collaboration

**Article Type:** Empirical study with design science research methodology, including theoretical framework development, experimental validation, and case study analysis

## 2. Problem Statement & Research Gap

**Specific Problem:** Traditional financial sentiment analysis systems face limitations due to the discriminative nature of the task and lack of prescriptive knowledge on leveraging existing generative LLMs without fine-tuning.

**Research Gap Identified:**

- Most FSA systems rely on fine-tuning approaches which are computationally expensive and require extensive labeled datasets
- Limited research on using generative LLMs (decoder-based transformers like GPT) for discriminative FSA tasks
- Existing multi-agent LLM frameworks employ homogeneous agents without theoretical grounding
- Lack of design theory for creating specialized heterogeneous agents for FSA

**Significance:** FSA is increasingly important as financial services digitalize, with clear evidence from events like GameStop saga and popularity of sentiment indexes like MarketPsych. Accurate FSA is crucial for forecasting returns, detecting fraud, and predicting risk.

## 3. Literature Context & Background

**Prior Work Foundation:**

- Early FSA systems relied on sentiment dictionaries and rule-based approaches
- Learning-based systems emerged using CNN, SVR models with combined lexical and dense word features
- Recent wave (2019+) based on fine-tuning pre-trained models like BERT (FinBERT achieving state-of-the-art)
- Current progress mainly uses encoder-type transformers, but most powerful LLMs are decoder-based

**Positioning Relative to Literature:**

- Differentiates from ad hoc multi-agent designs (Chain of Thought, Tree of Thoughts)
- Builds on design science guidelines by Hevner et al.
- Contrasts with homogeneous multi-agent frameworks (Multi-agent Debate, Multi-role Negotiation)

**Key Theoretical Foundations:**

- Minsky's theory of mind and emotions as kernel theory
- Society of mind perspective on human intelligence
- Linguistic error categorization from Zimbra et al. and Xing et al.
- Behavioral finance literature on institutional vs. individual investor differences

## 4. Research Objectives & Innovation

**Main Objectives:**

- Investigate effectiveness of using LLMs without fine-tuning for FSA
- Develop theory-informed heterogeneous multi-agent framework
- Test whether linguistic error types and investor domain knowledge can guide agent design

**Novel Contributions:**

- **Heterogeneous multi-Agent Discussion (HAD) framework:** Unlike homogeneous approaches, uses specialized agents based on linguistic and financial domain knowledge
- **Theoretical grounding:** First to apply Minsky's emotion theory to LLM agent design for FSA
- **Design science approach:** Follows systematic design theory development rather than ad hoc solutions
- **Zero-shot, training-free framework:** Provides useful explanations while avoiding fine-tuning costs

**Innovation Claims:**

- Simulates mental "resources" using specialized LLM agents
- Demonstrates that simple prompt templates can create heterogeneous behavior
- Shows 20-50% improvement over naive prompting, closing gap with fine-tuning approaches

## 5. Methodology & Approach

**Research Methods:**

- **Design Science Research:** Following Hevner et al. guidelines
- **Empirical evaluation:** Performance metrics on 6 FSA datasets
- **Ablation analysis:** Testing contribution of individual agents
- **Case study analysis:** Qualitative examination of agent discussions

**Framework Architecture:**

```
1. Define heterogeneous agents A1, A2, ..., Ak with specialized prompts
2. Obtain intermediary analysis: Oi = Ai(User_Message)
3. Generate summative analysis: Result = A(User_Message, O1, ..., Ok)
```

**Agent Design:**

- **5 Linguistic agents** based on FSA error types:

  - A1 (Mood): Focus on irrealis mood
  - A2 (Rhetoric): Attention to sarcasm, negative assertion
  - A3 (Dependency): Speaker vs. third party sentiment
  - A4 (Aspect): Stock ticker focus vs. other entities
  - A5 (Reference): Time expressions, prices, external facts

- **2 Domain knowledge agents** based on investor types:
  - A6 (Institutional): Long-term, fundamental focus
  - A7 (Individual): Price changes, technical indicators

**Base Models Tested:**

- GPT-3.5 Turbo and GPT-4o (commercial)
- LlaMa3-70B (open-access)
- BLOOMZ-560M (open-access, smallest)

## 6. Key Findings & Results

**Performance Improvements:**

- HAD achieved best performance in 12 out of 18 experiments
- Consistent improvements over baseline: 20-50% gap closure between ICL and fine-tuning
- More pronounced improvements with advanced base models (GPT-3.5, LlaMa3)

**Quantitative Results (Selected):**

- **FPB Dataset:** GPT-3.5 baseline (78.58% acc, 81.06% F1) → HAD (81.25% acc, 87.10% F1)
- **FiQA Dataset:** GPT-3.5 baseline (90.53% acc, 92.41% F1) → HAD (95.07% acc, 96.20% F1)

**Benchmark Comparisons:**

- **HAD:** 12/18 best performances
- **Multi-agent Debate (MD):** 12/16 better than naive prompting
- **Multi-agent Simple Voting (MSV):** 9/16 better than naive prompting
- **Heterogeneous Simple Voting (HSV):** 6/16 better than naive prompting

**Agent Importance Ranking:**

- Most important: {A6, A7} (institutional/individual agents)
- Moderately important: {A1, A2, A4} (mood, rhetoric, aspect agents)
- Less important: {A3, A5} (dependency, reference agents)

## 7. Practical Applications & Implications

**Real-world Applications:**

- **Financial advisory services:** Customizable FSA tools with client-specific constraints
- **Trading and investment:** Enhanced market sentiment analysis for decision-making
- **Risk management:** Improved fraud detection and risk prediction
- **Portfolio management:** Better sentiment-aware asset allocation

**Organizational Impact:**

- **Cost reduction:** Avoids expensive fine-tuning while maintaining performance
- **Interpretability:** Provides explanations through agent discussions
- **Scalability:** Framework adaptable to different financial contexts
- **Competitive advantage:** Enhanced sentiment analysis capabilities

**Industry Implications:**

- **Financial technology:** New paradigm for sentiment analysis tools
- **Investment firms:** Improved fundamental and technical analysis
- **Regulatory compliance:** Better detection of market manipulation through sentiment

**Future AI Development:**

- Demonstrates viability of specialized multi-agent approaches
- Provides blueprint for theory-informed LLM collaboration
- Shows potential for emotion theory application in AI systems

## 8. Limitations & Future Work

**Acknowledged Limitations:**

**Scalability Issues:**

- LLM agent discussions are slower than statistical analysis
- Computational costs increase with number of agents
- Large-scale systems challenging to design and evaluate

**Data Confidentiality Concerns:**

- Some evaluation datasets may have been exposed to LLMs during training
- Potential information leakage, especially for older datasets (FPB, FiQA)
- LLM training transparency limitations

**Experimental Constraints:**

- Limited scale of ablation studies due to computational costs
- Agent importance analysis primarily based on GPT-3.5
- Generalizability to other LLMs needs investigation

**Suggested Future Directions:**

- **Error analysis:** Investigate new error types made by LLMs vs. traditional methods
- **Human performance benchmarking:** Large-scale expert evaluation on FSA datasets
- **Scalability solutions:** Optimize framework for larger agent ensembles
- **Cross-domain application:** Test framework effectiveness beyond FSA
- **Dynamic agent selection:** Develop methods for context-aware agent activation

## 9. Key Concepts & Definitions

**Core Theoretical Concepts:**

- **Society of Mind:** Reductionistic view that intelligence emerges from interaction of simpler, non-intelligent agents
- **Emotional States as Activation Patterns:** Emotions result from specific resource activation/suppression patterns
- **Heterogeneous vs. Homogeneous Agents:** Specialized function agents vs. identical capability agents

**Technical Terminology:**

- **In-Context Learning (ICL):** Using LLMs without fine-tuning through appropriate prompting
- **Heterogeneous multi-Agent Discussion (HAD):** Proposed framework using specialized agents with summative reasoning
- **Design Science Research:** Systematic approach to creating and evaluating design artifacts
- **Kernel Theory:** Natural/social science theory informing information system design

**Financial Concepts:**

- **Irrealis Mood:** Linguistic feature expressing hypothetical/uncertain statements
- **Institutional vs. Individual Investors:** Behavioral dichotomy in investment approaches
- **Aspect-Based Sentiment Analysis:** Sentiment analysis focused on specific entities/attributes

**Evaluation Metrics:**

- **Macro F-1 Score:** Performance metric accounting for class imbalance
- **Ablation Analysis:** Systematic removal of components to assess individual contributions

## 10. Relevance Assessment

### Direct Relevance to Your Research Interests:

**Financial Markets Sentiment Analysis:**

- **Core application domain:** Paper directly addresses financial sentiment analysis challenges
- **Multi-source data integration:** Framework demonstrates combining different analytical perspectives
- **Market sentiment indicators:** Shows potential for building sophisticated financial indices

**Social Media Data Analysis:**

- **Dataset coverage:** Includes StockTwits, Reddit, CoinMarketCap data
- **Text preprocessing:** Addresses noisy social media text challenges
- **Cross-platform analysis:** Framework applicable to multiple social media sources

**Persian Language Processing/Multilingual NLP:**

- **Framework transferability:** Theory-informed design likely adaptable to other languages
- **Agent specialization:** Could incorporate Persian-specific linguistic error patterns
- **Limited direct applicability:** Study focuses on English financial texts

**Combining Multi-source Data:**

- **Agent-based integration:** Each agent could represent different data source
- **Weighting mechanisms:** Summative agent provides natural weighting approach
- **Heterogeneous perspectives:** Framework designed for diverse information synthesis

**Transformer Model Fine-tuning:**

- **Alternative to fine-tuning:** Paper explicitly avoids fine-tuning, using prompting instead
- **Performance comparison:** Shows 20-50% gap closure with fine-tuned models
- **Cost-benefit analysis:** Demonstrates trade-offs between fine-tuning and prompting approaches

**Stock Valuation/Price Prediction:**

- **Sentiment-price relationship:** Framework could inform price prediction models
- **Behavioral finance insights:** Incorporates institutional vs. individual investor perspectives
- **Limited direct modeling:** Focuses on sentiment classification, not price prediction

**Backtesting Methodologies:**

- **Performance evaluation:** Comprehensive evaluation across 6 datasets provides methodological insights
- **Ablation testing:** Systematic component evaluation applicable to backtesting
- **Cross-validation approaches:** Multiple LLM testing provides robustness insights

**Behavioral Finance/Investor Psychology:**

- **Strong relevance:** Framework explicitly incorporates investor behavioral differences
- **Psychological modeling:** Uses emotion theory as foundational framework
- **Sentiment measurement:** Provides sophisticated approach to capturing investor psychology

## 11. Citation-Worthy Information

**Key Performance Statistics:**

- "HAD can fix 20%–50% of the gap between ICL and fine-tuning" (p. 5:12)
- HAD achieved best performance in 12 out of 18 experiments across different LLMs and datasets
- Framework improves accuracy consistently when using advanced base models (GPT-3.5, LlaMa3)

**Important Datasets Referenced:**

- Financial PhraseBank (FPB), StockSen, CMC, FiQA Task 1, SEntFiN 1.0, FinEntity
- Combined dataset size: >33,000 financial text samples across news, social media, forums

**Significant Comparative Results:**

- GPT-3.5 + HAD vs. baseline on FiQA: 95.07% accuracy vs. 90.53% (4.54% improvement)
- Framework particularly effective for ternary classification problems (positive/negative/neutral)

**Novel Methodological Contributions:**

- First application of Minsky's emotion theory to multi-agent LLM design
- "simple template 'please pay special attention to [error type]' can change LLM agents' attention and prompt them to behave differently" (p. 5:4)

**Theoretical Insights:**

- "emotions come from the managed interaction of a variety of resourceful but simpler and non-intelligent agents" (p. 5:6)
- Demonstrates that voting mechanisms are inadequate for multi-agent integration - discussion mechanisms superior

## 12. Critical Analysis

**Research Strengths:**

**Theoretical Rigor:**

- Strong theoretical foundation using Minsky's emotion theory
- Systematic design science approach rather than ad hoc development
- Clear connection between kernel theory and practical implementation

**Comprehensive Evaluation:**

- Multiple datasets spanning different financial text types
- Various LLM architectures tested (commercial and open-source)
- Both quantitative metrics and qualitative case studies

**Practical Relevance:**

- Addresses real industry need for cost-effective FSA solutions
- Framework provides interpretable results through agent discussions
- Demonstrates clear performance improvements over baselines

**Potential Weaknesses and Concerns:**

**Limited Theoretical Validation:**

- While Minsky's theory provides inspiration, the connection between "emotional resources" and FSA error types may be tenuous
- No empirical validation that the proposed agents actually simulate different "mental resources"
- Agent design based on limited error categorization studies

**Experimental Limitations:**

- **Data contamination concerns:** Acknowledged but not addressed - some datasets may have been in LLM training data
- **Limited generalizability:** Agent importance analysis primarily on GPT-3.5
- **Computational cost analysis missing:** No detailed comparison of cost vs. performance trade-offs

**Methodological Concerns:**

- **Ablation study scope:** Limited to three datasets due to computational constraints
- **Agent interaction complexity:** Non-linear agent interactions acknowledged but not thoroughly investigated
- **Baseline comparisons:** Limited comparison with more sophisticated prompting techniques beyond naive approaches

**Statistical Rigor:**

- No statistical significance testing reported for performance improvements
- No confidence intervals or error bars provided for results
- Limited discussion of variance across multiple runs

**Framework Limitations:**

- **Scalability questions:** Framework may not scale to larger numbers of agents
- **Domain specificity:** Unclear how well linguistic agents transfer to other financial contexts
- **Agent dependency:** Success heavily dependent on quality of summative agent reasoning

**Evidence Quality Assessment:**
The paper provides convincing evidence for the framework's effectiveness within the tested scope, but several concerns limit confidence in broader applicability. The performance improvements are consistent across datasets and models, suggesting real benefits. However, the theoretical connection between emotion theory and FSA could be stronger, and the experimental design could address data contamination concerns more rigorously.

**Overall Assessment:**
This represents solid applied research with practical value, but the theoretical contributions are somewhat incremental. The work successfully demonstrates that theory-informed agent design can improve multi-agent LLM performance, though the specific theoretical grounding could be more rigorously validated. The framework shows promise for financial applications but requires further validation for broader claims about emotion theory in AI systems.
