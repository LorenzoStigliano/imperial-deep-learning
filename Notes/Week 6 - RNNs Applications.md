## Sequence-to-Sequence Model
![[Screenshot 2023-02-14 at 10.10.21.png]]
- Sequence encoder with LSTMs: 
	- Inputs: word embeddings of the words $x_{1:T}$
	- Outputs: representation of the EN sentence $v$
	- We also use the last LSTM to get the probability of the first word
	- Keeps running until it sees the <eos\> token ![[Screenshot 2023-02-14 at 10.11.35.png]]
- Sequence decoder
![[Screenshot 2023-02-14 at 10.12.15.png]]
- Sequence decoder inputs during training/test:![[Screenshot 2023-02-14 at 10.15.38.png]]

## Image Captioning
 - Image captioning with CNN encoder + LSTM decoder: 
 - CNN encoder extract representation $v$ of the image $x$
 - LSTM decoder generate caption conditioned on $v$
![[Screenshot 2023-02-14 at 10.17.18.png]]

## Sequence generation models
- Latent variable model for sequence generation![[Screenshot 2023-02-14 at 10.18.10.png]]
- Latent variable $z$
- Sequence VAE for language modelling![[Screenshot 2023-02-14 at 10.19.05.png]]
- At the end the encoder produces the distributional parameters

### Combining state-space models and RNNs
![[Screenshot 2023-02-14 at 10.20.30.png]]
![[Screenshot 2023-02-14 at 10.21.47.png]]
![[Screenshot 2023-02-14 at 10.22.33.png]]
![[Screenshot 2023-02-14 at 10.24.49.png]]
