# Training Information

## Training Infrastructure
We used custom training libraries, Meta's custom built GPU cluster, and production infrastructure for pretraining. Fine-tuning, annotation, and evaluation were also performed on production infrastructure.

Training utilized a cumulative of 39.3M GPU hours of computation on H100-80GB (TDP of 700W) type hardware, per the table below. Training time is the total GPU time required for training each model and power consumption is the peak power capacity per GPU device used, adjusted for power usage efficiency.

Training Greenhouse Gas Emissions Estimated total location-based greenhouse gas emissions were 11,390 tons CO2eq for training. Since 2020, Meta has maintained net zero greenhouse gas emissions in its global operations and matched 100% of its electricity use with renewable energy, therefore the total market-based greenhouse gas emissions for training were 0 tons CO2eq.

|   | Training Time (GPU hours)  | Training Power Consumption (W)  | Training Location-Based Greenhouse Gas Emissions (tons of CO2eq)  | Training Market-Based Greenhouse Gas Emissions (tons of CO2eq)  |
|---                  |---      |---   |---      |--- |
| **Llama 3.1 8B**    | 1.46M   | 700  | 420     | 0  |

The methodology used to determine training energy use and greenhouse gas emissions can be found [here](https://arxiv.org/pdf/2204.05149). Since Meta is openly releasing these models, the training energy use and greenhouse gas emissions will not be incurred by others.

## Training Data

### Overview
Llama 3.1 was pretrained on ~15 trillion tokens of data from publicly available sources. The fine-tuning data includes publicly available instruction datasets, as well as over 25M synthetically generated examples.

### Data Freshness
The pretraining data has a cutoff of December 2023.

### Benchmark Scores
In this section, we report the results for Llama 3.1 models on standard automatic benchmarks. For all the evaluations, we use our internal evaluations library.

#### Base Pretrained Models
| **Category** | **Benchmark** | **# Shots** | **Metric** | **Llama 3.1 8B** |
|---                  |---      |---   |---      |--- |
| **General** | MMLU | 5 | macro_avg/acc_char | 66.7 |
|| MMLU-Pro(CoT) | 5 | macro_avg/acc_char | 37.1 |
|| AGIEval English | 3-5 | average/acc_char | 47.8 |
|| CommonSenseQA | 7 | acc_char | 75.0 |
|| Winogrande | 5 | acc_char | 60.5 |
|| BIG-Bench Hard (CoT) | 3 | average/em | 64.2 |
||ARC-Challenge |25 | acc_char | 79.7 |
| **Knowledge Reasoning** | TriviaQA-Wiki | 5 | em | 77.6 |
| **Reading Comprehension** | SQuAD | 1 | em | 77.0 |
||QuAC (F1) | 1 | f1 | 44.9 |
|| BoolQ | 0 | acc_char | 75.0 |
|| DROP (F1) | 3 | f1 | 59.5 |

#### Instruction Tuned Models
| **Category** | **Benchmark** | **# Shots** | **Metric** | **Llama 3.1 8B Instruct** |
|---                  |---      |---   |---      |--- |
| **General** | MMLU | 5 | macro_avg/acc_char | 69.4 |
|| MMLU (CoT) | 0 | macro_avg/acc_char | 73.0 |
|| MMLU-Pro (CoT) | 5 | micro_avg/acc_char | 48.3 |
||IFEval||| 80.4 |
| **Reasoning** |ARC-C|0|acc|83.4|
||GPQA|0|em|30.4|
| **Code** |HumanEval|0|pass@1|72.6|
||MBPP++ base version|0|pass@1|72.8|
||Multipl-E HumanEval|0|pass@1|50.8|
||Multipl-E MBPP|0|pass@1|52.4|
| **Math** |GSM-8K (CoT)|8|em_maj1@1|84.5|
||MATH (CoT)|0|final_em|51.9|
| **Tool Use** |API-Bank|0|acc|82.6|
||BFCL|0|acc|76.1|
||Gorilla Benchmark API Bench|0|acc|8.2|
||Nexus (0-shot)|0|macro_avg/acc|38.5|
| **Multilingual** |Multilingual MGSM (CoT)|0|em|68.9|

#### Multilingual Benchmarks
| **Category** | **Benchmark** | **Language** | **Llama 3.1 8B** |
|---                  |---      |--- |--- |
| **General** | **MMLU (5-shot, macro_avg/acc)** | Portuguese | 62.12 |
|||Spanish|62.45|
|||Italian|61.63|
|||German|60.59|
|||French|62.34|
|||Hindi|50.88|
|||Thai|50.32|