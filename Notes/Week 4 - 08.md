### ResNet

- Does adding more layers improve accuracy?
	- ResNet, are good in practice and help with gradients that do not go through
	- Deep networks diverge away and are not expressive as layers increase
	- As more layers added the expressiveness of functions increase this is what ResNet achieves
- Adding a layer changes function class
- We want to add to the function class ![[Screenshot 2023-01-25 at 17.15.05.png]]
- If it needs to it can ignore a block
- Add input to the output

ResNet Block
![[Screenshot 2023-01-25 at 17.17.11.png]]
- Networks searches to not change the network
- Each block has 2 conv layers
- There are different flavours of ResNet, they did this by trail and improvement
- Smaller memory footprint than the inception network

**ResNext**
- People pushed this idea of course further and Xie et al introduced ResNEXT. 
- And it has a neat idea in it. Essentially, it relies on the following observation. If this is our resnet block, right, so we have a one by one and maybe a three by three, then we have a one by one.

- We can reduce the complexity by using groups in 2d convolution.

#### More ideas
- DenseNet
	- DenseNet uses higher order ‘Taylor series’ expansion![[Screenshot 2023-01-25 at 17.29.32.png]]
	- Occasionally need to reduce resolution (transition layer)
- Squeeze-Excite Net
	- Learn global weighting function per channel 
	- Allows for fast information transfer between pixels in different locations of the image
- ShuffleNet
	- ResNext breaks convolution into channels 
	- ShuffleNet mixes by grouping (very efficient for mobile)
