# Ollama Model Service

This model service example is based on the `ollama-ubi` image and manifests provided here: https://github.com/redhat-ai-dev/ollama-ubi.

To stand up your own instance, follow the instructions in the repository to deploy resources to Kubernetes. After the ollama instance has been deployed, following the instructions to use the `ollama` CLI to pull the models of your choice.

## Models

The models deployed in the example are:

- gemma2:2b
- llama3.2:1b
- phi3.5:3.8b
- granite-code:20b

However, if you wish to deploy different or less models, simply remove the corresponding `Resources` from the [ai-catalog.yaml](./ai-catalog.yaml). 

## Import into RHDH

If you wish to replicate this example:

1) Fork this repository.

2) Follow the instructions above to deploy the model server and models.

3) Modify the `ai-catalog.yaml` as needed: replace any links (e.g. any `domain.com` references), and update any `Resources` as needed (for example, adding/removing models).

4) Select `Register Existing Component` in Backstage, and copy the catalog link into import form.