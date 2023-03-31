- Most of the data we see is unlabelled 
- We focus on unsupervised learning
- We have data $x_1, x_2, ... x_n \sim p_{data}(x)$
- Goal: inferring a function that describes the hidden structure of unlabelled data
- All of the following can be achieved by using generative models
- Examples: 
	- Probability distribution/density estimation 
		- Goal: learn a distribution $p_{\theta}(x)\approx p_{data}(x)$ with data $x_1, x_2, ... x_n$
		- Latent Variable Models
			- Design  $p_{\theta}(x)$ as a generative latent variable model 
			- $z \sim p_{\theta}(x)$ and $x \sim p_{\theta}(x|z)$
			- So $p_{\theta}(x) = \int p_{\theta}(x|z)p_{\theta}(z)dz$
			- $z$ latent variable unobserved and $x$ observation variable![[Screenshot 2023-02-06 at 10.26.39.png]]
	- Dimensionality Reduction 
		- High dimensional raw data are often sparse perhaps lying on a low dimensional manifold.
		- Principal Component Analysis PCA
			- Find principal components - orthogonal directions that capture most of the variance in the data
			- Probabilistic Principal Component Analysis ![[Screenshot 2023-02-06 at 10.31.19.png]]
			- ![[Screenshot 2023-02-06 at 10.31.33.png]]
			- Auto-encoders for dimensionality reduction:
				- Encoder network to extract data representations
				- Decoder network to reconstruct data given the representation
			- All the dimensionality reduction methods have a probabilistic counterpart which use latent variable models ![[Screenshot 2023-02-06 at 10.32.53.png]]
	- Clustering
		- Discovering group structure
		- Group datapoints into several clusters
		- Datapoints in the same cluster are similar
		- Example: Gaussian Mixture Model (GMM)
			- ![[Screenshot 2023-02-06 at 10.34.54.png]]

- Both dimensionality reduction and clustering can be viewed as representation learning, the hope: useful for downstream tasks

#### Taxonomy of Generative Models
![[Screenshot 2023-02-06 at 10.36.27.png]]
- A Parametric Model is **a concept used in statistics to describe a model in which all its information is represented within its parameters**.