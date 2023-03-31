### Attention application pre-2017

- Attention used in RNN generators back in 2013:
	- Idea: align two different sequences with different length ![[Screenshot 2023-02-27 at 10.17.06.png]]
	- ![[Screenshot 2023-02-27 at 10.17.22.png]]
- DRAW model, extending Graves (2013):
	- A VAE generative model for images combining RNNs and Gaussian attention
	- Treat intermediate drawing states latent variable
	- Decoder uses “read” and “write” operations guided by attention 
	- Gaussian attention to select focused patch at time t 
	- The Gaussian attention filter parameters are obtained from the RNN in the decoder
- Attention applied in image captioning:
	- CNN low-level features are indexed by spatial location
	- Sort CNN features and then process with RNNs 
	- Apply similar RNN attention methods in Bahdanau et al. (2014)

### Transformers in NLP 
- Pretraining Transformer models on massive data
- Deeper & bigger Transformer architecture with modifications 
- Pretrained on very big corpus by e.g. randomly masking out and predicting words in a sequence 
- After training: Fine-tune on specific tasks that the user cares

## Multi-head attention in other application
- Can be applied to any Set Data with/out indexing
	- Text = set of words, Image = set of pixels (or set of patches), Graph = set of nodes and edges, point cloud = set of points, … 
	- Cross-modality application: embed points from diff. modality to the same space then apply attention
	- An image is an ordered set of patches![[Screenshot 2023-02-27 at 10.22.56.png]]
	- We can see that these projections act as an convolutional layer 
	- Attention in original form is very expensive
Other application:
- Image completion & super-resolution 
- Regression & supervised learning 
- Point cloud applications
![[Screenshot 2023-02-27 at 10.26.14.png]]
## Efficient Transformers

- Local attention by defining “neighbourhood”: 
	- Treat the input as a sequence with position ordering and build an auto-regressive model 
	- At current position, both the query and the key (or memory) inputs are “local”![[Screenshot 2023-02-27 at 10.27.45.png]]
	- These are hyperparameters we choose to balance between memory and performance
- Sparse attention by defining attention weight matrix patterns
	- ![[Screenshot 2023-02-27 at 10.28.51.png]]
	- Sparse attention matrix: fix rules such that only for certain pairs of (i,j) the attention entry is computed 
	- Different attention heads can have different sparsity patterns
- Low-rank approximations:
	- ![[Screenshot 2023-02-27 at 10.29.40.png]]
	- Makes the scaling linear when the activation function is linear
	- Closely related to kernel methods
- Learnable inducing points for set summary:![[Screenshot 2023-02-27 at 10.31.01.png]]

## Memorisation in Transformers

Potential privacy issues: 
- Transformer-based Language models has billions of parameters 
- Capable for memorising the input data 
- Currently they are pre-trained on open-web text without any privacy protection 
- Attacks can steal sensitive input data