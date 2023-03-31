### Invariance and Equivariance

#### Shift invariance 
- We don't care where the object is located, we expect the same output.
- It will not produce a different variant of the output only because the object in the input space underwent a linear translation. So shift invariance means that the output of the left function and the right function is the same.![[Screenshot 2023-01-23 at 12.26.22.png]]
#### Shift equivariance 
- Well let’s say we have now a different model and we want to segment the cat. 
- We want to label every pixel that belongs to the cat as 1 and all the pixels that belong not to the cat as 0. 
- So in this case the output of the cat detector should shift exactly in the same way as the cat is shifted.![[Screenshot 2023-01-23 at 12.27.32.png]]

#### Comparison 
![[Screenshot 2023-01-23 at 12.27.56.png]]

#### How is shift invariance achieved in CNNs?
![[Screenshot 2023-01-23 at 12.29.03.png]]
Filter Kernels:
- In theory, applying a filter kernel to an image should not change the filter response. 
- This can be proven in frequency space and through the Fourier transform where we can find that convolutions in the image or time domain (remember back the animations about two convoluted functions) is equivalent to a multiplication in frequency space. 
- So in theory convolutions should be ***shift equivariant***.

Pooling:
- Now, pooling builds up ***shift invariance***. 
- Approximately If I shift the image a little bit under this pooling kernel, the maximum will still be the same. 
- It is not completely bullet proof but at least locally it will still find the same maximum in this small window.

Drawback:
- Max-pooling breaks ***shift equivariant***.
- Partial solution: use what you learned about anti-aliasing in Computer Vision: blur and then down sample

#### Group equivarance
![[Screenshot 2023-01-23 at 12.35.27.png]]
- Groups are simply collections of operations that have the property of closure.
- These are any operations where if I combine two elements of that group I get another element of that group.
- Simple example: rotations: I can first rotate a little bit to the left and then another little bit and if I combine these I get a consolidated rotation matrix that will do exactly the same as the two previous ones.

#### Approximate Deformation invariance

![[Screenshot 2023-01-23 at 12.39.24.png]]
- Warping operations like small local perturbations – like variants of smooth transformations of a canonical 3 like in this image.
- We can think of these deformations as small local shifts, so CNNs are so successful for example classifying these handwritten digits because they are approximately invariant to these shifts.![[Screenshot 2023-01-23 at 12.40.11.png]]
- CNN are approximately shift invariance and equivariant invariant.