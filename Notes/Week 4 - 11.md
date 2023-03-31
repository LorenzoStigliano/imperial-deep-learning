### Input Augmentation

- Artificially inflate training data size through applying expected transformations during training
- Excellent regularizer against overfitting
- Random 
	- flipping • scaling • rotations • intensity/contrast variations • cropping/padding • noise • affine transformations • perspective transformations
- Don’t just use all of them blindly. Carefully select expected transformations

Anomaly detection
- Predict continuation 
- Measure distance in a latent space 
- Reconstruct the input
- Classify artificial, subtle variations 
- Also known as out-of-distribution detection