# Efficient Frontiers

This GitHub repository contains all the work related to my study of efficient frontiers and mean-variance optimisation. My notes are heavily inspired by research and lectures whilst studying at Warwick.

## Introduction

Mean-variance analysis is the problem of finding a portfolio that maximises expected returns for a given level of risk. The variance of an assets return is used as a measure of risk. This theory suggests that an investor can reduce portfolio risk by diversifying their portfolio of assets. The mean-variance framework was first introduced by Markowitz.

## Problem Formulation

We explicitly solve the mean-variance optimisation problems for risk-only portfolios and general portfolios. For general portfolios these can be formulated as follows.
- Given an initial wealth $x_0>0$ and a minimal desired expected return $\mu_{\text{min}}>0$, minimise the variance of the return $\sigma_{\bar{\vartheta}}^2$ among all $x_0$-feasible portfolios $\bar{\vartheta}\in\mathbb{R}^{1+d}$ that satisfy $\mu_{\bar{\vartheta}}\geq\mu_{\text{min}}$.
- Given an initial wealth $x_0>0$ and a maximal desired variance of the return $\sigma_{\text{max}}^2\geq0$, maximise the expected return $\mu_{\bar{\vartheta}}$ among all $x_0$-feasible portfolios $\bar{\vartheta}\in\mathbb{R}^{1+d}$ that satisfy $\sigma_{\bar{\vartheta}}<\sigma_{\text{max}}^2$.

For risk only-portfolios

- Given an initial wealth $x_0>0$ and a minimal desired expected return $\mu_{\text{min}}>0$, minimise the variance of the return $\sigma_{\vartheta}^2$ among all $x_0$-feasible portfolios $\vartheta\in\mathbb{R}^{d}$ that satisfy $\mu_{\vartheta}\geq\mu_{\text{min}}$.
- Given an initial wealth $x_0>0$ and a maximal desired variance of the return $\sigma_{\text{max}}^2\geq0$, maximise the expected return $\mu_{\vartheta}$ among all $x_0$-feasible portfolios $\vartheta\in\mathbb{R}^{d}$ that satisfy $\sigma_{\vartheta}<\sigma_{\text{max}}^2$.

An implementation solving the risk-only problems can be seen in the document `23072024_Efficient_Frontier.ipynb`. One of the other key problems we look at is the mutual fund theorem. This theorem states that any portfolio on the efficient frontier can be generated by holding a combination of any two given portfolios on the frontier. So even in the absence of a risk-free asset, an investor can achieve any desired efficient portfolio.

## Implementation

We calculate the forward-looking expected returns and covariance of returns using historical data gathered from Yahoo Finance. Given a portfolio, we can then easily compute it's return and variance. We solve the constraint problems by using `scipy.optimize.minimize` with the method `'SLSQP'` (see https://docs.scipy.org/doc/scipy/reference/optimize.minimize-slsqp.html#optimize-minimize-slsqp for more details).

## Results

Please view `Efficient_Frontier_Curve.png` to see the constructed efficient frontier and read `Efficient_Frontier_Project.pdf` if you are interested in the theory behind efficient frontiers.
