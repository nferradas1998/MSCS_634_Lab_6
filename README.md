# MSCS_634_Lab_6

## Overview
This lab explores association rule mining techniques using the Apriori and FP-Growth algorithms. The goal was to analyze transactional retail data, identify frequent itemsets, and generate meaningful association rules. The lab also included several visualizations (barplots, heatmaps, scatter plots) to help interpret the patterns found in the dataset.

The dataset used for this lab was the Online Retail dataset, which contains transaction-level purchase data from a UK-based retailer. After cleaning the data and converting it into a basket format, both Apriori and FP-Growth were applied to extract frequent itemsets.

## Key Insights
### Frequent Itemsets
- The dataset contained a very large number of unique items, which made frequent itemset mining computationally heavy.
- To make Apriori feasible, the itemspace was reduced.
- After reduction, Apriori still produced mostly single-item itemsets, while FP-Growth was able to identify a richer set of item combinations due to its more efficient FP-tree structure.

### Association Rules
- FP-Growth successfully generated several association rules with strong support, confidence, and lift.
- These rules revealed meaningful product relationships, such as items that tend to be purchased together in the same order.

### Apriori Returned Zero Rules
- Apriori produced 0 association rules, which is expected given the reduced dataset.
- Because Apriori was limited to a smaller set of transactions and items to avoid memory errors, it found only single-item frequent itemsets.
- Since association rules require itemsets of size ≥ 2, Apriori had no valid pairs to generate rules from.
- This behavior highlights the scalability limitations of Apriori and illustrates why FP-Growth is generally preferred for larger retail datasets.

## Challenges
### Memory Errors with Apriori
- The full dataset caused Apriori to exceed system memory (attempting to allocate tens of gigabytes). This required reducing the dataset by:
- Even after reduction, Apriori still struggled to produce multi-item itemsets.

### BOM Encoding Issue
- The dataset contained a UTF-8 BOM, causing the first column name InvoiceNo to appear as ï»¿InvoiceNo. This caused errors during cleaning. The issue was fixed by stripping the BOM from the column names.

### Sparse Transactions
- Retail transaction data tends to be highly sparse, meaning most items do not frequently co-occur. This makes generating multi-item frequent itemsets more difficult, especially when item-level filtering is applied.

## Conclusion
- FP-Growth performed significantly better than Apriori in terms of both runtime and the richness of itemsets discovered.
- Apriori’s inability to generate rules in this lab was not only expected but also provided a useful demonstration of the algorithm’s limitations.
- The overall lab helped illustrate how association rule mining works in practice, why algorithm choice matters for large datasets, and how preprocessing decisions impact the results.
