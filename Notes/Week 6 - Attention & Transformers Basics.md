### Motivation
- Long sequence is everywhere, LSTMs don't generalise well with long sequences

## Attention
![[Screenshot 2023-02-27 at 09.29.43.png]]
- The $v$ vector needs to capture as much information as possible in Seq2Seq![[Screenshot 2023-02-27 at 09.30.29.png]]
- With attention we get a weighted sum of the all of the sequences using an RNN encoder before hand
- ![[Screenshot 2023-02-27 at 09.31.25.png]]
- Notice $\alpha$ are different for each token 
- If alignment score is high then the feature for that token will be high 
- Still relies on RNNs for encoder feature extraction 

## Attention in Transformers
![[Screenshot 2023-02-27 at 09.33.30.png]]
![[Screenshot 2023-02-27 at 09.34.30.png]]
![[Screenshot 2023-02-27 at 09.35.42.png]]
![[Screenshot 2023-02-27 at 09.36.27.png]]
- We can also used masked attention, to mask out key vectors for the query vector $Q_n$ so their corresponding value vectors $V_n$ do not contribute to the value output for that query

### Time Complexity 
![[Screenshot 2023-02-27 at 09.38.24.png]]

### Multi-head attention
![[Screenshot 2023-02-27 at 09.39.31.png]]
- We project Q, K, V to different lower dimensional spaces, which reflect different aspects of the alignment processes
- ![[Screenshot 2023-02-27 at 09.42.23.png]]

## Transformer Architecture

![[Screenshot 2023-02-27 at 09.43.39.png]]
![[Screenshot 2023-02-27 at 09.44.08.png]]

### Encoder 

Attention is permutation equivariant so we need the positional encoding keeps this information![[Screenshot 2023-02-27 at 09.44.33.png]]
Position encoding: 
- inject ordering information Can either be learned or be a pre-defined mapping![[Screenshot 2023-02-27 at 09.45.47.png]]
- Normalisation layer to stabilise learning similar to batch norm![[Screenshot 2023-02-27 at 09.46.16.png]]
- Output of the encoder![[Screenshot 2023-02-27 at 09.46.57.png]]

### Decoder 

![[Screenshot 2023-02-27 at 09.48.07.png]]
- We mask out all of the the current future words so the model is trained using previous words
- ![[Screenshot 2023-02-27 at 09.49.12.png]]
- Trained with MLE or negative cross entropy loss