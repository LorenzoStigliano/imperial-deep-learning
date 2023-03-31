### Inception (Network in Network)

- Network in network - multi-layer perceptron inserted as intermediate layers in my convolutional Network.
- A convolutional layer 
	- Kerel size, stride, and padding are hyper parameters
- Two 1x1 convolutions 
	- 1 stride and no padding, share the same output channels as first layer 
	- These act like dense layers 
	- ![[Screenshot 2023-01-25 at 16.36.40.png]]
- Final dense layers get replaced by ‘internal’ quasi dense layers 
- Mapping to number of output classes is done via globalAveragePooling

#### Inception - GoogLeNet

- Deep network and parallel paths in networks![[Screenshot 2023-01-25 at 16.41.13.png]]
- So you don't have to choose which convolution to use, the machine picks the one to use.![[Screenshot 2023-01-25 at 16.42.19.png]]
- Inception blocks have fewer parameters and less computation complexity than single 3x3 or 5x5 convolution layers
- They are a mix of different functions, which makes them a powerful function class 
- Computing and memory wise they are efficient (good generalisation)

![[Screenshot 2023-01-25 at 16.46.41.png]]
- ![[Screenshot 2023-01-25 at 16.50.19.png]]
- Architecture, this was discovered and tuned for the task at hand
- Stage 1 and 2 
	- Smaller kernel size and output channels because of more layers![[Screenshot 2023-01-25 at 16.51.09.png]]
- Stage 3![[Screenshot 2023-01-25 at 16.51.54.png]]
- Stage 4 and 5![[Screenshot 2023-01-25 at 16.52.30.png]]
- Inception-BN (v2) – added batch normalisation 
- Inception-V3 – Modified the inception block 
	- Replace 5x5 by multiple 3x3 convolutions 
	- Replace 5x5 by 1x7 and 7x1 convolutions 
	- Replace 3x3 by 1x3 and 3x1 convolutions 
	- Generally deeper stack![[Screenshot 2023-01-25 at 16.53.38.png]]![[Screenshot 2023-01-25 at 16.54.04.png]]
- Inception-V4 – adds residual connections
