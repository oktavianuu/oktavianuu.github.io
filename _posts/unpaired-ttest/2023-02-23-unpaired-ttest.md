---
title: Unpaired T-test
date: 2023-02-23 08:36:00 +07:00
tags: [R, python, statistics]
description:
image:
---
Uji t-test dua sampel tidak berpasangan digunakan untuk untuk membandingkan mean dua kelompok berbeda.
<hr>
For example, suppose that we have measured the weight of 100 individuals: 50 women (group A) and 50 men (group B). We want to know if the mean weight of women (mA) is significantly different from that of men (mB).

In this case, we have two unrelated (i.e., independent or unpaired) groups of samples. Therefore, it’s possible to use an independent t-test to evaluate whether the means are different.

Note that, unpaired two-samples t-test can be used only under certain conditions:
- when the two groups of samples (A and B), being compared, are normally distributed. This can be checked using Shapiro-Wilk test.
- and when the variances of the two groups are equal. This can be checked using F-test.

In statistics, we can define the corresponding null hypothesis (H0) as follow:
1. H0:mA=mB
2. H0:mA≤mB
3. H0:mA≥mB

The corresponding alternative hypotheses (Ha) are as follow:
1. Ha:mA≠mB (different)
2. Ha:mA>mB (greater)
3. Ha:mA<mB (less)

Note that:
* Hypotheses 1) are called two-tailed tests
* Hypotheses 2) and 3) are called one-tailed tests

#### Visualize your data and compute unpaired two-samples t-test in R
##### Install ggpubr R package for data visualization
You can draw R base graphs as described at this link: R base graphs. Here, we’ll use the ggpubr R package for an easy ggplot2-based data visualization:
```R
install.packages("ggpubr")
```
##### R function to compute unpaired two-samples t-test
To perform two-samples t-test comparing the means of two independent samples (x & y), the R function t.test() can be used as follow:
```R
t.test(x, y, alternative = "two.sided", var.equal = FALSE)
```
```
x,y: numeric vectors
alternative: the alternative hypothesis. Allowed value is one of “two.sided” (default), “greater” or “less”.
var.equal: a logical variable indicating whether to treat the two variances as being equal. If TRUE then the pooled variance is used to estimate the variance otherwise the Welch test is used.
```
##### Import your data into R
1. Prepare your data as specified here: Best practices for preparing your data set for R
2. Save your data in an external .txt tab or .csv files
3. Import your data into R as follow:
```R
# If .txt tab file, use this
my_data <- read.delim(file.choose())
# Or, if .csv file, use this
my_data <- read.csv(file.choose())
# Or, if .xlsx file, use this
my_data <- read.excel(file.choose())
```