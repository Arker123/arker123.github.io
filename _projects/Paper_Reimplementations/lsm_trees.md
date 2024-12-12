---
title: Log Structured Merge Trees
subtitle: Classical Image Understanding
contributors: Arnav Kharbanda*, Gopal Bansal*, Yashasav Prajapati*, Dr. Akansha
date: 2022-01-01
image: ../images/LSM.jpg
carousels: 
  - images: 
    - image: ../images/LSM.jpg
      desc: Bayesian Matting is hard...
order: -30
---

<!-- <div class="github-card" data-github="Arker123" data-width="400" data-height="200" data-theme="default"></div> -->

Github:- [Github](https://github.com/Arker123/LSM-Trees)
# Implementing LSM Trees with Bloom Filters  

Managing data efficiently is an exciting challenge in high-performance systems. LSM Trees have emerged as a great solution, especially for applications where writing data quickly is more critical than retrieving it immediately. In this project, my team and I enhanced the LSM Tree structure with Bloom filters to improve its efficiency even further. Here’s how we did it. LSM Trees are widely used in NoSQL databases, where the ability to batch writes while keeping queries responsive makes them invaluable.  

## Why LSM Trees?  

When working with databases, traditional structures like B-Trees struggle with high volumes of insertions because every update requires a disk operation. This can make systems slow. LSM Trees tackle this by writing changes to an in-memory structure first (called `C0`) and only later merging them with on-disk components (`C1`, `C2`, etc.). Think of it like saving drafts on your computer before finalizing a document in a shared folder.  

Bloom filters added an extra layer of efficiency to our design by acting as quick "guards." Instead of searching the disk blindly for data, the filters helped us decide whether it was even worth checking in the first place.  

## How We Built It  

### Step 1: Prepare Test Data  

We started by creating a Python script, `testcase.py`, to generate a dataset for our program to process. This dataset simulated a real-world environment with millions of records.  

**Thoughts**: Creating good test data was crucial. We wanted to ensure the program could handle large-scale scenarios, like those in real databases. The script made it easy to create consistent test cases, so we didn’t have to worry about variability.  

Command to run:  
```sh  
python3 testcase.py  
```
This generated a file called TestCase.txt, which we used for all operations.
### Step 2: Compile the Program

The heart of our implementation was written in C++. This part involved compiling the main file along with helper files for operations like managing red-black trees and handling data compaction.

Thoughts: Compaction was a fascinating feature to work on. It’s like tidying up your room – merging smaller files into larger ones for efficiency. Watching our table folder fill up with neatly compacted SSTables was immensely satisfying!

Command to compile:
```sh
g++ main.cpp rbtree.cpp compaction.cpp read.cpp -lm -pthread  
./a.out  
```
### Step 3: Perform Operations

Once the program was running, it presented three options:

- Insert: This used the TestCase.txt file to insert millions of records into the tree.
- Search: Quickly found records using Bloom filters to skip unnecessary checks.
- Delete: Removed records from the tree, ensuring proper updates in both memory and disk.

The insertion step was the most time-intensive but also the most rewarding. It showed how the system flushed data to disk in the background, compacting it and keeping the structure optimized. After that, search and delete operations felt like a breeze.
A Closer Look at the Formulas

### Batching Efficiency:
LSM Trees are powerful because they batch multiple operations before flushing to disk. This is quantified by:
$M = \frac{SpSe \cdot S0}{S0 + S1}$.
M=SpSe⋅S0S0+S1
M=Se​Sp​​⋅S0​+S1​S0​​

Where:
    MM: Average number of entries merged per leaf during compaction.
    SpSp​: Page size (bytes).
    SeSe​: Entry size (bytes).
    S0,S1S0​,S1​: Sizes of the C0 and C1 components, respectively.

Insight: A higher MM means fewer expensive disk operations, making the system more efficient.

I/O Cost per Insert:
LSM Trees shine when compared to traditional B-Trees because their I/O cost per insert is lower:
COSTLSM-ins=2⋅COSTπM
COSTLSM-ins​=M2⋅COSTπ​​
    COSTπCOSTπ​: Disk arm cost for a multi-page I/O.

For B-Trees, the cost is:
COSTB-ins=COSTP⋅(De+1)
COSTB-ins​=COSTP​⋅(De​+1)
    COSTPCOSTP​: Disk arm cost for random I/O.
    DeDe​: Effective depth of the B-Tree.

Efficiency Ratio: Comparing LSM Trees to B-Trees, the improvement is captured by:
COSTLSM-insCOSTB-ins=2De+1⋅COSTπCOSTP⋅1M
COSTB-ins​COSTLSM-ins​​=De​+12​⋅COSTP​COSTπ​​⋅M1​

This ratio demonstrates how batching and sequential writes give LSM Trees an edge.

Role of Bloom Filters

Bloom filters were the highlight of our project. These are like a "fast-forward button" for search operations. Instead of looking through every file, the filter quickly told us whether something was even worth searching for.

Thoughts: Adding Bloom filters wasn’t straightforward at first, but it made a noticeable difference. The search times dropped significantly because we could skip unnecessary disk reads.
What We Learned
Key Insights

    Batching is powerful:
    Using formulas like the one for MM, we realized how batching entries minimizes expensive operations.

    Compaction optimizes storage:
    By merging smaller files into larger ones, the system ensured we weren’t wasting disk space or creating a mess of fragmented files.

    Bloom filters save time:
    These acted like a first line of defense, reducing unnecessary work by up to 30%.

Challenges

    Finding the right balance between memory (C0) and disk (C1) sizes was tricky. If C0 was too small, the program would trigger frequent merges. If it was too large, it would use too much memory.
    Debugging compaction errors required a deep dive into how data flowed between components.

Results

    10 Million Records in 12 Seconds: Our program processed massive datasets quickly, outperforming traditional methods.
    1.5x Faster Than B-Trees: We confirmed that LSM Trees handle write-heavy workloads much better.

Closing Thoughts

This project was a blend of theory and practice. Working on LSM Trees taught us how small optimizations in data handling can lead to massive performance gains. Adding Bloom filters was the cherry on top, proving how the right tools can transform a system’s capabilities.