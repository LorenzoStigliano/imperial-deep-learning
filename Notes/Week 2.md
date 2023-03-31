- Motivation: popular becomes it works often
- Lots of data very powerful

### 01 - Curse of Dimensionality 

Why do neural networks fail image analysis? Due to the curse of dimensionality. As the number of features grows or dimension, the amount of data we need to generalize accurately grows exponentially.

To illustrate this suppose you fix the number of samples $n=10$. In one dimension suppose you want to know what 20% of the samples occupy the space. In one dimension is 2 samples. 

In 2D with $n=10$, 20% of the space is a $length^d \approx (\frac{k}{n})$, where n is the number of samples and k is the number of samples  we are interested in. So as the dimension increases you have more empty space, where the samples can live.

Number of features to approximate a lipschitz continuous function $O(\epsilon^{-d})$ where $\epsilon$ is the accuracy and $d$ is the dimension.

### 02 - Convolution

Motivation: self similarity in images and curse of dimensionality.
![[Screenshot 2023-01-19 at 16.44.35.png]]
![[Screenshot 2023-01-19 at 16.46.48.png]]
**Why do I need this?**
In convolutional neural networks, convolutions can be implemented through weight sharing, i.e., the weights of N spacial neighbours are identical as illustrated in the extremely simple example in Figure 1. These shared weights can be interpreted as weights of a filter function. The input tensor is convoluted with this filter function (c.p. sliding window filter) before the activation of a convolutional layer. Reduces the number of features from $N^2$ to $K$. This is the main idea REDUCE COMPUTATIONAL COMPLEXITY WITHOUT LOSS OF ACCURACY.
![[Screenshot 2023-01-19 at 16.47.45.png]]
### 03 - Convolution Neural Networks
- No spatial strucutre preservation, fully connect layer with a neural network.
- We need priors about the data.
- CNN preserve structure
![[Screenshot 2023-01-19 at 16.52.11.png]]

- The filter is learnt through backpropagation dependant on a task
![[Screenshot 2023-01-19 at 16.54.14.png]]
![[Screenshot 2023-01-19 at 16.54.28.png]]
If you do not want image shrinkage add zero padding:
![[Screenshot 2023-01-19 at 16.54.47.png]]
Learning a different feature map from different filters
![[Screenshot 2023-01-19 at 16.55.20.png]]
![[Screenshot 2023-01-19 at 16.56.22.png]]
Number of parameters:
- $5*5*3+1 = 76$ paramerters, $76*6 = 456$ parameters for first layer.
- $3*3*6+1 = 55$ paramerters, $55*10 = 550$ parameters for second layer.

You can also do a 1x1 convlulution to reduce the chanel from 3 to 1.![[Screenshot 2023-01-19 at 17.00.50.png]]

#### Padding and strides

Padding - what you add around the image
Strides - is what you move the filter around by so jump 1 or 2 pixels
![[Screenshot 2023-01-19 at 17.02.04.png]]

#### Computational complexity
![[Screenshot 2023-01-19 at 17.03.43.png]]
We can reduce the complexity by applying two smaller filters
![[Screenshot 2023-01-19 at 17.05.37.png]]
We can take this further by applying seperable filters![[Screenshot 2023-01-19 at 17.06.47.png]]

#### Pooling
- Permutation-invariant aggregation+ downsampling (max or avg)
- Reduces resolution
- Hierarchical features
- Contributes to approximate shift
Example:
![[Screenshot 2023-01-19 at 17.08.37.png]]
![[Screenshot 2023-01-19 at 17.09.34.png]]

### What do CNNs Learn?
- Visualize the feature maps per layer
- We can see basic features and in higher layers more abstract features are being learnt

### Takeaways
- Convolutions can massively reduce the computational complexity of neural networks but the real power of CNNs is revealed when priors are implemented and for example spatial structure is preserved. This is also one of the reasons why CNNs have been so successful in Computer Vision 
- CNNs are pipeline of learnable filters interleaved with nonlinear activation functions producing d-dimensional feature maps at every stage. Training works like a common neural network: initialise randomly, present exampled from the training database, update the filter weights through backpropagation by propagating the error back through the network. 
- Convolution and pooling can be used to reduce the dimensionality of the input data until it forms a small enough representation space for either traditional machine learning methods for classification or regression or to steer other networks to for example generate a semantic interpretation like a mask of a particular object in the input.