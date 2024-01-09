## Study Guide

#### Topics
1. AI security

#### Questions



### AI/ML
1. What are some mitigations against evasion attacks against ML?
**Expected Answer**: 
   1. Adversarial training
   2. Randomized smoothing
   3. Formal verification


1. What is adversarial training for ML and what are the trade-offs?
**Expected Answer**: Adversarial training is a general method that augments the training data with adversarial examples generated iteratively during training using their correct labels. The stronger the adversarial attacks for generating adversarial examples are, the more resilient the trained model becomes. Interestingly, adversarial training results in models with more semantic meaning than standard models, but this beneft usually comes at the cost of decreased model accuracy on clean data. Additionally, adversarial training is expensive due to the iterative generation of adversarial examples during training.

1. What is randomized smoothing for ML and what are the trade-offs?
**Expected Answer**: Randomized smoothing enhances the model's robustness against adversarial attacks, particularly ℓ2-norm bounded perturbations. This means the classifier is less likely to be fooled by small, carefully crafted changes to the input data (adversarial attacks). The robustness is "certifiable," implying a certain level of assurance against these attacks within a defined perturbation radius. The trade-off comes in the form of reduced precision or certainty in predictions across all samples. While the method provides certified robust predictions, it may only do so for a subset of testing samples. It might not maintain the same level of accuracy or confidence for every possible input as a standard classifier would.

1. What is formal verification for ML and what are the trade-offs?
**Expected Answer**:  Formal verification methods, like Reluplex and AI2, use mathematical techniques to prove whether a neural network is robust against certain types of adversarial attacks within predefined constraints. This approach provides a theoretical guarantee of security but is limited by a lack of scalability (meaning they are challenging to apply to large or complex networks), high computational cost, and restrictions on the types of operations they can verify within a network. These limitations make it difficult to apply formal verification universally across all neural network architectures and applications