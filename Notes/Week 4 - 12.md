### U-Net Architecture

- U-net is designed for image segmentation  [[Week 4 - 04]] 
- ![[Screenshot 2023-02-04 at 09.31.28.png]]
- It is an encoder/decoder architecture
- First half encoder and second part decoder upsampling
- Plus skip connections improve performance since it gives localisation information 
- When upsampling we reduce the number of channels by 2
- Remember to pad when needed
- Variants
	- 3D U-Net 2016
	- H-DenseUNet for liver and Tumor Segmentation 2017 
	- UNet++ more powerful medical image segmentation 2018
	- nnU-Net automatic self adapting framework 2018
	- Graph U-Net 2019