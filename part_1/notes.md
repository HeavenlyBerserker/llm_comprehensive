## Transformer Decoder
LLMs are decoder-only architectures.

Parts:
- Embedding
- Positional encoding
- Masked multi-head attention: Same output dimension as input
    - Gets qkv-ed by applying linear layer to forward output.
    - Remember scaled dot product Attention(Q,K,V) = softmax(QK^T/sqrt(d_k))V
    - Concatenate over heads and apply proj linear layer
    - Convert to qkv again.
    - Causal mask is an upper triangular matrix
- Add & Norm
- Masked multi-head attention
- Add & Norm
- Feed Forward
- Add & Norm
- Linear
- Softmax

Causal mask just makes upper right of matrix 0s. Masks the answer tokens.
1 0 0
1 1 0
1 1 1