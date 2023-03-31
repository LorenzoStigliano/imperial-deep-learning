- The main idea, we have drawn samples from the data distribution 
- We can also generate the images by first sampling z and then creating a generator 
- The generator and discriminator networks are against one another generator tries to generate better images and the discriminator cannot distinguish between real and fake![[Screenshot 2023-02-06 at 18.17.34.png]]
- Discriminator: I train myself to distinguish the real images from the fake ones.
- Generator: I trick the discriminator to think my fake images as real ones.

- Two-player game objective:![[Screenshot 2023-02-06 at 18.18.50.png]]
- With fixed $\theta$; training $D_{\phi}$ as the classifier of the following binary classification task with MLE (negative cross entropy):
	- y = 1 if $x \sim p_{data}(x)$ else y = 0 if $x \sim p_{\theta}(x)$
- With fixed $\phi$; training $G_{\theta}$ to minimize the log-probability of $x \sim p_{\theta}(x)$ classified as "fake data" by $D_{\phi}$

Solving the two-player game objective:
- Assume the discriminator network $D_{\phi}$ has infinite capacity with fixed $\theta$ ![[Screenshot 2023-02-06 at 18.24.51.png]]
- Use the optimal discriminator (dependant on $\theta$) to the objective![[Screenshot 2023-02-06 at 18.27.26.png]]
- As a result, we get a valid divergence to be minimised so at equilibrium the generative model is equivalent to the true data distribution.

- In practice we use a double-loop algorithm 
	- Inner loop: with fixed $\theta$, optimise $\phi$ for a few gradient ascent iterations, real images:![[Screenshot 2023-02-06 at 18.30.32.png]]
	- Outer loop: with fixed $\phi$ from the inner loop, optimise $\theta$ by ONE gradient descent step, we only compute based on the fake data:![[Screenshot 2023-02-06 at 18.31.08.png]]
	- Repeat until convergence HYPERPARAMETERS NUMBER OF ITERATIONS ![[Screenshot 2023-02-06 at 18.32.58.png]]
- ![[Screenshot 2023-02-06 at 18.33.59.png]]
- ![[Screenshot 2023-02-06 at 18.37.13.png]]
- At the start we do not have high gradient for training the generator since it is randomly initialised so the discriminator can, with high probability, classify it as an fake image
- Solution :Use an alternative “non-saturate” loss:![[Screenshot 2023-02-06 at 18.39.10.png]]![[Screenshot 2023-02-06 at 18.39.24.png]]

## Variations on GANs

**Wassertein GAN** - scores not probabilities
![[Screenshot 2023-02-06 at 18.40.28.png]]
- Problem: Assume the discriminator network $D_{\phi}$ has infinite capacity: a trivial solution![[Screenshot 2023-02-06 at 18.41.16.png]]
- Solution:![[Screenshot 2023-02-06 at 18.43.43.png]]
	- Discriminator should assign high scores to data inputs and low scores to fake inputs At the same time, discriminator should be smooth to provide useful gradient for learning $G_{\theta}$
	- ![[Screenshot 2023-02-06 at 18.43.15.png]]
	- This provides stable learning for the the discriminator is 1 lipschitz

We need to solve: Constraint optimisation problem since the constraint is placed over all $x$ values, instead, ![[Screenshot 2023-02-06 at 18.46.22.png]]![[Screenshot 2023-02-06 at 18.46.44.png]]
- Training is similar to GANs
