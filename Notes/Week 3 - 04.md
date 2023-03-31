### AlexNet
![[Screenshot 2023-01-23 at 14.28.14.png]]
- AlexNet from 2012 was the first large scale convolutional neural network that was able to do well on the ImageNet classification task.
- In 2012 AlexNet was entered in the competition, and was able to outperform all previous non deep learning based models by a significant margin, and so this was the convNet that started the spree of convNet research usage afterwards.

#### Architecture overview
- Alexnet takes as input images of size 224 by 224 by 3. So these are 3 channel colour images.
- 11 by 11 filters at stride 4. Other people showed in the meantime that it isn't necessary to have such large filter kernels.
- we have a couple of fully connected layers of size 4096 and finally the last layer is FC8 going to the soft max, which is going to the 1000 ImageNet classes.
- AlexNet diagram is split into two different rows. The reason for this is mostly historical. AlexNet was trained on old GTX580 GPUs that only had 3 gigs of memory.
- It couldn't actually fit this entire network on these cards, and what they ended up doing, was they spread the network across two GPUs.
- In some layers there is communication between the GPUs.![[Screenshot 2023-01-23 at 14.41.45.png]]
#### The data used
![[Screenshot 2023-01-23 at 14.32.48.png]]
- ImageNet (2010): big data set at the time with 1.2 million examples, thousand classes compare that to 60 thousand samples, ten classes for MNIST.
- Images are in 3 channels.

#### Key modifications over LeNet
- Deeper and bigger LeNet
- Add a dropout layer after two hidden dense layers (better robustness / regularization)
- Change activation function from sigmoid to ReLu (no more vanishing gradient)
- MaxPooling - Novel, more shift invariant than average pooling
- Heavy data augmentation 
- Model ensembling

Revolutionary because it was a paradigm shift for computer vision, since the features we learnt from the CNN rather than manually engineered features. 

#### Complexity

![[Screenshot 2023-01-23 at 14.38.33.png]]
- In terms of computation it's 250 times more expensive, very extreme
- In terms of parameters only 10 times more