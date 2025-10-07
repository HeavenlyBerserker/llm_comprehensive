## BPE
Byte pair encoding tokenizer

Iteratively replace common 2-strings with new token. It will increase our vocab size by 1, but will decrease our representaiton length by a lot, potentially. It also helps with semantic understanding of "words" instead of byte level stuff. BPETokenizer train does not backpropagate anything, it just figures out the new encodings based on the text.

We gloss over, but implemented in Rust, so very fast. 

## Data loader is a lazy loader

## LR
The learning rate has a warm up stage that increases LR linearly to end in base rate.
Then the LR will fluctuate using a cosine function, i.e. 0.5xbase_rate -> 0 -> 0.5xbase_rate -> base_rate -> repeat, but not as abrupt, smooth like a cosine function.

## Gradient accumulation

You just split each mini-batch into micro-batches and accumulate the gradient instead of saving the gradient for each sample in the mini-batch. This way, you will have a gradient the size of your micro-batch and not the size of your mini-batch.

In practice, our minibatches become micro-batches but we accumulate gradients. At the end, we can handle larger batch sizes because we use only the memory of a batch size while doing the work of batch_size x accumulator_steps (usually 2 or 4).