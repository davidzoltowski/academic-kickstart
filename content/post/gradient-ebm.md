---

title: "Gradients of Energy-Based Models"
date: 2020-04-21T13:19:36-07:00
draft: false
featured: true
markup: mmark

---

Consider an energy based model

$$
p(x) = \frac{1}{Z(\theta)} \, e^{-E_\theta(x)}
$$

with normalizing constant $Z(\theta)$. Papers often state that the gradient of $\log p_\theta(x)$ with respect to $\theta$ is

$$
\frac{\partial}{\partial \theta} \log p_\theta(x) = \mathbb{E}_{p_\theta(x)} \left[ \frac{\partial}{\partial \theta} E_\theta(x) \right] - \frac{\partial}{\partial \theta} E_\theta(x). 
$$

But where does this come from? Here we derive it using the log-derivative trick and with one key assumption. We start by writing the gradient

$$
\frac{\partial}{\partial \theta} \log p_\theta(x) = \frac{\partial}{\partial \theta} \left[ -\log Z(\theta) - E_\theta(x) \right] = - \frac{\partial}{\partial \theta} \log Z(\theta) - \frac{\partial}{\partial \theta} E_\theta(x).
$$

We have already identified the second term in the gradient. The first term requires some care. We start by using the log-derivative trick

$$
\frac{\partial}{\partial \theta} \log Z(\theta) = \frac{ \frac{\partial}{\partial \theta} Z(\theta)}{Z(\theta)}.
$$

Next, we derive $\frac{\partial}{\partial \theta} Z(\theta)$ with the key assumption that we can *interchange integration and differentiation* 

$$
\frac{\partial}{\partial \theta} Z(\theta) = \frac{\partial}{\partial \theta} \int e^{-E_\theta(x)} \mathrm{d}x = \int \frac{\partial}{\partial \theta} e^{-E_\theta(x)} \mathrm{d}x.
$$ 

Putting together the pieces gives us

\begin{align}
\frac{\partial}{\partial \theta} \log Z(\theta)  &= \frac{1}{Z(\theta)} \int \frac{\partial}{\partial \theta} e^{-E_\theta(x)} \mathrm{d}x \\ 
 & = \int  \frac{1}{Z(\theta)} \frac{\partial}{\partial \theta} e^{-E_\theta(x)} \mathrm{d}x \\
 & = - \int  \frac{1}{Z(\theta)} e^{-E_\theta(x)}  \frac{\partial}{\partial \theta} E_\theta(x)  \mathrm{d}x \\
 & = - \mathbb{E}_{p_\theta(x)} \left[  \frac{\partial}{\partial \theta} E_\theta(x) \right].
\end{align}

We are done! We can plus this into the equation above (keeping track of minus signs) to get

$$
\frac{\partial}{\partial \theta} \log p_\theta(x) = \mathbb{E}_{p_\theta(x)}\left[\frac{\partial}{\partial \theta} E\_\theta(x) \right]- \frac{\partial}{\partial \theta} E_\theta(x).
$$
