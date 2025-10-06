## Notes on basic training

Block size is the context window.

Top k is to only sample from the top k highest probabilities
Top p is to only sample from the top probabilities that cumulatively sum to a certain p.
Beam search is to consider sequences of token probabilities, i.e. /sum log P(x_t | x_{<t})