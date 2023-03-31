### Loss functions

#### Regression
- L2 Norm, mean squared error
	- ![[Screenshot 2023-02-04 at 09.04.00.png]]
	- Reduction to a single value can be either 𝑚𝑒𝑎𝑛(𝓛) or sum(𝓛). If dealing with mini-batches.
- L1 Norm
	- ![[Screenshot 2023-02-04 at 09.04.46.png]]
	- Use for robust regression (noisy data)
	- Problem, not differentiable at the bottom, use smooth L1 norm
- Smooth L1
	- ![[Screenshot 2023-02-04 at 09.06.11.png]]
	- Problem with the scale, why is it 0.5, you will need to tune this value in order to get good results.

### Classification
- Negative log likelihood loss
	- Assumption: Network output represents log likelihoods.
	- Make the desired output as large as possible and all others as small as possible
	- ![[Screenshot 2023-02-04 at 09.07.58.png]]
- Cross Entropy (CE) Loss
	- Combines LogSoftmax and NLLLoss 
	- Useful for classification problems with C classes
	- Classes can also be weighted. 
	- The losses are averaged across observations for each minibatch.
	- ![[Screenshot 2023-02-04 at 09.09.04.png]]
- Binary Cross Entropy (BCE) Loss
	- CE loss for only two classes
	- Probabilities between 0 and 1 
	- Useful if you have an autoencoder
	- ![[Screenshot 2023-02-04 at 09.10.21.png]]
- Margin Ranking Loss/Ranking Losses/Contrastive loss
	- Relative distance between inputs![[Screenshot 2023-02-04 at 09.13.52.png]]
	- Useful to push classes as far away as possible and for metric learning
	- Practical: take category that scores is closest or higher than correct one change until difference is at least the margin
	- similarity score between data points to use them. That score can be binary
	- To use a Ranking Loss function we first extract features from two (or three) input data points and get an embedded representation for each of them. 
	- Then, we define a metric function to measure the similarity between those representations, for instance Euclidian distance. 
	- Finally, we train the feature extractors to produce similar representations for both inputs, in case the inputs are similar, or distant representations for the two inputs, in case they are dissimilar.
- Triplet Margin Loss
	- Make samples from same classes close and different classes far away.![[Screenshot 2023-02-04 at 09.16.48.png]]
	- Objective: Distance for the good pair has to be smaller than distance to the bad pair. 
	- Actual distance does not need to be small, just smaller. Used for metric learning and Siamese networks
- Cosine Embedding Loss
	- Measure weather two inputs are similar or dissimilar 
	- Basically a normalised Euclidian distance![[Screenshot 2023-02-04 at 09.19.30.png]]


### Distributions
- Kullback-Leibler Divergence Loss
	- Measures distance between distributions![[Screenshot 2023-02-04 at 09.11.25.png]]
	- Y is a one-hot vector
	- May have numerically stability issues
	- Measure of closeness of distributions
	- Not used for a classification problem used for, used in auto-encoders, for bottlenecks
	- Variational Autoenconder!