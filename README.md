# Student’s Pooled t-test vs. Welch’s t-test

## Introduction

This repository hosts code and documentation for comparing the power of two popular statistical tests: Student’s pooled t-test and Welch’s t-test. Monte Carlo simulations are employed to estimate the power of these tests across various scenarios, with a focus on different sample sizes and population standard deviations. Both tests are implemented in R using the `t.test()` function, with the `var.equal` argument set to `TRUE` for the pooled t-test.

## Background

### Student’s Pooled t-test:
- Assumes equal variances between the groups being compared.
- Combines variances of the two groups into a single pooled estimate, assuming they represent the overall population variance.
- Suitable when there is confidence in the equality of variances between groups.

### Welch’s t-test:
- Does not assume equal variances between groups.
- Provides a more robust alternative when equal variances assumption is violated or uncertain.
- Adjusts for unequal variances, offering more accurate results when sample sizes and variances between groups differ significantly.

## Objective

The objective is to identify scenarios where one test demonstrates greater power than the other. Power curves are generated to visualize the relationship between statistical power and mean difference for both tests across various sample sizes and standard deviations.

## Simulations

Monte Carlo simulations are conducted to evaluate the power of each test under different conditions. The simulations vary sample sizes (`n1` and `n2`), population standard deviations (`σ1` and `σ2`), and mean differences between groups.

## Code Overview

- Functions:
  - `pooled_t_test()`: Performs Student’s pooled t-test.
  - `welch_t_test()`: Performs Welch’s t-test.
  - `calculate_power()`: Calculates the power of both tests.
- Parameters:
  - `n1_values`, `n2_values`: Varying sample sizes.
  - `sd1_values`, `sd2_values`: Varying population standard deviations.
  - `mean_diff_values`: Varying mean differences between groups.
- Simulations:
  - Nested loops iterate over combinations of sample sizes, standard deviations, and mean differences.
  - Power calculations are performed using Monte Carlo simulations.
  - Results are stored in a data frame and saved to `results.Rdata`.
- Plotting:
  - Power curves are plotted for aggregated data and specific scenarios.
  - Visualizations illustrate the relationship between power, mean difference, and test type.

## Results

### Aggregated Comparison
- Power curves demonstrate the relationship between mean difference and aggregated power for both tests.
- No significant differences observed in power between tests across varying sample sizes or standard deviations.

### Impact of Sample Size
- As sample sizes increase, Welch’s t-test exhibits more consistent power compared to the pooled t-test.

### Effect of Standard Deviation
- Higher discrepancies in standard deviations favor Welch’s t-test, showing higher power in such scenarios.

## Conclusion

The choice between Student’s pooled t-test and Welch’s t-test should consider factors such as sample sizes and standard deviations. Welch’s test generally performs better when there is unequal variance or larger discrepancies in standard deviations between groups. However, both tests provide reliable results under appropriate conditions.
