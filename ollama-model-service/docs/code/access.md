# Access & Usage Information

## Basic Information

### Model Server URL

The model server API can be accessed at: http://ollama-route-ollama.apps.domain.com/v1

## Authentication

The model server does not require authentication to access, and can be accessed over a Kubernetes service or an external URL.

**Note:** If you are unable to access the model server via SSO you need to reach out to a platform administrator.

## API Schema
<!--
The name of the api, model-service-api, is grabbed from the name field in the ai-catalog.yaml metadata for the api.

TechDocs read this as a URL starting from where the docs are located, so we can use ../ behaviour to navigate the TechDocs to reference other resources/components/apis
-->
The API Schema is available [here](../../../../../api/ollama-service-api/definition).

## Usage Examples

### IBM Granite-20B-Code-Instruct

#### Text Generation

##### Using Curl

```
curl -X 'POST' \
    'http://ollama-route-ollama.apps.domain.com/v1/completions' \
    -H 'accept: application/json' \
    -H 'Content-Type: application/json' \
    -d '{
    "model": "ibm-granite-8b-code-instruct",
    "prompt": "San Francisco is a",
    "max_tokens": 15,
    "temperature": 0
}'
```

##### Python

```python
import requests
import urllib3
import numpy as np
import json

API_URL = "http://ollama-route-ollama.apps.domain.com"
API_KEY = "sk-no-key-required"

input = ["San Francisco is a"]

completion = requests.post(
    url=API_URL+'/v1/completions',
    json={
      "model": "ibm-granite-20b-code-instruct",
      "prompt": "San Francisco is a",
      "max_tokens": 15,
      "temperature": 0
    },
    headers={'Authorization': 'Bearer '+API_KEY}
).json()

print(completion)
```

##### Python With Langchain

**Note:** Requires `pip install langchain-community`

```python
from langchain_community.llms import VLLMOpenAI

API_URL = "http://ollama-route-ollama.apps.domain.com/v1"
API_KEY = sk-no-key-required

llm = VLLMOpenAI(
    openai_api_key=API_KEY,
    openai_api_base=API_URL
    model_name="ibm-granite-8b-code-instruct",
    model_kwargs={"stop": ["."]},
)
print(llm.invoke("Rome is"))
```

### phi-mini-instruct

#### Text Generation

##### Using Curl

```bash
curl -X 'POST' \
    'http://ollama-route-ollama.apps.domain.com/v1/completions' \
    -H 'accept: application/json' \
    -H 'Content-Type: application/json' \
    -d '{
    "model": "phi3.5:3.8b",
    "prompt": "What is Kubernetes?",
    "max_tokens": 50,
    "temperature": 0
}'
```