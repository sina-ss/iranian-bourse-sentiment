# Profiling Noisy Social Media Data for Sentiment Applications

---

## 1. Article Overview

**Title:** Profiling Noisy Social Media Data for Sentiment Applications: A Visual and Analytical Framework
**Author:** Daniela Pencheva
**Year:** 2025
**Journal:** SAR Journal – Science and Research, Volume 8, Issue 3, Pages 213–224, ISSN 2619-9955
**DOI:** 10.18421/SAR83-01
**Affiliation:** Science and Research Institute, University of Economics – Varna, Bulgaria

**Main Research Domain:** Natural Language Processing (NLP), specifically Sentiment Analysis and Data Quality Management within applied AI.

**Article Type:** Applied empirical study with a conceptual framework proposal — it combines a practical experiment (on a real dataset) with framework design and visual analytics, making it part case study, part methodology paper.

---

## 2. Problem Statement & Research Gap

**Core Problem:** Social media text is inherently noisy — filled with emojis, hashtags, informal spelling, repeated characters, slang, and abbreviations. This noise systematically distorts the output of sentiment analysis tools, leading to misclassification, inflated neutral scores, and misleading analytical conclusions.

**Research Gap:** While NLP tools have advanced significantly, the field still lacks a structured, lightweight, and practically implementable framework that:

- Profiles incoming noisy text _before_ sentiment scoring,
- Quantifies how noise affects sentiment polarity distributions,
- Integrates data quality monitoring into the sentiment pipeline using accessible, low-code tools.

Most existing work either assumes clean input or applies noise-reduction as an informal preprocessing step without systematically measuring its impact.

**Significance:** Businesses and researchers increasingly rely on social media sentiment for strategic decisions (product feedback, crisis monitoring, policy evaluation). If the underlying data is noisy and unvalidated, those decisions rest on unreliable signals. The stakes are especially high in domains like public health communication, financial sentiment, and political analysis.

---

## 3. Literature Context & Background

The paper builds on several intersecting bodies of work:

**Data Quality Theory:**

- Wang & Strong (1996) — foundational framework categorizing data quality into empirical, theoretical, and intuitive dimensions.
- Olson (2003) — defines data profiling as an analytical technique for uncovering structure, content, and quality; argues poor-quality data leads to customer loss and faulty decisions.
- Otto & Österle (2016); Cichy & Rass (2019) — broader overviews of data quality frameworks.

**NLP & Sentiment Analysis:**

- Chomsky (1957) — foundational linguistic theory underlying morphological, syntactic, and semantic text processing stages.
- Hutto & Gilbert (2014) — creators of VADER, the rule-based lexicon tool used in this study.
- Xing et al. (2020) — NLP research showing that standard preprocessing (stop word removal, stemming) is insufficient to eliminate all noise sources.
- Gosh et al. — automated spelling correction improves classification accuracy.
- Bordoloi & Biswas (2023) — comprehensive survey on sentiment analysis design frameworks.

**Applied Studies Referenced:**

- Çilgin et al. (2022) — Twitter sentiment analysis during COVID-19 using VADER.
- Shad et al. (2024) — comparative ML algorithms in sentiment analysis, showing high-quality data yields significantly better results.
- Bhardwaj & Girdhar — social media sentiment analysis requires high-quality data to minimize noise.
- Dakwah et al. — political sentiment analysis requires extreme attention to data quality.

**Positioning:** The paper positions itself as a practical bridge between theoretical data quality frameworks and operational NLP pipelines, using low-code tools (Alteryx, Power BI) rather than custom code or deep learning architectures.

---

## 4. Research Objectives & Innovation

**Main Objectives:**

1. Develop a structured, modular framework for profiling noisy social media text before sentiment classification.
2. Empirically demonstrate how data quality affects VADER-based sentiment scores.
3. Visualize the before/after impact of cleansing on sentiment polarity distributions.
4. Propose a replicable workflow applicable in business intelligence contexts.

**Hypothesis:** Improved input quality leads to more distinct polarity distributions, a lower proportion of neutral misclassifications, and enhanced interpretability of sentiment scores.

**Novel Contributions:**

- Integration of a dedicated data quality assessment module directly into the sentiment analysis pipeline — treating preprocessing not as a preliminary step but as a core analytical component.
- A visual, dashboard-driven validation method (Power BI) that makes the impact of data cleansing visible to non-technical stakeholders.
- Use of Alteryx Designer to create a replicable, low-code pipeline for profiling, cleansing, and sentiment scoring.
- Demonstration that even rule-based, lexicon-oriented models (VADER) benefit significantly from structured preprocessing — without needing deep learning.

---

## 5. Methodology & Approach

**Dataset:** 1,000 user-generated tweets about the COVID-19 pandemic, sourced from Kaggle (open access, no privacy concerns). Selected to reflect realistic social media noise — informal language, emojis, inconsistent spelling, fragmented expressions.

**No Gold Standard Labels:** The study focuses on _internal consistency_ and polarity shifts caused by cleansing, not external benchmarking against labeled ground truth.

**Workflow (Three Stages):**

**Stage 1 — Data Profiling (Alteryx Designer):**

- Scanned dataset for: missing values, duplicate entries, incorrect data, inconsistent casing, excessive punctuation, elongated words (e.g., "finallyyy"), emojis, non-standard characters.
- Key metrics collected: word count distribution, frequency of non-standard characters, token patterns, string length.
- Outputs used to establish a quantitative baseline.

**Stage 2 — Data Quality Enhancement:**
Transformations applied:

- Language translation normalization
- Case normalization (lowercase standardization)
- Spell correction (e.g., "h8" → "hate", "luv" → "love")
- Removal of duplicate and empty entries
- Standardization of emojis into textual descriptions (e.g., 😡 → ":angry_face:")
- Removal of excessive punctuation and repeated characters
- Lemmatization (e.g., "running/ran/runs" → "run")
- Stop word removal ("and", "but", "the")
- POS tagging (Part-of-Speech annotation)
- Tokenization

**Guiding Principle:** Preserve original semantics (sentiment modifiers like "not", "very"; emotionally loaded informal terms like "meh", "yay") while improving formal structure for lexicon matching.

**Stage 3 — Sentiment Analysis (VADER):**

- VADER assigns polarity scores on a scale from -4.0 (extremely negative) to +4.0 (extremely positive), based on human-rated lexicon entries.
- Applied to both raw and cleansed texts to measure polarity shifts.
- Aggregate polarity calculated by summing/averaging individual word scores.

**Visualization:** Power BI dashboard with clustered bar charts, pie charts, numeric indicators, and side-by-side tweet comparison tables, comparing sentiment distributions before and after cleansing.

**Tools Compared:** Alteryx was chosen over Ataccama, Talend, and Informatica for its user-friendly interface and integrated profiling/transformation capabilities (Gartner 2024 recognized it as a leading niche player). Power BI was chosen over Tableau and Qlik for seamless Microsoft integration and rapid academic prototyping.

---

## 6. Key Findings & Results

**Quantitative Results (from the Power BI Dashboard, Figure 7):**

| Metric              | Before Cleansing | After Cleansing |
| ------------------- | ---------------- | --------------- |
| Negative sentiments | 440 (44%)        | 646 (64.6%)     |
| Neutral sentiments  | 356 (35.6%)      | 236 (23.6%)     |
| Positive sentiments | 204 (20.4%)      | 118 (11.8%)     |

**Key observations:**

- Negative sentiment count increased significantly after cleansing (from 440 to 646), suggesting many originally-noisy texts were actually negative but misclassified as neutral due to unrecognized expressions.
- Neutral misclassifications decreased substantially (from 35.6% to 23.6%), confirming the hypothesis.
- Positive sentiment count decreased slightly (204 → 118), indicating some false positives in the raw data were due to noise (e.g., emojis misinterpreted as positive signals).

**Qualitative Examples (Table 3):**

| Source Text                 | Cleaned Text                 | Polarity             |
| --------------------------- | ---------------------------- | -------------------- |
| "I h8 this app!! ughhh 😡"  | "I hate this app."           | Negative             |
| "luv it soooo much 💙💙💙"  | "Love it so much."           | Positive             |
| "idk what2say meh"          | "I do not know what to say." | Neutral              |
| "finallyyy!!! safe & sound" | "Finally! Safe and sound."   | Negative _(shifted)_ |

**Three Core Improvements Documented:**

1. **Reduction of ambiguity** — cleansed texts had clearer semantic structure, reducing neutral misclassification.
2. **Improved lexical coverage** — normalization of slang and abbreviations increased alignment with VADER lexicon entries, enabling previously unrecognized phrases to be scored.
3. **Enhanced contextual representation** — corrected word forms improved mapping between text and sentiment scores, especially for rule-based methods.

---

## 7. Practical Applications & Implications

**Business Applications:**

- Brand monitoring and customer feedback analysis on social media.
- Real-time sentiment tracking for product launches or crisis events.
- Policy evaluation based on public opinion data (health, politics, environment).

**Organizational Impact:**

- Non-technical stakeholders can use the Power BI dashboard to understand data quality effects without coding knowledge.
- The framework is modular and adaptable — the profiling module can be integrated into existing data pipelines as a preparatory layer.

**Broader AI Impact:**

- Demonstrates that data quality preprocessing deserves equal investment to model architecture choices.
- Provides a template for combining low-code BI tools with NLP pipelines, making advanced analytics accessible to smaller organizations.
- Reinforces that even simple lexicon models (VADER) can be significantly improved through structured input preparation, reducing the need for computationally expensive deep learning in many practical scenarios.

---

## 8. Limitations & Future Work

**Acknowledged Limitations:**

- **Computational intensity:** Data profiling and quality enhancement are resource-heavy, particularly for large-scale or heterogeneous datasets.
- **Scale constraints:** The framework is optimized for moderate-sized, context-specific datasets (social media posts about a targeted event). Generalizability to broader or more dynamic topics is limited.
- **Domain dependency:** The effectiveness of individual cleansing techniques (e.g., spell correction, noise removal) is highly dependent on the data domain. Impact will vary across different topics and text structures.
- **No external validation:** Without gold-standard labels, the findings reflect internal consistency improvements rather than externally benchmarked accuracy gains.
- **VADER limitations:** As a lexicon-based tool, VADER cannot capture complex contextual relationships, sarcasm, or nuanced sentiment that deep learning models handle better.

**Future Research Directions:**

- Expanding to **multilingual data sources** (explicitly mentioned as a priority — highly relevant for Persian NLP).
- Evaluating data cleansing effects across different sentiment analysis techniques, including **transformer-based models**.
- Incorporating **feedback mechanisms and dynamic data validation** into the cleansing pipeline for real-time environments.
- Integrating **machine learning methods** for scalable, automated analysis of complex datasets.
- Further refinement of the **dashboard's interactivity** for decision support systems.

---

## 9. Key Concepts & Definitions

| Term                                                        | Definition                                                                                                                                                                                         |
| ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Data Profiling**                                          | An analytical technique for systematically examining data structure, content, patterns, and quality metrics (missing values, duplicates, distributions) to establish a baseline before processing. |
| **Noisy Data**                                              | Textual data containing typographical errors, emojis, hashtags, informal language, auto-generated content, and other elements that interfere with computational analysis.                          |
| **VADER (Valence Aware Dictionary and Sentiment Reasoner)** | A rule-based lexicon tool that assigns polarity scores to words on a scale from -4.0 to +4.0 based on human ratings, optimized for informal/social media text.                                     |
| **Lexicon-Based Sentiment Analysis**                        | Sentiment classification using a predefined dictionary of words with known emotional valences, without training a statistical model on labeled data.                                               |
| **Data Completeness Rating (CR)**                           | Quantitative measure: CR = 1 − (number of data objects with missing data / total data objects).                                                                                                    |
| **Lemmatization**                                           | Reducing words to their dictionary base form using linguistic context (e.g., "running/ran/runs" → "run"), unlike stemming which uses simplified suffix removal.                                    |
| **POS Tagging**                                             | Automatic assignment of grammatical categories (noun, verb, adjective, etc.) to each word in a text, supporting syntactic analysis.                                                                |
| **Tokenization**                                            | Splitting text into individual meaningful units (tokens) — words, phrases, or sentences — as a fundamental NLP preprocessing step.                                                                 |
| **Stop Word Removal**                                       | Filtering out high-frequency, low-semantic-weight words (e.g., "and", "the", "but") to reduce noise and improve ML efficiency.                                                                     |
| **Case Normalization**                                      | Standardizing all text to lowercase (or a consistent case) to ensure the same word in different capitalizations is treated identically.                                                            |
| **Sentiment Polarity**                                      | The directional valence of expressed sentiment: positive, negative, or neutral.                                                                                                                    |
| **Value Rule Analysis**                                     | Statistical analysis calculating key metrics (min, max, standard deviation, frequency distribution, domains) to identify anomalies in data.                                                        |
| **Alteryx Designer**                                        | A low-code data analytics platform supporting data profiling, transformation, and automation, recognized in Gartner's 2024 ML platform rankings.                                                   |

---

## 10. Relevance Assessment for Your Research

### Sentiment Analysis in Financial Markets / Social Media Data Analysis

**High relevance.** The paper directly addresses the core challenge your research will face: social media text for sentiment extraction is noisy and requires structured preprocessing before any meaningful signal can be extracted. The profiling-first philosophy (characterize noise before cleaning) is directly applicable to financial social media (Twitter/X, Reddit, Telegram channels discussing stocks). The demonstrated improvement — reducing neutral misclassification from 35.6% to 23.6% — is exactly the kind of signal clarity improvement needed for financial sentiment indices.

### Persian Language Processing / Multilingual NLP

**Directly relevant, and the authors explicitly call this out as future work.** The paper acknowledges that the framework is currently English-centric (VADER is English-only) and explicitly lists multilingual expansion as a primary future direction. For Persian NLP, you would need to replace VADER with a Persian-compatible lexicon (e.g., SentiPers) or adapt a transformer-based approach, but the data quality pipeline (profiling → normalization → quality enhancement) is language-agnostic and fully applicable to Persian social media text, which has similar noise patterns (informal spelling, Arabizi-style writing, emojis, repeated characters in Farsi).

### Combining Multi-Source Data / Weighting Data Sources

**Partially relevant.** While the paper does not directly address multi-source aggregation, its modular quality framework provides a principled foundation: each data source (Twitter, Telegram, news) could be profiled independently, with cleansing rules tailored to each source's noise profile, before aggregation. The quality indicators (completeness, consistency, accuracy, timeliness) offer a natural weighting basis — sources with higher quality scores could receive higher weights in a composite sentiment index.

### Building Financial Indices / Market Sentiment Indicators

**Relevant at the methodology level.** The paper demonstrates how raw sentiment distributions (before cleaning: 35.6% neutral) become more informative signals (after cleaning: 23.6% neutral, cleaner positive/negative separation) — this principle is directly applicable to constructing financial sentiment indices, where noisy neutral classifications dilute signal quality. The before/after quantification methodology could be adapted as a quality validation step in your index construction pipeline.

### Fine-Tuning Transformer Models (BERT, GPT)

**Indirectly relevant.** The paper explicitly uses VADER instead of transformer models, noting that lexicon-based approaches are more interpretable for this purpose. However, it acknowledges that the cleansing pipeline it proposes would _also benefit_ transformer-based models — clean, normalized input improves all downstream model types. The preprocessing steps described (normalization, lemmatization, stop word removal) are standard preparatory steps for BERT fine-tuning on domain-specific financial data. The paper provides citation support for the claim that "data quality is a prerequisite for model performance regardless of architecture."

### Stock Valuation / Price Prediction

**Not addressed.** This paper does not touch financial modeling, price prediction, or backtesting. It is purely focused on sentiment classification quality.

### Backtesting / Performance Evaluation Metrics

**Not addressed.** No financial backtesting methodology is present. For financial prediction evaluation, you will need to draw on other literature.

### Behavioral Finance / Investor Psychology

**Indirectly relevant.** The paper does not discuss behavioral finance explicitly, but its demonstration that noisy text leads to misclassified sentiment has implications for behavioral finance research: studies relying on raw social media sentiment (without this kind of preprocessing) may be measuring noise rather than genuine investor psychology signals.

### Data Preprocessing of Noisy Social Media Text

**Highly relevant — this is the paper's primary contribution.** The specific techniques are directly applicable: emoji standardization, repeated character normalization, spell correction for social media slang, case normalization, stop word removal, lemmatization, and POS tagging. For financial Persian social media, you would additionally need: handling of Persian numerals and currency symbols, normalization of zero-width non-joiners (a common Persian text issue), and domain-specific financial vocabulary handling.

---

## 11. Citation-Worthy Information

**Key Statistics:**

- In the experiment on 1,000 COVID-19 tweets, neutral misclassifications decreased from **35.6% to 23.6%** after data cleansing, while correctly classified negative sentiments increased from **44% to 64.6%**.
- The study uses a dataset of **1,000 short text entries** from Kaggle, reflecting informal social media content.

**Key Claims Suitable for Citation:**

- On the importance of preprocessing: the paper argues that data profiling and cleansing should be treated "not as auxiliary steps, but as integral components of the sentiment analysis pipeline capable of directly influencing the accuracy and practical value of the results."
- On data quality and model performance: "even when the underlying model architecture remains unchanged, the input quality determines the interpretability, reliability, and richness of the extracted insights."
- On the insufficiency of standard techniques: citing Xing et al. [12], the paper notes that "standard preprocessing techniques, such as stop word removal and stemming, are insufficient for eliminating all sources of noise."

**Important Tools/Benchmarks Mentioned:**

- VADER lexicon polarity scale: -4.0 (extremely negative) to +4.0 (extremely positive); example scores: "excellent" = +2.0, "terrible" = -2.5, "safe" = +1.5.
- Alteryx Designer (Gartner 2024 recognized as leading niche player in Data Science and ML platforms).
- Completeness Rating formula: CR = 1 − (number of data objects with missing data / total data objects).

**Foundational References to Follow Up:**

- Hutto & Gilbert (2014) — original VADER paper (essential for sentiment lexicon methodology).
- Olson (2003) — foundational data quality/profiling text.
- Wang & Strong (1996) — data quality dimensions framework.
- Bordoloi & Biswas (2023) — comprehensive sentiment analysis survey.

---

## 12. Critical Analysis

**Strengths:**

- **Practical and accessible:** The use of Alteryx and Power BI (rather than custom Python code) makes the framework replicable by practitioners without deep programming expertise, which is a genuine contribution to applied NLP.
- **Transparent validation:** The Power BI dashboard provides an honest, visual comparison of before/after results, making the impact of preprocessing concrete and verifiable.
- **Modular design:** The proposed framework is well-structured and genuinely modular — the profiling module, quality enhancement module, and sentiment module are distinct and independently adaptable.
- **Clear quantitative evidence:** The reported shift from 440 to 646 negative-classified tweets is a concrete, falsifiable result.
- **Timely dataset:** COVID-19 social media data is a well-established, realistic test case for informal, noisy text.

**Weaknesses and Concerns:**

- **No gold standard evaluation:** The absence of manually labeled ground truth is a significant methodological limitation. The paper measures _change_ in sentiment scores, not whether those scores become _more accurate_. It is possible (though unlikely) that the raw scores were actually more correct in some cases. This should be a point you acknowledge when citing this work.
- **Dataset size is modest:** 1,000 tweets is a small sample for drawing generalizable conclusions about preprocessing impact. The results are illustrative, not statistically robust at scale.
- **English-only applicability of VADER:** Since VADER is inherently designed for English social media text, the sentiment scoring itself cannot generalize — only the preprocessing pipeline can. This is important for your Persian NLP research.
- **No comparison to transformer-based models:** The paper explicitly avoids deep learning. While this is a legitimate scope limitation, it means the results cannot be used to argue that preprocessing helps transformer-based models — only lexicon-based ones. The cited literature supports this broader claim, but the empirical evidence in this paper does not.
- **Cleansing rules are not fully specified:** The paper describes cleansing transformations at a conceptual level but does not provide the actual Alteryx rule specifications or dictionary entries used. This limits full reproducibility.
- **Potential for semantic distortion:** The paper acknowledges trying to preserve semantics during cleaning but does not rigorously evaluate whether any cleaning steps inadvertently removed or altered sentiment-bearing content. The example "finallyyy!!! safe & sound" being classified as _Negative_ after cleaning raises a question — "safe and sound" typically implies positive/relief sentiment. This edge case suggests the cleaning or VADER scoring may still have unresolved issues.

**Overall Convincingness:** The evidence is sufficient to support the paper's core claim that preprocessing improves lexicon-based sentiment clarity. The quantitative results (especially the neutral reduction) are meaningful and directionally convincing. However, the lack of ground truth labels and the modest dataset size mean this should be cited as a methodology and framework paper rather than as definitive empirical proof. For your research proposal, it is most useful as a foundational justification for including a dedicated data quality module in your own pipeline.
