## Mixture-of-experts

Instead of the MLP layer, we have smaller MLPs but more focused

The TopKGate or router uses a linear layer to get logits that represents probability of going into different experts. 

There is a load balancing problem so we need to penalize the model for concentrating all load into a single expert. Celebrity problem. We take the load (fraction of tokens assigned as primary, i.e. top 1 for expert).

Hybrid is symply

Blend dense FFN with MoE output: y = α * Dense(x) + (1−α) * MoE(x)