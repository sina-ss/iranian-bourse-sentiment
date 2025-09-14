# FX Sentiment Analysis with Large Language Models

## 1. Article Overview

**Title**: FX sentiment analysis with large language models  
**Authors**: Daniele Ballinari (Swiss National Bank), Jessica Maly (University of St. Gallen and Thurgau Institute for Digital Transformation)  
**Publication Year**: 2025  
**Journal/Conference**: SNB Working Papers 11/2025  
**Main Research Domain**: Financial Natural Language Processing, Foreign Exchange Markets, Large Language Models  
**Article Type**: Empirical study with practical trading applications

## 2. Problem Statement & Research Gap

**Specific Problem Addressed:**

- The foreign exchange (FX) market, with $7+ trillion daily trading volume, uses exceptionally complex language with specialized jargon and inherent currency pair relativity (e.g., EUR/USD), creating significant challenges for accurate sentiment classification
- Traditional sentiment analysis methods struggle to capture nuances in FX market language, particularly the relative nature of currency pairs
- Despite success in equity markets, sentiment analysis application in FX markets remains relatively unexplored

**Research Gap:**

- Lack of publicly available labeled FX sentiment datasets
- Existing financial models (like FinBERT) are not specifically tailored for FX market complexities
- No distinction between past and future sentiment in financial news analysis
- Limited application of state-of-the-art LLMs to domain-specific FX sentiment analysis

**Significance:**
The FX market is the world's largest financial market, making accurate sentiment analysis crucial for understanding market dynamics and investment decision-making.

## 3. Literature Context & Background

**Prior Work Foundation:**

- Traditional lexicon-based approaches (VADER, Loughran-McDonald dictionary) often struggle with context sensitivity and financial terminology
- FinBERT represents advancement over traditional methods but faces challenges with numerical data sensitivity and declining accuracy with sentence complexity
- Recent models like FinGPT, Instruct-FinGPT, FinLlama, and BloombergGPT show progress but have limitations:
  - Many are not open source (BloombergGPT, FinGPT)
  - Not specifically tailored for FX markets
  - Cannot handle unique FX challenges like relative currency pair nature

**Theoretical Foundations:**

- Builds on transformer-based architecture advancements
- Leverages distant labeling methodologies from Chen et al. (2022) and Ke, Kelly, and Xiu (2019)
- Incorporates recent advances in parameter-efficient fine-tuning (QLoRA)

**Positioning Relative to Literature:**
This work specifically addresses the gap in FX-focused sentiment analysis by tailoring LLMs to FX domain complexities, unlike existing approaches that rely on generic sentiment models.

## 4. Research Objectives & Innovation

**Main Objectives:**

1. Fine-tune state-of-the-art LLMs (Llama 3.1 8B) for FX-specific sentiment analysis
2. Compare performance against traditional methods and existing financial models
3. Demonstrate practical utility through trading strategy construction and evaluation
4. Address temporal dynamics by distinguishing past vs. future sentiment

**Novel Contributions:**

1. **Domain-specific fine-tuning**: First application of Llama 3.1 8B to FX sentiment analysis with limited labeled data
2. **Hybrid labeling approach**: Combines human labeling (high quality) with distant labeling (scalability)
3. **Temporal sentiment distinction**: Novel framework separating past and future sentiment labels
4. **Multi-currency classification**: Simultaneous sentiment classification for G10 currencies within single articles
5. **Practical validation**: Real-world trading strategy implementation and backtesting

**Advancement of State-of-the-Art:**

- Demonstrates superiority over traditional lexicon-based methods and existing financial models
- Introduces scalable methodology for creating FX sentiment datasets
- Provides open-source approach (unlike proprietary alternatives)

## 5. Methodology & Approach

**Research Design:** Mixed-methods approach combining model development, evaluation, and practical application

**Data Collection:**

- Scraped 251,845 articles from three major FX platforms: Investing.com (77,789), DailyFX (45,593), FXStreet (128,463)
- Timeframes: Investing.com (Oct 2011-June 2024), DailyFX (Jan 2015-June 2024), FXStreet (Oct 2018-June 2021)
- Applied filtering: minimum 20 words, duplicate removal, character limits

**Labeling Methodology:**

1. **Human Labeling**: 1,068 articles with rigorous annotation process, achieving 2.7% error rate
2. **Distant Labeling**: 30,000 articles using return-based labels (5-day windows, 30% appreciation/depreciation thresholds)

**Model Architecture:**

- Base model: Meta's Llama 3.1 8B parameters
- Fine-tuning technique: QLoRA (Quantized Low-Rank Adaptation)
- Training parameters: 3 epochs (distant), 10 epochs (human), rank 8, scaling factor 16

**Evaluation Framework:**

- Performance metrics: Accuracy, F1-score
- Baseline comparisons: FinBERT, VADER, Loughran-McDonald dictionary, untuned Llama
- Trading strategy evaluation: Sharpe ratios, maximum drawdown, annualized returns

**Trading Strategy Implementation:**

- Daily sentiment scoring using log-difference of appreciation/depreciation counts
- Zero-cost portfolio construction with long/short positions
- Performance evaluation across multiple data sources

## 6. Key Findings & Results

**Classification Performance:**

- Fine-tuned Llama (DL & HL) achieved highest accuracy: 60% (past sentiment), 56% (future sentiment)
- Outperformed all baselines: FinBERT (50%/43%), VADER (47%/44%), LM-dictionary (44%/38%)
- F1 scores: 0.62 (past), 0.56 (future) for fine-tuned model
- Appreciation/depreciation classes performed better than "unchanged" class across all models

**Trading Strategy Results:**

- **DailyFX**: Fine-tuned Llama achieved 3.29% annualized return, 0.42 Sharpe ratio, 7.97% max drawdown
- **Investing.com**: 1.27% annualized return, 0.17 Sharpe ratio (outperformed by LM-dictionary: 3.02%, 0.45 Sharpe)
- **FXStreet**: Positive returns but weaker performance; VADER performed best (10.99% return, 1.70 Sharpe ratio)

**EUR/JPY Specific Results:**

- Strong performance on sentiment-sensitive currency pair
- DailyFX: 2.49% annualized return, 0.43 Sharpe ratio
- Investing.com: 3.59% annualized return, 0.56 Sharpe ratio
- Lower rebalancing frequency (92 times/year vs. 252 for traditional methods)

**Key Quantitative Evidence:**

- Consistent positive cumulative returns throughout sample period for fine-tuned model
- Statistical significance tests showed some differences significant at 5-10% levels, but became insignificant after multiple testing corrections
- Lower transaction costs due to reduced rebalancing frequency

## 7. Practical Applications & Implications

**Real-World Applications:**

1. **Automated FX Trading**: Direct implementation in quantitative trading strategies with demonstrated profitability
2. **Risk Management**: Enhanced ability to capture market sentiment shifts for portfolio risk assessment
3. **Market Analysis**: Improved interpretation of FX news for financial analysts and traders
4. **Research Tools**: Methodology applicable to other specialized financial domains

**Organizational Impact:**

- **Central Banks**: Enhanced monitoring of FX market sentiment and communication effectiveness
- **Investment Banks**: Improved algorithmic trading strategies and client advisory services
- **Asset Managers**: Better-informed currency hedging and portfolio allocation decisions
- **Fintech Companies**: Integration into automated trading platforms and sentiment dashboards

**Industrial Implications:**

- Demonstrates feasibility of domain-specific LLM applications in high-stakes financial environments
- Provides cost-effective alternative to proprietary financial NLP solutions
- Establishes framework for applying LLMs to other specialized financial markets

**Societal Level:**

- Contributes to more efficient FX market functioning through improved information processing
- Democratizes access to sophisticated sentiment analysis tools via open-source approach
- Advances transparency in algorithmic trading methodologies

## 8. Limitations & Future Work

**Acknowledged Limitations:**

1. **Data Scarcity**: Limited availability of labeled FX sentiment datasets remains a constraint
2. **Look-ahead Bias**: Potential concerns due to model training period overlap (though authors argue this is unlikely to be primary driver)
3. **Temporal Coverage**: FXStreet dataset limited to 2018-2021 period
4. **Model Size**: Computational constraints limited to 8B parameter model
5. **Currency Coverage**: Focus on G10 currencies may not generalize to emerging market currencies

**Challenges Encountered:**

- Computational resource limitations for processing larger datasets
- Difficulty in obtaining comprehensive FXStreet archive data
- Balancing annotation quality vs. scalability in labeling process
- "Unchanged" class classification proved challenging across all models

**Future Research Directions:**

1. **Expanded Datasets**: Development of larger, more comprehensive labeled FX datasets
2. **Higher Frequency Trading**: Application to intraday and high-frequency trading strategies
3. **Multi-modal Analysis**: Integration of numerical data, charts, and text for enhanced sentiment analysis
4. **Cross-lingual Expansion**: Extension to non-English FX news sources
5. **Real-time Implementation**: Development of streaming sentiment analysis systems
6. **Larger Models**: Investigation of performance gains from larger LLMs (70B+ parameters)
7. **Alternative Architectures**: Exploration of other transformer-based models and ensemble methods

## 9. Key Concepts & Definitions

**Core Technical Terms:**

- **QLoRA (Quantized Low-Rank Adaptation)**: Parameter-efficient fine-tuning technique combining 4-bit quantization with LoRA-style adaptation
- **Distant Labeling**: Automated labeling methodology using observed market returns to assign sentiment labels
- **G10 Currencies**: Ten most traded currencies globally (USD, EUR, JPY, GBP, CHF, SEK, NOK, NZD, AUD, CAD)
- **Zero-cost Portfolio**: Investment strategy where long and short positions balance to require no net capital
- **Temporal Sentiment Distinction**: Separation of sentiment into past (retrospective) and future (prospective) components

**Financial Concepts:**

- **FX Market Relativity**: Inherent characteristic where currency values are always expressed relative to another currency
- **Currency Pair Interpretation**: Understanding that EUR/USD appreciation implies EUR strength and USD weakness
- **Sharpe Ratio**: Risk-adjusted return metric (return per unit of volatility)
- **Maximum Drawdown**: Largest peak-to-trough decline in portfolio value

**NLP Concepts:**

- **Transformer Architecture**: Neural network design using attention mechanisms for sequence processing
- **Fine-tuning**: Process of adapting pre-trained models to specific domains or tasks
- **F1 Score**: Harmonic mean of precision and recall, useful for imbalanced datasets
- **Sentiment Classification**: Task of categorizing text into emotional or opinion-based categories

## 10. Relevance Assessment

### Direct Relevance to Your Research Interests:

**Sentiment Analysis in Financial Markets:**

- **Highly Relevant**: Provides cutting-edge methodology for financial sentiment analysis with demonstrated trading performance
- **Methodological Transfer**: QLoRA fine-tuning approach directly applicable to stock market sentiment analysis
- **Performance Benchmarking**: Established comparison framework against traditional methods (VADER, dictionary-based)

**Social Media Data Analysis:**

- **Moderate Relevance**: While focused on professional news sources, methodology adaptable to social media sentiment
- **Data Processing Pipeline**: Filtering, preprocessing, and quality control methods transferable to social media data
- **Multi-source Integration**: Framework for combining different data sources applicable to multiple social media platforms

**Persian Language Processing:**

- **Framework Relevance**: Domain-specific fine-tuning methodology adaptable to Persian financial texts
- **Limited Direct Application**: Study focuses on English language, but principles transferable
- **Multilingual Potential**: Llama 3.1's multilingual capabilities (30+ languages) may include Persian support

**Multilingual NLP:**

- **High Relevance**: Demonstrates effectiveness of multilingual base models (Llama 3.1) for specialized domains
- **Fine-tuning Strategy**: Methodology for adapting multilingual models to specific linguistic and domain contexts
- **Cross-lingual Transfer**: Insights into how domain adaptation works across language barriers

**Multi-source Data Combination:**

- **Highly Relevant**: Study integrates three different news sources (Investing.com, DailyFX, FXStreet) with distinct characteristics
- **Weighting Strategies**: Demonstrates how different sources can be weighted based on performance and reliability
- **Source-specific Performance**: Shows that optimal strategies may vary by data source, relevant for multi-platform social media analysis

**Building Financial Indices:**

- **Highly Relevant**: Sentiment scoring methodology directly applicable to creating sentiment-based financial indices
- **Aggregation Techniques**: Daily sentiment scoring using log-difference of positive/negative signals
- **Temporal Dynamics**: Framework for incorporating both historical and forward-looking sentiment

**Transformer Model Fine-tuning:**

- **Extremely Relevant**: Detailed implementation of QLoRA fine-tuning for financial domain
- **Resource Efficiency**: Demonstrates how to fine-tune large models with limited computational resources
- **Domain Adaptation**: Specific techniques for adapting general models to specialized financial language

**Stock Valuation/Price Prediction:**

- **Moderate to High Relevance**: Trading strategy implementation provides framework for price movement prediction
- **Return Prediction**: Uses sentiment to predict currency movements, transferable to stock price prediction
- **Risk-adjusted Performance**: Evaluation methodology applicable to stock trading strategies

**Backtesting Methodologies:**

- **Highly Relevant**: Comprehensive backtesting framework with proper temporal separation
- **Performance Metrics**: Standard financial metrics (Sharpe ratio, maximum drawdown, annualized returns)
- **Multiple Testing Corrections**: Addresses statistical significance testing with appropriate corrections

**Behavioral Finance/Investor Psychology:**

- **Moderate Relevance**: Analyzes how news sentiment relates to market movements, touching on investor behavior
- **Market Psychology**: Examination of how different types of sentiment (past vs. future) affect trading decisions
- **Limited Depth**: Focus is more on technical implementation than psychological mechanisms

**Data Preprocessing for Social Media:**

- **High Relevance**: Robust preprocessing pipeline including duplicate detection, length filtering, quality control
- **Noise Handling**: Techniques for dealing with inconsistent data quality across sources
- **Scalability**: Methods for processing large volumes of text data efficiently

**Financial Vocabulary Development:**

- **Moderate Relevance**: Incorporates currency synonyms and financial jargon recognition
- **Domain-specific Terms**: Framework for handling specialized financial terminology
- **Limited Scope**: Focused on FX rather than general financial vocabulary

## 11. Citation-Worthy Information

### Key Statistics:

- "FX market daily trading volume exceeding 7 trillion USD" (BIS, 2022)
- Fine-tuned Llama achieved 60% accuracy vs. 50% for FinBERT on past sentiment classification
- 3.29% annualized return with 0.42 Sharpe ratio for DailyFX trading strategy
- Error rate of only 2.7% in human-labeled dataset validation
- Dataset comprises 251,845 articles across three major FX platforms

### Important Methodological Claims:

- "QLoRA enables substantial memory and computational savings without compromising the model's ability to learn task-specific features"
- "The fine-tuned LLMs achieve high classification accuracy while maintaining computational efficiency during training"
- "Distant labelling links sentiment to observed returns around the publication dates of news articles, enabling efficient and scalable dataset creation"

### Performance Benchmarks:

- Traditional methods (VADER, LM-dictionary) rebalance daily (252 times/year) vs. Llama models (~232 times/year)
- "Fine-tuned Llama model is the only one that consistently maintains a positive return throughout the sample period"
- EUR/JPY strategy achieved "more than 10% cumulative returns for DailyFX and nearly 20% for Investing.com"

### Dataset Information:

- **Investing.com**: 77,789 articles, average 394 words per article, 17 articles per day average
- **DailyFX**: 45,593 articles, average 403 words per article, 15 articles per day average
- **FXStreet**: 128,463 articles, average 374 words per article, 114 articles per day average

### Comparative Results:

- "Fine-tuned LLMs outperform traditional lexicon-based methods such as VADER and financial models such as FinBERT"
- "The distinct classification between past and future sentiment enhances the model's ability to capture temporal nuances"
- Performance varies by source: "dictionary-based approaches performing competitively in some cases"

### Technical Specifications:

- Training: 3 epochs (distant labeling), 10 epochs (human labeling)
- LoRA parameters: rank 8, scaling factor 16, dropout 0.1
- Model size: 8 billion parameters with multilingual support for 30+ languages

## 12. Critical Analysis

### Strengths:

**Methodological Rigor:**

- Comprehensive evaluation framework with multiple baselines and metrics
- Proper temporal separation between training and testing data
- Rigorous human annotation process with quality control measures
- Statistical significance testing with appropriate multiple comparison corrections

**Practical Relevance:**

- Demonstrates real-world applicability through profitable trading strategies
- Addresses genuine industry need for FX-specific sentiment analysis
- Provides open-source alternative to proprietary solutions

**Technical Innovation:**

- Novel application of state-of-the-art LLMs to specialized financial domain
- Creative combination of human and distant labeling to balance quality and scale
- Effective use of parameter-efficient fine-tuning (QLoRA) for resource optimization

**Comprehensive Scope:**

- Multi-source data integration provides robustness
- Covers extended time periods for reliable evaluation
- Addresses both classification accuracy and practical trading performance

### Potential Weaknesses:

**Limited Generalizability:**

- Focus on G10 currencies may not extend to emerging market currencies
- English-only analysis limits international applicability
- Performance varies significantly across data sources, suggesting method sensitivity

**Dataset Limitations:**

- FXStreet data limited to 2018-2021 period affects temporal coverage
- Declining article volumes in later years for some sources may impact recent performance
- Relatively small human-labeled dataset (1,068 articles) for such a complex domain

**Statistical Concerns:**

- Some reported significant differences become non-significant after multiple testing corrections
- Look-ahead bias concerns, while addressed, cannot be completely eliminated
- Modest sample size starting from 2020 may limit statistical power

**Methodological Questions:**

- "Unchanged" class consistently underperforms across all models, suggesting fundamental classification challenge
- Distant labeling approach assumes news sentiment correlates with subsequent returns, which may not always hold
- Currency-level performance analysis limited by sample size constraints

**Economic Reality:**

- Transaction costs not included in performance evaluation, though rebalancing frequency is reported
- Market impact of trades not considered (relevant for real-world implementation)
- Performance evaluation period includes unique market conditions (COVID-19 era) that may not be representative

### Evidence Quality Assessment:

**Strong Evidence:**

- Consistent outperformance of fine-tuned models across multiple evaluation metrics
- Robust backtesting methodology with proper temporal controls
- Clear performance differences between fine-tuned and untuned models

**Moderate Evidence:**

- Trading strategy profitability varies significantly by data source
- Statistical significance often marginal and sensitive to corrections
- Performance attribution between genuine signal and potential bias remains unclear

**Areas Requiring Caution:**

- Generalizability beyond the specific datasets and time periods studied
- Scalability to higher-frequency trading or larger position sizes
- Robustness across different market regimes and economic conditions

### Overall Assessment:

This research represents a solid contribution to financial NLP with clear practical applications. The methodology is sound, and the results demonstrate meaningful improvements over existing approaches. However, the findings should be interpreted within the context of the specific datasets and evaluation periods. The work provides a valuable framework for domain-specific LLM applications in finance, though further validation across different markets, languages, and time periods would strengthen the conclusions.
