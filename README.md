### Calculate Perplexity

Perplexity is calculated as \( P = 2^h \) where \( h \) is the entropy of the sequence. Entropy is calculated as the average negative log probability of each word in the sequence. The expression \( 2^h \) is used to convert entropy to a perplexity value.

#### Pretrained Language Model → Bigram Model

**Example Sequence:** I love to eat ice cream.

1. **Preprocess (Tokenize)**
    ```markdown
    [I, love, to, eat, ice cream]
    ```

2. **Calculate the Negative Log Probability**
    - \( P(I) = \text{Probability of 'I' according to the language model} \)
    - \( P(\text{love} \mid I) = \text{Probability of 'love' given 'I'} \)
    - \( P(\text{to} \mid \text{love}) = \text{Probability of 'to' given 'love'} \)
    - \( P(\text{eat} \mid \text{to}) = \text{Probability of 'eat' given 'to'} \)
    - \( P(\text{cream} \mid \text{ice}) = \text{Probability of 'cream' given 'ice'} \)

    - \( \log P(I) = -\log(P(I)) \)
    - \( \log P(\text{love} \mid I) = -\log(P(\text{love} \mid I)) \)
    - \( \ldots \)
    - \( \log P(\text{cream} \mid \text{ice}) = -\log(P(\text{cream} \mid \text{ice})) \)

3. **Calculate the Entropy**
    - \( \text{Entropy} = \frac{1}{n} \sum \log P(\text{word}_{i} \mid \text{word}_{i-1}), \text{ where } n=6 \)

---

### Calculate Burstiness

Burstiness measures the deviation of word occurrences from the average frequency in a text.

**Example Sequence:** The cat sat on the mat. The mat was soft.

1. **Tokenize**
    ```markdown
    [The, cat, sat, on, the, mat, The, mat, was, soft]
    ```

2. **Calculate Frequency**

    | Word  | Frequency |
    |-------|-----------|
    | The   | 3         |
    | cat   | 1         |
    | sat   | 1         |
    | on    | 1         |
    | mat   | 2         |
    | was   | 1         |
    | soft  | 1         |

3. **Calculate Average Frequency**
    - \( \text{Total Word Count (TWC)} = 10 \)
    - \( \text{Total Distinct Words (TDW)} = 7 \)
    - \( \text{Average Frequency} = \frac{\text{TWC}}{\text{TDW}} = \frac{10}{7} = 1.43 \)

4. **Calculate Burstiness**
    - \( \text{Variance of word frequency (V)} = \frac{\sum (\text{freq} - \text{avg. freq})^2}{\text{TDW}} \)
    - \( \text{For the given example, } V = 0.74 \)
    - \( \text{Burstiness Score} = \frac{V}{(\text{AF})^2} = \frac{0.74}{(1.43)^2} = 0.37 \)
    - \( \text{Burstiness Score} \in [0,1] \)

---

It is difficult to detect AI content from a closed-source model because the model architecture and training details are unknown.
