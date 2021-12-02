---
title: Machine Learning
summary: An advanced introduction.
date: 2021-03-25
math: true
tags:
- Other
diagram: true
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

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
  - It's inevitable, Mr. Anderson. (when you have latent variable in you model.)
- 


### Example on the Multinominal Model (Topic Modeling)

## Interpretable Machine Learning: some fun fact.
> The opinions are from Ms Cynthia Rudin. 
- You can generally find an interpretable ML model that is as accurate as any black box model. 
- It has become clear that people don't know this. 
- DON'T USE BLACK BOX MODEL FOR HIGH-STAKE APPLICATIONS.
- There is no scientific evidence for a tradeoff between interpretability and accuracy.





### References
[1] [Latent Variables & Expectation Maximization Algorithm](https://towardsdatascience.com/latent-variables-expectation-maximization-algorithm-fb15c4e0f32c)

