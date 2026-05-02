# Alluder-Reaseach-Data
Documentation and representation of research data for Alluder

Alluder Experiment Results

Overview

This section presents performance benchmarking data for the Alluder system. Alluder is a computational dramaturgical assistant designed to analyze dramatic text using natural language processing (NLP).

The experiments measure how input text size affects system performance. The is a focus on runtime behavior, scalability, and the impact of optimization techniques such as caching. The goal is to understand how efficiently the system processes text and where performance bottlenecks occur.

Experiment Design

Objective

Measure how input size (text length) affects:

Total system runtime
Time spent in different processing stages
Performance before and after optimization
Scalability of the system
Test Setup

Three test cases were created with increasing input sizes:

Test	Input Size	Description
Test 1	Short (~1–2 sentences)	Minimal input
Test 2	Medium (~2 paragraphs)	Moderate input
Test 3	Long (~2 pages of text)	Large input

Each test was executed multiple times to ensure consistency and reduce the effect of variability.

Data Collection

System Flow

1. Input Stage
User provides a segment of dramatic text
2. Processing Stage
spaCy performs tokenization and linguistic analysis
Entity detection identifies names, locations, and other elements
Pattern detection identifies structured features (dates, abbreviations)
3. Enrichment Stage
External APIs (e.g., Wikipedia/Wikidata) are used to retrieve contextual information
4. Output Stage
Results are formatted and returned to the user

Metrics Recorded
Total runtime (seconds)
Runtime before optimization
Runtime after optimization
Relative performance improvement
Observed bottlenecks

Key Findings

Lag Trends
1. Runtime increases with input size
Short inputs: ~14 seconds
Medium inputs: ~22 seconds
Long inputs: ~117 seconds
2. Post-optimization runtime improved
Improvements ranged from ~5% to ~27%
Greatest improvement observed for large inputs

Performance Characteristics
1. Internal NLP Processing is Efficient
spaCy processing and detection steps contribute minimally to runtime
2. Entity Enrichment is the Primary Bottleneck
External API calls dominate execution time (~95%)
3. Caching Improves Performance
Reduces redundant API calls
Most effective for longer inputs with repeated entities
4. Scalability is Near-Linear Internally
System scales predictably with input size
External dependencies introduce variability

How to Interpret Results

Understanding Performance
Total Runtime reflects overall system efficiency
Optimization Improvements show effectiveness of system design changes
Bottleneck Identification highlights areas for future improvement

Key Insight

While the system scales efficiently at the algorithmic level, overall performance is primarily influenced by external API latency rather than internal computation.

Methodology Notes

Test Constraints
Inputs were manually selected to represent realistic dramaturgical use cases
External API behavior was not controlled, introducing some variability
Tests were run sequentially under consistent conditions

Why These Metrics Matter
1. Runtime → Determines usability of the system
2. Scalability → Determines feasibility for larger texts
3. Optimization Impact → Demonstrates effectiveness of engineering decisions
4. Bottleneck Analysis → Guides future system improvements

Limitations of Experimental Design
No formal accuracy metrics (precision/recall) were included
Results focus on performance, not correctness
External APIs introduce non-deterministic variability

Files / Artifacts 
Runtime tables (Chapter 4)
Optimization comparison table
Pipeline diagram
Runtime graph

Next Steps / Recommendations
1. Accuracy Evaluation
Introduce precision and recall metrics using annotated datasets
2. API Optimization
Reduce dependency on external APIs through caching or local storage
3. Parallel Processing
Explore concurrent API calls to reduce latency
4. Scalability Testing
Test larger inputs and varied entity distributions
5. User Evaluation
Conduct usability testing with dramaturgs
