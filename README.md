
### Questions

### Objectives
YWBAT 
* explain how A/B testing is used in industry
* write down flow chart for choosing proper test

### Outline


```python
import pandas as pd
import numpy as np

import scipy.stats as scs

import matplotlib.pyplot as plt
```

## Pablo's experience
* Causal Inference (mentioned w/ regards to hypothesis testing)
* Used in E-Commerce
* Experiments

* ML != Causal Inference

## Scenario:

Facebook is testing 2 algorithms for generating your 'top' newsfeed. 

How do we set up this test?
* Need a control vs test group
* What are we measuring? Define metrics to measure that Facebook equates to user engagement.
    * Number of reactions to posts ('likes', emojis, etc) that are clicked
* Algorithm A - currently in production
* Algorithm B - New Algorithm to attempt and increase user engagement
    
**What does A/B testing do:**
* Run both algorithms over set sample sizes
    * Groups must be large, large sizes handle normality assumption by CLT 
    * GroupA and GroupB - similar sizes - can't change
    * Groups should be properly randomized
    * Collect data and measure post reactions
* Choose some alpha value 
* How long are we doing this for? 
    * 1 month
    * 2e6 samples in each group
* Run Hypothesis Testing to compare Algorithm A and B's effect on engagement
* Come to a conclusion
* Draw up some action plans
* Implement a new algorithm

**What ML would do (Multi-Arm Bandit):**
* Run both algorithms over set sample sizes
    * Group must be large, large sizes handle normality assumption by CLT 
    * Group should be properly randomized
    * Collect data and measure post reactions
    * Half of your group gets Alg A the other half Alg B
    * Each user is tracked
* Choose a probablity distribution (beta distribution) that a user gets fed A or B.
    * The probablity of choosing one algorithm would then increase/decrease based on how the user engaged with the newsfeed
* Exploitation vs Exploration
    * Why do we have this?
        * Virality could mess this up
        * Seasonality could also be an effect
    * Leave room for a comeback story
        * Choose some function to determine what to serve users
            * Exploiting
                * always serves highest probablity of beta distribution
            * Exploration
                * completely random
            * balance
                * serve high probablity, but also randomly serve

### A/B Testing Workflow
* Design your experiment    
* Run your experiment
* If 1 group
    * 1 sample ttest against some mu
        * Assumptions
        * Population is normally distributed
    * compare pvalue to alpha and reject or fail to reject null hypothesis
* If 2 groups
    * 2 sample ttests
        * Welch's TTest
            * Assumptions
            * populations have unequal variances
            * populations are normally distributed
        * Student TTest
            * Assumptions
            * populations have equal variances
            * populations are normally distributed
            * populations are of equal size
* If 2+ Groups
    * ANOVA test
        * Assumptions
    * Pairwise comparisons
        * Tukey Test
            * Assumptions


```python
# 1 sample
# scs.ttest_1samp

# 2 sample
# scs.ttest_ind

# anova 
```

### Assessment
