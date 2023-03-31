NLP RNNs : [[Imperial/Spring Term/Natural Language Processing/Notes/Week 3 - 01]]

Example of Sequential data uses 
- Time series prediction: 
	- Data sequence (x_1, ... x_t)
	- Goal predict future values 

![[Screenshot 2023-02-13 at 19.01.13.png]]
- We maintain $h_t$, which is the hidden output of the RNN 
- We can unroll this out and feed $h_t$ at each time step 
![[Screenshot 2023-02-13 at 19.03.07.png]]
![[Screenshot 2023-02-13 at 19.03.16.png]]
- The derivative of the loss wrt to the $W_y$ in the output linear layer![[Screenshot 2023-02-13 at 19.03.55.png]]
- The derivative of the loss wrt to the $W_x$ in the output linear layer![[Screenshot 2023-02-13 at 19.05.02.png]]
- We need to compute the partial derivative backwards iteratively![[Screenshot 2023-02-13 at 19.06.20.png]]
- Issue of vanish gradients above ![[Screenshot 2023-02-13 at 19.08.00.png]]
- ![[Screenshot 2023-02-13 at 19.09.36.png]]
- The problem is that we find it hard to find longer dependencies due to the vanishing gradient problem![[Screenshot 2023-02-13 at 19.09.51.png]]

## LSTM 

- Solution to the vanishing gradients 
- Key ideas of LSTM: 
	- Introduce cell state $C_t$
	- Gating mechanisms to control cell state updates and output values![[Screenshot 2023-02-13 at 19.11.10.png]]

### Forget gate 
![[Screenshot 2023-02-13 at 19.11.44.png]]
### Input gate 
![[Screenshot 2023-02-13 at 19.12.08.png]]
### Cell state update 
![[Screenshot 2023-02-13 at 19.12.43.png]]
### Update the hidden state - Output gate 
![[Screenshot 2023-02-13 at 19.13.38.png]]

## Gated Recurrent Unit (GRU)
The Gated Recurrent Unit (GRU) improves the simple RNN with the gating mechanism as well. Compared with LSTM, GRU removes the input/output gates and the cell state, but still maintains the forgetting mechanism in some form![[Screenshot 2023-02-13 at 19.15.28.png]]
### LSTM vs GRU 
- Other gated RNN variants exists, but LSTM and GRU are the most widely-used 
- GRU is quicker to compute and has fewer parameters 
- No conclusive evidence for LSTM > GRU or vice versa 
- LSTM is a good default choice (especially if your data has particularly long dependencies, or you have lots of training data)
- Switch to GRU if you want more efficient compute & less overfitting

![[Screenshot 2023-02-13 at 19.20.41.png]]
![[Screenshot 2023-02-13 at 19.21.00.png]]
