# **Ethical Considerations**
<!--
Sourced from: https://huggingface.co/google/gemma-2-2b#ethical-considerations-and-risks
-->
The development of large language models (LLMs) raises several ethical concerns. In creating an open model, we have carefully considered the following:

- **Bias and Fairness**
    - LLMs trained on large-scale, real-world text data can reflect socio-cultural biases embedded in the training material. These models underwent careful scrutiny, input data pre-processing described and posterior evaluations reported in this card.
    
- **Misinformation and Misuse**
    - LLMs can be misused to generate text that is false, misleading, or harmful.
    - Guidelines are provided for responsible use with the model, see the Responsible Generative AI Toolkit.

- **Transparency and Accountability**
    - This model card summarizes details on the models' architecture, capabilities, limitations, and evaluation processes.
    - A responsibly developed open model offers the opportunity to share innovation by making LLM technology accessible to developers and researchers across the AI ecosystem.

Risks identified and mitigations:

- **Perpetuation of biases:** It's encouraged to perform continuous monitoring (using evaluation metrics, human review) and the exploration of de-biasing techniques during model training, fine-tuning, and other use cases.
- **Generation of harmful content:** Mechanisms and guidelines for content safety are essential. Developers are encouraged to exercise caution and implement appropriate content safety safeguards based on their specific product policies and application use cases.
- **Misuse for malicious purposes:** Technical limitations and developer and end-user education can help mitigate against malicious applications of LLMs. Educational resources and reporting mechanisms for users to flag misuse are provided. - Prohibited uses of Gemma models are outlined in the Gemma Prohibited Use Policy.
- **Privacy violations:** Models were trained on data filtered for removal of PII (Personally Identifiable Information). Developers are encouraged to adhere to privacy regulations with privacy-preserving techniques.
