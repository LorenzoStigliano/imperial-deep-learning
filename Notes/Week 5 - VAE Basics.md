- Goal: $p_{\theta}(x) = p_{data}(x)$
- Fitting the model to the data by divergence minimisation:
- $\theta^* = argmin D[p_{data}(x)|| p_{\theta}(x)]$![[Screenshot 2023-02-06 at 14.42.02.png]]

- Example of a valid divergence: 
	- Kullback-Leibler (KL) divergence $KL[p_{data}(x)|| p_{\theta}(x)] = E_{p(x)}[log\frac{p(x)}{q(x)}]$![[Screenshot 2023-02-06 at 14.43.49.png]]
	- Fitting the model by minimising KL:![[Screenshot 2023-02-06 at 14.45.09.png]]
	- In practice: ![[Screenshot 2023-02-06 at 14.46.05.png]]

Maximum Likelihood estimation
- MLE for training latent variable models (LVM)
- $p(z)= N(z;0,I)$ and $p_{\theta}(x|z)= N(x; G_{\theta}(z), \sigma^2 I)$
- We want to evaluate ![[Screenshot 2023-02-06 at 14.56.23.png]]
- Notice that ![[Screenshot 2023-02-06 at 14.56.43.png]]
- So the marginal distribution $p_{\theta}(x)$ is intractable so the MLE objective is intractable

Variational Auto-Encoders
- MLE for latent variable model training is intractable 
- Optimising a variational lower-bound instead
![[Screenshot 2023-02-06 at 14.59.46.png]]
- In step two we multiply by an arbitrary distribution.
- Alternative derivation:![[Screenshot 2023-02-06 at 15.01.46.png]]
- We can see that the difference between the marginal log likelihood and the lower bound is the KL divergence
- It some cases it helps but in other times it does not 
- So we aim to: 
	- ![[Screenshot 2023-02-06 at 15.03.31.png]]

Putting it all together:
![[Screenshot 2023-02-06 at 15.08.21.png]]
Ingredients of training VAEs:
![[Screenshot 2023-02-06 at 15.08.39.png]]

### Designing the $q$ distribution
![[Screenshot 2023-02-06 at 15.10.42.png]]

Reparameterisation trick ![[Screenshot 2023-02-06 at 15.12.13.png]]
- It requires computing the expectation under the $q$ distribution
- How do we learn $\phi$? since the right hand side depends on it 
- ![[Screenshot 2023-02-06 at 15.15.52.png]]
- Enables end to end differentiation together

### Combining everything together
![[Screenshot 2023-02-06 at 15.17.11.png]]
- Once trained, sample new images form the model as so:
- ![[Screenshot 2023-02-06 at 15.19.14.png]]
- QUESTIONS:
	- *$z$ is sampled from $p(z)$ so we know this distribution before hand?* 
		- Yes we know this distribution $p(z)= N(z;0,I)$
	- Why is the Loss the expected value over the data?
- We first sample from distribution $z$ and then pass it through the decoder![[Screenshot 2023-02-06 at 15.25.22.png]]
- Notice that $\hat{x}_m$ depends on $\theta$ thus that is what is being differentiated
