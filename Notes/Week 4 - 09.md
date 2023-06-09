### Activation Functions

- Linear activation
	- Output = c x  
	- Constant gradient, no relationship to x during backpropagation
	- Even worse for fully connected layers. 
	- Each layer is activated by a linear function. 
	- That activation in turn goes into the next level as input and the second layer calculates weighted sum on that input and it in turn, fires based on another linear activation function. 
	- No matter how many layers we have, if all are linear in nature, the final activation function of last layer is nothing but just a linear function of the input of first layer.
	- N linearly activated layers can be replaced by a single layer.
- Sigmoid function
	- Output = $\frac{1}{1+e^{-input}}$
	- Nonlinear
	- between X values -2 to 2, Y values are very steep. 
	- Which means, any small changes in the values of X in that region will cause values of Y to change significantly. 
	- That means this function has a tendency to bring the Y values to either end of the curve. It tends to bring the activations to either side of the curve
	- Making clear distinctions on prediction.
	- Towards either end of the sigmoid function, the Y values tend to respond very less to changes in X. The gradient at that region is going to be small. 
	- It gives rise to a problem of “vanishing gradients”. This meant the network may refuse to learn further or is drastically slow.
- tanh function
	- Non Linear 
	- Stack layers
	- -1 to 1
	- One advantage of tanh is that we can expect the output to be close to have a zero-mean. This has advantages for the weights that follow, because they see positive and negative values and therefore tend to converge faster.
	- Deciding between the sigmoid or tanh will depend on your requirement of gradient strength. 
	- Unfortunately if you stack a lot of these you cannot learn very efficiently. One also needs to be very careful about normalisation.
- ReLU
	- 𝑂𝑢𝑡𝑝𝑢𝑡 = max (0, x)
	- Efficient 
	- Combinations of are non linear
	- It is not bound and the range of ReLu is \[0, inf). This means it can blow up the activation. The sparsity of the activation can also be a problem in networks. 
	- dying ReLu problem. 
	- Because of the horizontal line in ReLu( for negative X ), the gradient can go towards 0. For activations in that region of ReLu, gradient will be 0 because of which the weights will not get adjusted during descent.
- Leaky ReLU
	- Mitigates dying ReLu
	- will make it a slightly inclined line rather than horizontal line. This is leaky ReLu. There are other variations too. The main idea is to let the gradient be non zero and recover during training eventually.
- PReLU
	- 𝑎 is learnable 
	- Either one or a separate 𝑎 is used for each input channel
	- 𝑎 is the steepness of the 0 part of ReLU