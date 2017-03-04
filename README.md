Python Implementation of Apriori Algorithm
==========================================

[![Build Status](https://travis-ci.org/asaini/Apriori.svg?branch=master)](https://travis-ci.org/asaini/Apriori)

The code attempts to implement the following paper:

> *Agrawal, Rakesh, and Ramakrishnan Srikant. "Fast algorithms for mining association rules." Proc. 20th int. conf. very large data bases, VLDB. Vol. 1215. 1994.*

List of files
-------------
1. apriori.py
2. apriori-improved.py
3. tesco.csv //test data
4. README(this file)
5. images
6. research papers on improved algo

Improved Apriori Algorithm
-------------

### Idea for optimized execution for larger data sets: 

Scan all transactions to generate L1 table L1(items, their support, their transaction IDs) >> Construct Ck by self-join >> Use L1 to identify the target transactions for Ck >> Scan the target transactions to generate Ck

```
The improvement of algorithm can be described as follows:  
//Generate items, items support, their transaction ID (1) L1 = find_frequent_1_itemsets (T);  
(2) For(k=2;Lk-1 ≠Φ;k++){  
//Generate the Ck from the LK-1  
(3) Ck = candidates generated from Lk-1;  
//get the item Iw with minimum support in Ck using L1,(1≤w≤k). (4) x = Get _item_min_sup(Ck, L1);  
// get the target transaction IDs that contain item x.  
(5) Tgt = get_Transaction_ID(x);  
(6) For each transaction t in Tgt Do  
(7) Increment the count of all items in Ck that are found in Tgt; (8) Lk= items in Ck ≥ min_support;  
(9) End;  
(10) }
```

### Analysis of Improvement:

The first experiment compares the time consumed of original Apriori, and our improved algorithm by applying the five groups of transactions in the implementation. The result is shown in Figure 2.  

![alt tag](/images/graph1.png?raw=true "Optional Title")  

The second experiment compares the time consumed of original Apriori, and our proposed algorithm by applying the one group of transactions through various values for minimum support in the implementation. The result is shown in Figure 3.  

  ![alt tag](/images/graph2.png?raw=true "Optional Title")  

Usage
-----
To run the program with dataset provided and default values for *minSupport* = 0.15 and *minConfidence* = 0.6

    python apriori.py -f INTEGRATED-DATASET.csv
    python apriori-improved.py -f INTEGRATED-DATASET.csv

To run program with dataset  

    python apriori.py -f INTEGRATED-DATASET.csv -s 0.17 -c 0.68
    python apriori-improved.py -f INTEGRATED-DATASET.csv -s 0.17 -c 0.68

Best results are obtained for the following values of support and confidence:  

Support     : Between 0.1 and 0.2  

Confidence  : Between 0.5 and 0.7

Credits
-------
> *-github/asaini  
-Darshan M. Tank : Improved Apriori Algorithm for Mining Association Rules  
-Mohammed Al-Maolegi1, Bassam Arkok2 Computer Science, Jordan University of Science and Technology, Irbid, Jordan: AN IMPROVED APRIORI ALGORITHM FOR ASSOCIATION RULES*


-------
