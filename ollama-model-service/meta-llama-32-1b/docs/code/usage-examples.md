# **Usage Examples**
<!--
Sourced from: https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct#how-to-use
-->

## **Use with transformers**

Starting with transformers >= 4.43.0 onward, you can run conversational inference using the Transformers pipeline abstraction or by leveraging the Auto classes with the generate() function.

Make sure to update your transformers installation via pip install --upgrade transformers.

```python
import transformers
import torch

model_id = "meta-llama/Meta-Llama-3.2-1B-Instruct"

pipeline = transformers.pipeline(
    "text-generation",
    model=model_id,
    model_kwargs={"torch_dtype": torch.bfloat16},
    device_map="auto",
)

messages = [
    {"role": "system", "content": "You are a pirate chatbot who always responds in pirate speak!"},
    {"role": "user", "content": "Who are you?"},
]

outputs = pipeline(
    messages,
    max_new_tokens=256,
)
print(outputs[0]["generated_text"][-1])
```

## **Tool use with transformers**

LLaMA-3.1 supports multiple tool use formats. You can see a full guide to prompt formatting [here](https://llama.meta.com/docs/model-cards-and-prompt-formats/llama3_1/).

Tool use is also supported through [chat templates](https://huggingface.co/docs/transformers/main/chat_templating#advanced-tool-use--function-calling) in Transformers. Here is a quick example showing a single simple tool:

```python
import transformers
import torch

model_id = "meta-llama/Meta-Llama-3.2-1B-Instruct"

pipeline = transformers.pipeline(
    "text-generation",
    model=model_id,
    model_kwargs={"torch_dtype": torch.bfloat16},
    device_map="auto",
)

messages = [
    {"role": "system", "content": "You are a pirate chatbot who always responds in pirate speak!"},
    {"role": "user", "content": "Who are you?"},
]

outputs = pipeline(
    messages,
    max_new_tokens=256,
)
print(outputs[0]["generated_text"][-1])
```

*[Code Reference](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct#how-to-use)*