---
title: Machine Learning Notes
date: 2021-03-25
math: true
diagram: true
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

# Introduction
> A learning note.
## Expectation-Maximization Algorithm
- EM Step 
  - E step creates a function for the expectation of the log-likelihood evaluated using the current estimate for the parameters
  - M step computes parameters maximizing the expected log-likelihood found on the E step. These parameter-estimates are then used to determine the distribution of the latent variables in the next E step. 
> The model depends on unobserved *latent variables*. 
### Latent Variables and LVM 
> The primary role of the latent variables is to allow a complicated distribution over the observed variables to be represented in terms of a model constructed from simpler (typically exponential family) conditional distributions.<br>
- If you think of an image (ex. human face) as the observed variable x then, the latent variable z could encode the features of the face (which are not seen during training), like it can encode whether the face is happy or sad, male or female etc.
- Trouble: $log \sum$


### Example on the Multinominal Model (Topic Modeling)





### References
[1] [Latent Variables & Expectation Maximization Algorithm](https://towardsdatascience.com/latent-variables-expectation-maximization-algorithm-fb15c4e0f32c)

