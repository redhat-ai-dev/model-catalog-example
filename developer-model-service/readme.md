# Developer Model Service

This model service example is based on the "Models-as-a-Service" reference implementation found here: https://github.com/rh-aiservices-bu/models-aas.

To stand up your own instance, follow the instructions in the reference implementation's repository, and select [granite-8b-code-instruct-4k](https://huggingface.co/ibm-granite/granite-8b-code-instruct-4k) as the deployed model.

## Models

The following model is deployed in the example:

- granite-8b-code-instruct

## Import into RHDH

If you wish to replicate this example:

1) Fork this repository.

2) Follow the instructions above to deploy the model server and models.

3) Modify the `catalog-info.yaml` as needed: replace any links (e.g. any `domain.com` references), and update any `Resources` as needed (for example, adding/removing models).

4) Select `Register Existing Component` in Backstage, and copy the catalog link into import form.
