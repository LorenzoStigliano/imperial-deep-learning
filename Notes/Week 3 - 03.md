### LeNet

- LeNet was a network proposed in the 90s so LeNet-5 is around 1995 by Yann LeCun and his team.
- In the simplest version this was engineered for low resolution black and white object recognition.
- The inputs were 32 by 32 bit image size images.
- Those images were then convolved to turn into six channels of 28 by 28 pixels which were then reduced through average pooling to 14 by 14

Why would people have care about it 1995?

- At&T at the time had a project about handwritten digit recognition. Handwritten characters for postal codes on letters and also amounts on checks.

#### MNIST

- MNIST was a data set that was engineered specifically for the purpose of handwritten digit recognition. It consisted of centered and scaled images. 
- 50,000 training data and 10,000 tests data at the resolution of 28 by 28 pixels.![[Screenshot 2023-01-23 at 14.23.48.png]]

- Problem: These fully connected layers can be quite expensive if we have many outputs, so for ten classes it's not a big deal.