# Week 4 Association rules

## Market basket analysis
- beer => diapers(0.05, 0.30)
  - 5% - support of the rule
  - 30% - confidence of the rule
- applications
  - retail: what sells with what
  - marketing: population segments, recommendations
  - finance: investment
  - biology
- definitions
  - I = {i1,i2,...,in} a set of literals, **items**
  - *Transaction* T: a set of items such that T subset of I
  - *Dataset* D: a set of transactions
  - **Association rule**: X => Y, where X, Y belongs to I
  - X => Y has *support* s in transaction set D if s% of transactions in D contain X U Y
  - X => Y has *confidence* c in transaction set D if c% of transactions in D that contain X also contain Y
- Association rule mining problem
  - definition
    - given a set of transactions T, find all the rules having support >= minsup and confidence >= minconf, where minsup and minconf are the corresponding support and confidence thresholds
  - brute force
    - n items
      - R = 3^n + 2^(n+1) + 1 rules
  - two step approach
    1. frequent itemset generation
      - generate all item sets whose support >= minsup
      - 2^n - 1 possible subsets
      - compare: O(NMw)
      - reduce complexity
        - Apriori Algorithm
        - FP growth
    2. rule generation

## Apriori algorithm
- n items -> 2^n - 1 subsets
  - if A is infrequent, assume all sets that contain A are infrequent -> no need to consider A
- **Apriori Principle**
  - *if an itemset is frequent, then all of its subsets must also be frequent*
- rule generation
  - subsets of an itemset
  - {A,B} => {E}, conf = support for {A,B,E} / support for {A,B}

## FP Growth
- Apriori
  - reduce the number of candidate itemsets
- FP growth
  - reduce the number of comparisons by using advanced data structures to store candidate itemsets or to compress dataset
- FP tree
