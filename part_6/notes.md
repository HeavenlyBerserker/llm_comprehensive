## Fine tuning

In Supervised Finetuning (SFT), we want a high quality text corpus to train to adapt to specific tasks.

One aspect is that regular pretrained models are text completion engines, so they will not act like an assistant. If asked questions, they will just try to complete text. But SPT tries to change its behavior so that it answers questions and generally behaves like an assistant.

The training infrastructure is the same, but the data is going to be structured and propagated differently. The prompt is the following

template = (
    "<s>\n"
    "### Instruction:\n{instruction}\n\n"
    "### Response:\n{response}</s>"
)

Note that when doing inference, we remove </s> and {response} is "" so that it is prompted to complete the text.

-100 is the ignore index in pytorch. While training, y is the prompt trained on, we shift it by one each step and place -100 for the input so that is focuses on the output. This way the loss won't focus on the prompt, just the index.

Context windows can change because the matrix algebra works out with expanded context windows.

sample_sft contains the sampling for our SFTed model. It uses the KV cache and produces logits one by one.