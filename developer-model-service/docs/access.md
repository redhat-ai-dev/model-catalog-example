# Access & Usage Information

## Basic Information

### Model Server URL

The model server can be accessed [here](https://model-service.apps.domain.com/).

## Authentication

In order to gain access to the model server you will need to sign in with your SSO credentials by selecting Google auth. Once you have signed in you are able to generate a token by navigating to **`Apps and API Keys`** on the top ribbon and hitting **`Create new Application`**:

![Generation Example](./images/generation-example.png)

Once a token has been generated, you will be provided with the API server URL.

**Note:** If you are unable to access the model server via SSO you need to reach out to a platform administrator.

## API Schema
<!--
The name of the api, model-service-api, is grabbed from the name field in the catalog-info.yaml metadata for the api.

We can use absolute paths to navigate the TechDocs to reference other resources/components/apis
-->
The API Schema is available [here](/catalog/default/api/model-service-api/definition).

## Usage Examples
<!--
Sourced from: https://github.com/rh-aiservices-bu/models-aas/blob/main/deployment/3scale/portal/Examples.html.liquid
-->

### IBM Granite-8B-Code-Instruct

#### Text Generation

##### Using Curl

```
curl -X 'POST' \
    'https://ibm-granite-8b-code-instruct-3scale-apicast-production.apps.domain.com/v1/completions' \
    -H 'accept: application/json' \
    -H 'Content-Type: application/json' \
    -H 'Authorization: Bearer <YOUR_API_KEY>' \
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

API_URL = "https://ibm-granite-8b-code-instruct-3scale-apicast-production.apps.domain.com"
API_KEY = "***************************"

input = ["San Francisco is a"]

completion = requests.post(
    url=API_URL+'/v1/completions',
    json={
      "model": "ibm-granite-8b-code-instruct",
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

API_URL = "https://ibm-granite-8b-code-instruct-3scale-apicast-production.apps.domain.com"
API_KEY = "***************************"

llm = VLLMOpenAI(
    openai_api_key=API_KEY,
    openai_api_base=API_URL+"/v1",
    model_name="ibm-granite-8b-code-instruct",
    model_kwargs={"stop": ["."]},
)
print(llm.invoke("Rome is"))
```


##### Connecting Continue.dev to Granite-Code-Instruct

```
...
"models": [
    {
      "title": "Granite-8B-Instruct",
      "provider": "openai",
      "model": "ibm-granite-8b-code-instruct",
      "apiBase": "https://ibm-granite-8b-code-instruct-3scale-apicast-production.apps.domain.com/v1/",
      "apiKey": "************************",
      "completionOptions": {
      "temperature": 0.1,
      "topK": 1,
      "topP": 1,
      "presencePenalty": 0,
      "frequencyPenalty": 0
      }
    }
...
"tabAutocompleteModel": {
    "title": "Granite-8B-Instruct",
    "provider": "openai",
    "model": "ibm-granite-8b-code-instruct",
    "apiBase": "https://ibm-granite-8b-code-instruct-3scale-apicast-production.apps.domain.com/v1/",
    "apiKey": "****************************",
    "completionOptions": {
      "temperature": 0.1,
      "topK": 1,
      "topP": 1,
      "presencePenalty": 0,
      "frequencyPenalty": 0
    }
  },
  "tabAutocompleteOptions": {
    "useCopyBuffer": false,
    "maxPromptTokens": 1024,
    "prefixPercentage": 0.5
  },
...
```
