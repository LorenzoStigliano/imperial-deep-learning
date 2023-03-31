### VGG
![[Screenshot 2023-01-23 at 14.44.51.png]]

- The next step in the evolution of design came in the form of VGG, visual geometry group in Oxford.
- It is a bigger AlexNet
How to make a network better?
- More dense layers (too expensive) 
- More convolutions 
- Group into blocks - KEY INNOVATION 

#### VGG Blocks

"did a good comprehensive analysis and it showed that more layers of narrow convolutions were more powerful than a smaller number of wide convolutions"

- This tends to be a trend overall in the network designs that a: *larger number of compositions of simple functions turns out to be more expressive and more able to fit meaningful models than a small number of shallower and more complicated functions.*
![[Screenshot 2023-01-23 at 14.48.37.png]]
- The VGG block has a bunch of 3x3 convolutions
- If you padded them by one it didn't change the size of the input relative to the output and then in the end you have max pooling of two by two with a stride of two which halves the resolution.
- If you stack several of those things together and combine it with the same dense layers as we had in Alexnet, then you get VGG.
- Entire family of different such architectures simply by varying the number of such blocks that you will combine.
- So VGG is blocks + dense layers at the end for classification.

#### Progress

LeNet (1995) 
- 2 convolution + pooling layers 
- 2 hidden dense layers 

AlexNet 
- Bigger and deeper LeNet 
- ReLu, Dropout, preprocessing 

VGG 
- Bigger and deeper AlexNet (repeated VGG blocks)
- Wouldn’t have been possible without compute power progress (GPUs)