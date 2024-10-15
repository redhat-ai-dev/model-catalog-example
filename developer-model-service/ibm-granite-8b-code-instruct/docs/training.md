# **Training Information**

## **Training Infrastructure**
<!--
Sourced from: https://huggingface.co/ibm-granite/granite-8b-code-instruct-4k#infrastructure
-->
Granite Code models were trained using two of IBM's super computing clusters, Vela and Blue Vela. Both were outfitted with NVIDIA A100 and H100 GPUs, respectively. These clusters provide a scalable and efficient infrastructure for training the models over thousands of GPUs.

## **Training Data**
<!--
Sourced from: https://huggingface.co/ibm-granite/granite-8b-code-instruct-4k#training-data
-->
The Granite Code Instruct models were trained on the following data types:

- **Code Commits Datasets:** we sourced code commits data from the [CommitPackFT](https://huggingface.co/datasets/bigcode/commitpackft) dataset, a filtered version of the full CommitPack dataset. From CommitPackFT dataset, we only consider data for 92 programming languages. Our inclusion criteria boils down to selecting programming languages common across CommitPackFT and the 116 languages that we considered to pretrain the code-base model (*Granite-8B-Code-Base*).

- **Math Datasets:** We consider two high-quality math datasets, [MathInstruct](https://huggingface.co/datasets/TIGER-Lab/MathInstruct) and [MetaMathQA](https://huggingface.co/datasets/meta-math/MetaMathQA). Due to license issues, we filtered out GSM8K-RFT and Camel-Math from MathInstruct dataset.

- **Code Instruction Datasets:** We use [Glaive-Code-Assistant-v3](https://huggingface.co/datasets/glaiveai/glaive-code-assistant-v3), [Glaive-Function-Calling-v2](https://huggingface.co/datasets/glaiveai/glaive-function-calling-v2), [NL2SQL11](https://huggingface.co/datasets/bugdaryan/sql-create-context-instruction) and a small collection of synthetic API calling datasets.

- **Language Instruction Datasets:** We include high-quality datasets such as [HelpSteer](https://huggingface.co/datasets/nvidia/HelpSteer) and an open license-filtered version of [Platypus](https://huggingface.co/datasets/garage-bAInd/Open-Platypus). We also include a collection of hardcoded prompts to ensure our model generates correct outputs given inquiries about its name or developers.