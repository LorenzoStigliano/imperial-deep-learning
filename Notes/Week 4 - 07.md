### Batch Normalisation 

 - Loss is calculated at last layer
 - Last layers learn quickly
	- Data input is at first layer
	- Last layers need to relearn many time
	- Slow convergence
- Can we avoid change the last layers while learning first layers
- Fix mean and variance and adjust it separately![[Screenshot 2023-01-25 at 17.04.43.png]]![[Screenshot 2023-01-25 at 17.04.58.png]]
- We learn two additional parameters $\alpha$ and $\beta$ with the mini-batches 
- It works extremely well, doesn't reduce covariate shift, regularisation by noise injection
- No need to add dropout
- Ideal mini batch size: 64 - 256

- Dense layer: one normalisation for all 
- Convolution layer: one normalization per channel
- Compute new mean and variance for every minibatch
	- Acts as regularisaation
