# Usage Examples
<!--
Sourced from: https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct#how-to-use
-->
This repository contains two versions of Meta-Llama-3.1-8B-Instruct, for use with transformers and with the original llama codebase.

## Use With Transformers
<!--
Sourced from: https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct#use-with-transformers
-->
Starting with transformers >= 4.43.0 onward, you can run conversational inference using the Transformers pipeline abstraction or by leveraging the Auto classes with the `generate()` function.

Make sure to update your transformers installation via `pip install --upgrade transformers`.

```python
import transformers
import torch

model_id = "meta-llama/Meta-Llama-3.1-8B-Instruct"

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

**Note:** You can also find detailed recipes on how to use the model locally, with torch.compile(), assisted generations, quantised and more at [huggingface-llama-recipes](https://github.com/huggingface/huggingface-llama-recipes)

### Tool Use With Transformers
<!--
Sourced from: https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct#tool-use-with-transformers
-->
LLaMA-3.1 supports multiple tool use formats. You can see a full guide to prompt formatting [here](https://llama.meta.com/docs/model-cards-and-prompt-formats/llama3_1/).

Tool use is also supported through [chat templates](https://huggingface.co/docs/transformers/main/chat_templating#advanced-tool-use--function-calling) in Transformers. Here is a quick example showing a single simple tool:

```python
# First, define a tool
def get_current_temperature(location: str) -> float:
    """
    Get the current temperature at a location.
    
    Args:
        location: The location to get the temperature for, in the format "City, Country"
    Returns:
        The current temperature at the specified location in the specified units, as a float.
    """
    return 22.  # A real function should probably actually get the temperature!

# Next, create a chat and apply the chat template
messages = [
  {"role": "system", "content": "You are a bot that responds to weather queries."},
  {"role": "user", "content": "Hey, what's the temperature in Paris right now?"}
]

inputs = tokenizer.apply_chat_template(messages, tools=[get_current_temperature], add_generation_prompt=True)
```

You can then generate text from this input as normal. If the model generates a tool call, you should add it to the chat like so:

```python
tool_call = {"name": "get_current_temperature", "arguments": {"location": "Paris, France"}}
messages.append({"role": "assistant", "tool_calls": [{"type": "function", "function": tool_call}]})
```

and then call the tool and append the result, with the tool role, like so:

```python
messages.append({"role": "tool", "name": "get_current_temperature", "content": "22.0"})
```

After that, you can `generate()` again to let the model use the tool result in the chat. Note that this was a very brief introduction to tool calling - for more information, see the [LLaMA prompt format docs](https://llama.meta.com/docs/model-cards-and-prompt-formats/llama3_1/) and the Transformers [tool use documentation](https://huggingface.co/docs/transformers/main/chat_templating#advanced-tool-use--function-calling).

## Use With Llama
<!--
Sourced from: https://huggingface.co/meta-llama/Meta-Llama-3.1-8B-Instruct#use-with-llama
-->
Please follow the instructions in this [repository](https://github.com/meta-llama/llama)

To download Original checkpoints, see the example command below leveraging `huggingface-cli`:

```
huggingface-cli download meta-llama/Meta-Llama-3.1-8B-Instruct --include "original/*" --local-dir Meta-Llama-3.1-8B-Instruct
```