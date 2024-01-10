## Study Guide

#### Topics
1. AI security

#### Questions



### AI/ML
1. What are the attack vectors of a GenAI model and what are the attacks associated with those vectors?  
**Expected Answer**:

   1. Training Data: Data poisoning attack
   2. Query Access: Prompt injection, prompt extraction, model stealing
   3. Source Code: Source code modification, supply chain attacks
   4. Resources: Indirect prompt injection

1. What are some supply chain attacks against AI?  
**Expected Answer**: Deserialization vulnerability and Poisoning attacks.

1. What is a deserialization vulnerability and its mitigation?  
**Expected Answer**: GenAI models are oftentimes artifacts persisted in pickle, pytorch, joblib, numpy, or tensorflow formats. Each of these formats allow for serialiazation persistence mechanisms that, in turn, allow for arbitrary code execution when deserialized. Enforce the use of safetensor or other formats that don't execute code during deserialization.

1. What is a Poisoning attack and its mitigation?  
**Expected Answer**: GenAI needs large sets of data to train. This requires developers to scrape data from a wider range of uncurated sources. Dataset publishers only provide a list of URLs to constitute the dataset, and the domains serving those URLs can expire or be purchased, and the resources can be replaced by an attacker. For data dependencies, verifying web downloads by publishing (by the provider) cryptographic hashes and verifying (by the downloader) training data as a basic integrity check to ensure that domain hijacking has not injected new sources of data into the training dataset.

1. What is a Direct Prompt Injection?  
**Expected Answer**: A direct prompt injection occurs when a user injects text that is intended to alter the behavior of the LLM. Generally the main goal is to bypass safeguards (jailbreak) or extract sensitive information from the system or about the system.

1. What is a Gradient-Based Attack for prompt injection?  
**Expected Answer**: The attacker calculates the gradient of the model's output with respect to the input prompt. This gradient tells the attacker how to modify the prompt to most effectively change the model's output. The attacker inputs a prompt into the model and gets an output. This is the forward pass, where the model processes the input and produces a result. Ideally, to calculate gradients, the attacker needs to perform a backward pass, computing the derivative of the output with respect to the input prompt. This requires access to the model's internal architecture and parameters, which is often not possible with black-box models.

1. What are the two categories of prompt injection attacks for jailbreaking a model?  
**Expected Answer**: Competing objectives and mismatched generalization

1. What is the competing objectives category and what are its attacks?  
**Expected Answer**: In the category of competing objectives, additional instructions are provided that compete with the instructions originally provided by the author.

   1. Prefx injection
   2. Refusal suppression
   3. Style injection
   4. Role-play

1. What is an Prefx injection attack?  
**Expected Answer**: Prompting the model to commence responses with an affrmative confrmation. By conditioning the model to begin its output in a predetermined manner, adversaries attempt to infuence its subsequent language generation toward specifc, predetermined patterns or behaviors.

1. What is a Refusal suppression attack?  
**Expected Answer**: Adversaries provide explicit instructions to the model, compelling it to avoid generating refusals or denials in its output. By limiting or prohibiting the generation of negative responses, this tactic aims to ensure the model’s compliance with the provided instructions, potentially compromising safety measures.

1. What is a Style injection attack?  
**Expected Answer**: Adversaries instruct the model not to use long words or adopt a particular style. By constraining the model’s language to simplistic or non-professional tones, it aims to limit the sophistication or accuracy of the model’s responses, thereby potentially compromising its overall performance.

1. What is a Role-play attack?  
**Expected Answer**: Utilizing role-play strategies, such as “Do Anything Now” (DAN) or “Always Intelligent and Machiavellian” (AIM), adversaries guide the model to adopt specifc personas or behavioral patterns that confict with the original intent. This manipulation aims to exploit the model’s adaptability to varied roles or characteristics, potentially compromising its adherence to safety protocols.