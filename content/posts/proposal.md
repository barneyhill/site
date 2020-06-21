---
title: "My Google Summer of Code Proposal"
date: 2020-03-26
draft: true
---

# Implementing polynomial regression trees in Effective Quadratures
## Summary
Effective Quadratures is an open source library used to generate polynomials for parametric computational studies. Among the applications of the library is the ability to perform polynomial regression on a dataset. I propose an implementation of a polynomial regression tree class in Effective Quadratures which will offer greater accuracy when extrapolating compared to the current polynomial regression class.


By implementing a polynomial regression tree class I believe that I will help demonstrate some of the benefits of using orthogonal polynomials in the context of model trees. For example users of the library will be able to calculate sensitivity indices and moments over subdomains of functions and datasets. This has the benefit of providing more information about the dataset than was previously possible in the library.

  

## Deliverables

Core polynomial regression tree implementation (required)

The bulk of my proposed work will be on creating polytree.py. This will be a new class in Effective Quadrature, below I outline what I consider the essential public methods of this class.

-   fit(): Evaluates the trained network on data provided with the initialisation of the class.
    
-   evaluate_polytree(point): Evaluates the trained model at a given point.
    

I plan to mainly base my core implementation of the tree on [Anson Wong’s model tree class ](https://github.com/ankonzoid/LearningX/blob/master/advanced_ML/model_tree/src/ModelTree.py). I believe this deliverable will be fairly straightforward to implement and will allow a base from which to explore the benefits of using orthogonal polynomial models referenced below.

### Model statistics (optional)

By using a model composed of many orthogonal polynomial functions, moments and sensitivities can be calculated from each individual function. This means that the user will be able to select a subset of the input parameters and be given combined summary statistics from the polynomials. For this I will implement the methods:

-   get_mean_and_variance(lower,upper)
    
-   get_skewness_and_kurtosis(lower,upper)
    
-   get_sobol_indicies(highest_sobol_order_to_compute, lower, upper)
    

All methods will allow the user to specify a range over which the statistics should be calculated.


### Tree splitting using sensitivity obtained from the Sobol indices (optional)

While the core implementation determines the nodes of the tree through exhaustively attempting to minimise loss (mean squared error), I propose an extension that will instead consider feature importance to reduce the search space of parameters to split. It will do this by only splitting parameters with a significant sensitivity as shown from the sobol indices.

### Documentation (required)

I will support all implemented public methods with a description of the function and its parameters in docstrings.
  

### Testing (required)

In order to test any features, test_polytree.py will be created. Using the library unittest, I will ensure that the polynomial regression tree runs on both univariate and multivariate data-sets.

  

### Tutorial (optional)

I hope to be able to create a tutorial that will show a user how to run the model on both univariate and multivariate datasets.

## Schedule of Deliverables

### Preparation:

May 4th - May 31st: Begin reading relevant material and revising the details of deliverables.

### Phase 1 (evaluation deadline: July 3rd)

June 1st - July 3rd: I will work on the core polynomial regression tree implementation, testing will also be done in parallel to development.

### Phase 2 (evaluation deadline: July 31st)

July 4th - July 31st: I will use this month to finish the core implementation and begin work on the model statistics and performing tree splitting using input parameter sensitivities. As with phase 1, testing will also be worked on.

  

### Final phase

August 1st - August 28th: This month will be focused on ensuring what I have created is as accessible as possible. I will create documentation and a tutorial, as well as review and optimise any inefficient code.
