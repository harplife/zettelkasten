---
aliases: [Verstack]
tags: [python, library, what-is]
status: ongoing
edited: 2021-10-21
---

# Verstack
Verstack is a Python library(package) filled with tools to make a Data Scientist's work efficient.

Its main tools are:
- __NaNImputer__ : impute all missing values in a pandas dataframe
- __Multicore__ : execute any function in concurrency using all the available CPU cores
- __ThreshTuner__ : tune threshold for binary classification predictions
- __stratified_continuous_split__ : create train/test splits stratified on the continuous variable
- __timer__ : convenient timer decorator to quickly measure and display time of any function execution

## Install
```python
pip install verstack
```

## My Thoughts
It's not a popular package and it's really not that great.
I've tried messing around with it for a bit with multicore, and I already hit a snag.
Refer to [[how_to_parallelize_with_verstack|How to Parallelize with Verstack]].

## References
- [Official Documentation](https://verstack.readthedocs.io/)