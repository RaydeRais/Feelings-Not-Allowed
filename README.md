# Feelings-Not-Allowed
XHS Sensitive Keywords &amp; Anomalous Products Detection and Topic Clustering
XHS Sensitive Keywords & Anomalous Products Detection and Topic Clustering

This project is a Python-based workflow designed to automatically identify sensitive keywords, anomalous products, and emerging trends on Xiaohongshu (XHS) using advanced NLP techniques and topic clustering. The goal is to support risk monitoring and compliance analysis, especially for trade and cross-border e-commerce, by surfacing hidden “code words” and outlier topics in user-generated content.

Background

On platforms like Xiaohongshu, users often invent creative slang or code words to avoid platform moderation. This codebase aims to automate the discovery of these sensitive product keywords, leveraging topic clustering and semantic outlier detection, with manual review as a final filter. The outputs can then be used for further quantitative analysis and early warning in internal systems.

Workflow Overview

Data Cleaning

clean_data_true.py
Initial cleaning and deduplication of raw scraped data.
Tip: Remove duplicate content fields first to avoid clustering errors later!

Data Merging

merge_true.py
Merge multiple batches of scraped data and standardize fields.

Second Round of Cleaning

clean_2_true.py
Further filtering to remove noisy or irrelevant samples.

Topic Clustering

bert_2_true.py
Perform topic clustering using BERTopic to extract meaningful topic tags.

Blacklist Extraction

blacklist_true.py
Generate a blacklist of risky keywords based on clustering results and domain knowledge.

Blacklist Deduplication

去重字典.py
Remove duplicates from the manually curated blacklist.

Sensitive Product Extraction

key_12_pro_true.py
Extract candidate sensitive product keywords not yet covered by the blacklist.

Quantitative Risk Analysis

risk_2_true.py
Combine outputs such as New Words, Multi-topic Items, and Semantic Outliers to generate a final risk report.

Output Structure

New Words Ranking: Emerging keywords, sorted by their first appearance (highlighting those from the past 7 days).

Multi-topic Ranking: Product keywords appearing in 2 or more topics, sorted by the number of associated topics.

Semantic Outlier Ranking: Product keywords that are the least similar to the core terms in their topic (potentially hidden risks).

For each candidate goods (keyword), you get:

tags: Labels (e.g., New Word / Multi-topic / Outlier)

topic_num: Topic cluster index (from BERTopic)

outlier_score: Outlier score—the higher, the more suspicious

freq: Total occurrences

example: Highlighted context snippets from original posts

Technical Notes & Tips

LAC tokenizer requires Python 3.7 (path: C:\Users\gaoxu\Python37\python.exe);
all other scripts use Python 3.12.

When scraping Xiaohongshu, use multiple accounts and rotate batches. If one batch is flagged, all addresses in that batch may be invalidated.

Global VPN + foreign mobile numbers are less likely to trigger XHS anti-crawling mechanisms.

Chinese expressions are highly creative—manual review is always recommended for “hook words” or anomalies.

Real-World Application Example

If the model surfaces a strange word (e.g., “谷子”), you can search it in XHS posts to interpret its meaning, and then use it as a clue for further quantitative analysis in internal customs data.

About the Author

This project is maintained by Ray de Rais.
If you find it helpful, feel free to reach out for collaboration or discussions!

If you want to further personalize the "About the Author" section (for example, add your email or GitHub username, or a warm closing), let me know—I can tailor it to your style! 😊

How to actually obtain large-scale XHS crawled data? Or, how to access internal (customs) data for cross-referencing?
Well… that’s a whole different story. 😉
