## An Empirical Study of Sequence Models for Text Classification

---

# 1. Project Overview

This project investigates a fundamental question in modern deep learning:

**When do Transformer architectures outperform recurrent models like LSTM and GRU?**

While Transformers dominate many NLP benchmarks, they are computationally expensive and often require large datasets. In contrast, recurrent models may perform competitively in low-resource settings.

This project performs a **systematic empirical comparison** of three sequence architectures:

* LSTM (Long Short-Term Memory)
* GRU (Gated Recurrent Unit)
* Transformer Encoder

The experiments evaluate model behavior under different conditions including:

* varying sequence lengths
* varying dataset sizes
* inference latency
* training stability

The objective is to identify **practical scenarios where each architecture is most suitable.**

---

# 2. Research Questions

This project attempts to answer the following research questions:

### RQ1 — When do Transformers outperform LSTMs?

We analyze performance across dataset size and sequence length.

### RQ2 — How do recurrent models behave with long sequences?

We test whether LSTM/GRU struggle with increasing sequence length.

### RQ3 — Do Transformers require more training data?

We evaluate accuracy under progressively larger training datasets.

### RQ4 — What is the accuracy vs inference speed trade-off?

We compare inference latency across models.

---

# 3. Dataset

Dataset used:

IMDb Large Movie Review Dataset

Task:

Binary sentiment classification

* Class 0 → Negative Review
* Class 1 → Positive Review

Dataset statistics:

* Training samples: 25,000
* Test samples: 25,000

For controlled experiments we used subsets:

* 1,000 samples
* 5,000 samples
* 10,000 samples

---

# 4. Model Architectures

## 4.1 LSTM Classifier

Architecture:

Embedding Layer
→ LSTM Layer
→ Fully Connected Layer
→ Binary Classification

Properties:

* Sequential memory
* Captures temporal dependencies
* Vulnerable to vanishing gradients

---

## 4.2 GRU Classifier

Architecture:

Embedding Layer
→ GRU Layer
→ Fully Connected Layer
→ Binary Classification

Properties:

* Simplified recurrent architecture
* Fewer parameters than LSTM
* Often more stable during training

---

## 4.3 Transformer Encoder

Architecture:

Embedding Layer
→ Positional Encoding
→ Multi-head Self Attention
→ Feed Forward Layer
→ Classification Head

Properties:

* Parallel sequence processing
* Captures global token relationships
* Computationally expensive

---

# 5. Experimental Design

The experiments vary two key factors:

Dataset Size
Sequence Length

### Dataset Sizes Tested

1000 samples
5000 samples
10000 samples

### Sequence Lengths Tested

64 tokens
128 tokens
256 tokens

Each experiment trains and evaluates all three architectures under identical conditions.

---

# 6. Experimental Results

Final results obtained from the experiments:

| dataset_size | seq_len | lstm  | gru   | transformer |
| ------------ | ------- | ----- | ----- | ----------- |
| 1000         | 64      | 0.543 | 0.531 | 0.572       |
| 1000         | 128     | 0.541 | 0.508 | 0.594       |
| 1000         | 256     | 0.505 | 0.504 | 0.533       |
| 5000         | 64      | 0.618 | 0.610 | 0.664       |
| 5000         | 128     | 0.603 | 0.574 | 0.730       |
| 5000         | 256     | 0.513 | 0.527 | 0.748       |
| 10000        | 64      | 0.681 | 0.645 | 0.716       |
| 10000        | 128     | 0.547 | 0.646 | 0.762       |
| 10000        | 256     | 0.538 | 0.586 | 0.795       |

---

# 7. Key Observations

### Observation 1 — Transformers scale with dataset size

Transformer accuracy increased consistently as dataset size increased.

Example:

Dataset Size 1000 → Accuracy ≈ 0.57
Dataset Size 10000 → Accuracy ≈ 0.79

This suggests that **attention models benefit significantly from more data.**

---

### Observation 2 — Transformers benefit from longer sequences

For the largest dataset:

Sequence Length 64 → 0.716
Sequence Length 256 → 0.795

Longer context allows attention to capture **global relationships across tokens.**

---

### Observation 3 — LSTM struggles with long sequences

LSTM accuracy drops significantly with longer sequences.

Example:

5000 samples:

Sequence Length 64 → 0.618
Sequence Length 256 → 0.513

This behavior reflects known limitations of recurrent networks:

* vanishing gradients
* difficulty modeling long dependencies

---

### Observation 4 — GRU shows stable performance

GRU performance remains relatively stable across different sequence lengths.

This supports the idea that **GRU often provides a strong baseline for sequence modeling tasks.**

---

# 8. Inference Latency Experiment

In addition to accuracy, we measured inference latency.

Example results:

| Model       | Latency | Accuracy |
| ----------- | ------- | -------- |
| LSTM        | Medium  | Low      |
| GRU         | Fastest | Medium   |
| Transformer | Slowest | Highest  |

This demonstrates the **accuracy vs computational cost trade-off**.

---

# 9. Errors Encountered During Development

During the experimentation process several issues were encountered:

### Dataset formatting issues

Incorrect dataset formatting caused models to receive invalid tensors, leading to random predictions.

### Data leakage

Improper dataset slicing resulted in unrealistic accuracy values (1.0).

### Tokenization inconsistencies

Changing sequence lengths without reloading the dataset corrupted preprocessing pipelines.

### Training instability

Long sequences caused gradient instability in recurrent networks.

These issues were resolved by:

* reloading datasets for each experiment
* proper dataset shuffling
* careful tensor formatting
* controlled preprocessing pipelines

---

# 10. Final Conclusion

This study demonstrates that model performance depends strongly on **dataset size and sequence length**.

Key conclusions:

Transformers outperform recurrent models when:

* dataset size is sufficiently large
* sequence length is long
* global token relationships matter

Recurrent models remain competitive when:

* datasets are small
* sequence length is short
* computational efficiency is important

---

# 11. Key Takeaways

Transformer models provide the highest accuracy but incur higher computational cost.

GRU offers a strong balance between performance and efficiency.

LSTM can struggle with long sequence dependencies.

The choice of architecture should depend on:

* dataset size
* sequence length
* latency constraints
* available compute resources

---

# 12. Technologies Used

PyTorch
HuggingFace Datasets
Transformers Tokenizer
Scikit-learn
Matplotlib

---

# 13. Future Improvements

Possible extensions to this project include:

* attention visualization
* hyperparameter optimization
* larger transformer architectures
* additional datasets

---

# 14. Author

Deep Learning Portfolio Project

Focus: sequence modeling, architecture comparison, and empirical ML research.
