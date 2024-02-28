# CSE576_Augmenting_Attention_Mechanism

The attention mask in Transformer models either has a value of 1 when attention needs to be applied to the token or 0 when the token is padding. This form of Hard-Attention works well in most cases, but considering the difficulty for language models to understand logical reasoning samples, we instead try a form of Explainable Attention Mask mechanism.

In our approach, we obtain word importance for sample predictions using a well-performing model using explainability libraries using LIME (Local Interpretable Model-Agnostic Explanations). These word importance values are then normalized between 0 and 1.

```Proposed Attention Mask = Attention Mask * Normalized Word Importance```

![Proposed Attention Mask Mechanism]([https://github.com/[username]/[reponame]/blob/[branch]/image.jpg?raw=true](https://github.com/msakthiganesh/CSE576_Augmenting_Attention_Mechanism/blob/main/proposed_mechanism.png?raw=true))


Furthermore, the normalized word importance for the correctly predicted training and validation datasets is fed directly as the attention mask, whereas the word importance is inverted (1 - normalized word importance) for the samples predicted wrong.
We hypothesize that the baseline model (RoBERTa) would converge faster and would allow the model to understand important parts of the sentence better in order to make the correct predictions.
