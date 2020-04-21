---
title: "Gradients of Energy-Based Models"
date: 2020-04-21T13:19:36-07:00
draft: false
featured: true

---

Consider an energy based model

$$
p(x) = \frac{1}{Z(\theta)} \, e^{-E_\theta(x)}
$$

with normalizing constant $Z(\theta)$. Papers often state that the gradient of $\log p_\theta(x)$ with respect to $\theta$ is 

First. Does $\mathbb{E}$ work?

Second, does $\int$ work?

$$
\frac{\partial}{\partial \theta} \log p\_\theta(x) = \mathbb{E}\_{p_\theta(x)}
$$

