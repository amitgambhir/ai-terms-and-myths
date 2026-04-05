# AI & Machine Learning Glossary

A practical reference for engineers, product managers, and technical leaders navigating the AI landscape. Terms are explained with precision — no jargon inflation, no hand-waving.

---

## A

### Activation Function
A mathematical function applied after each linear layer in a neural network to introduce non-linearity. Without it, stacking multiple layers would be mathematically equivalent to a single layer. Common examples include ReLU, GELU, and SiLU. The choice of activation function affects how well gradients flow during training.

### Adam (Optimizer)
Short for Adaptive Moment Estimation. An optimization algorithm that combines momentum-based updates with per-parameter adaptive learning rates. It includes bias correction for early training steps and works well across most tasks with minimal manual tuning.

### AdamW
A variant of Adam that decouples weight decay from the gradient update step. In standard Adam, L2 regularization interacts undesirably with the adaptive learning rate. AdamW fixes this by applying weight decay directly to the weights, independent of gradient statistics. It is the standard optimizer for training transformer models.

### Agent
An LLM-powered system that follows a repeated loop: reason about a task, decide which tool to use, execute it, observe the result, and repeat. The "intelligence" comes from the language model; the "autonomy" comes from the loop and the tools wired around it. Agents are not self-aware or goal-driven in any philosophical sense — they are well-engineered reactive systems.

### Alignment
The technical challenge of ensuring an AI system's behavior reliably matches human intentions and values — including edge cases, ambiguous situations, and scenarios the designers did not anticipate. Alignment is an active research area and is not considered a solved problem.

### Attention
A mechanism in transformer models that allows each token in a sequence to weigh the relevance of every other token before producing its output. Relevance is computed via dot products between learned query and key vectors. The result is a weighted combination of value vectors. Named by analogy to human selective attention, though the mechanism is purely mathematical.

### Autograd
A system built into deep learning frameworks (PyTorch, JAX) that automatically tracks operations on tensors and computes their gradients via reverse-mode differentiation. You write the forward pass; autograd handles all the derivative calculations needed for backpropagation.

### Autoregressive
Describes a model that generates output one token at a time, where each new token is conditioned on all previously generated tokens. The output is fed back as input for the next step. GPT, LLaMA, Mistral, and Claude are all autoregressive models.

---

## B

### Backpropagation
An algorithm for computing how much each weight in a neural network contributed to the prediction error. It applies the chain rule from calculus backwards through the network — from output to input — and produces gradients used to update weights. It is the engine behind how neural networks learn from data.

### Batch Size
The number of training examples processed together in a single forward and backward pass before the model's weights are updated. Larger batches produce more stable gradient estimates but require more memory. Batch size interacts with learning rate: doubling the batch size typically calls for a proportional increase in learning rate.

### Bias (AI)
Systematic patterns in AI outputs that unfairly favor or disadvantage certain groups, perspectives, or outcomes. Bias typically originates in training data — if the data over-represents certain demographics or viewpoints, the model reproduces and sometimes amplifies those skews. Bias can also be introduced through labeling decisions, evaluation metrics, or fine-tuning objectives. Detecting bias requires targeted evaluation across demographic groups, not just aggregate accuracy scores. For practitioners, bias is an engineering and product concern: unaddressed bias leads to discriminatory outputs, regulatory risk, and eroded user trust.

### BLEU Score
Bilingual Evaluation Understudy. A metric for evaluating machine-generated text (especially translation) by measuring n-gram overlap with one or more reference outputs. BLEU is fast to compute but only captures surface-level similarity — two responses with the same meaning but different wording may score poorly.

---

## C

### Chain of Thought (CoT)
A prompting technique where the model is asked to reason through a problem step by step before producing a final answer. Because each step conditions the next token, explicit reasoning often improves accuracy on multi-step or logical tasks. Can be elicited with simple instructions like "think step by step."

### Chunking
The process of splitting documents into smaller segments before embedding them for retrieval. Chunk size controls the granularity of search results: too small loses contextual meaning; too large dilutes relevance. Common strategies include fixed-size with overlap, sentence-based, and semantic splitting. Typical sizes range from 256 to 512 tokens with 10–20% overlap.

### CNN (Convolutional Neural Network)
A neural network architecture designed for grid-structured data like images. It applies sliding filters (convolutions) across the input to detect local patterns — edges at lower layers, textures and shapes at higher layers. CNNs remain widely used in production vision systems despite the rise of Vision Transformers, particularly on mobile and edge devices where inference speed matters.

### Context Window
The maximum number of tokens — input plus output — that a model can process in a single API call. It is not persistent memory. When the conversation exceeds this limit, older content is dropped. A larger context window does not guarantee equal attention across all positions.

### Contrastive Learning
A training approach that teaches a model by pulling representations of similar items closer together in vector space while pushing dissimilar items apart. CLIP uses this to align image and text embeddings by contrasting matched image-text pairs against unmatched ones.

### Cosine Similarity
A measure of directional similarity between two vectors, calculated as the cosine of the angle between them. Ranges from -1 (opposite directions) to 1 (identical directions). Ignores vector magnitude, making it suitable for comparing embeddings regardless of length. The standard similarity metric for semantic search and retrieval.

### Cross-Entropy Loss
A loss function that measures the difference between a predicted probability distribution and the true distribution. For classification, it penalizes confident wrong predictions heavily. For language models, it is the negative log probability of the correct next token. Perplexity is simply the exponent of cross-entropy loss.

### CUDA
NVIDIA's parallel computing platform that enables code to run across thousands of GPU cores simultaneously. PyTorch and TensorFlow use CUDA under the hood for matrix operations. Writing CUDA-native code is rarely needed in practice, but understanding its role helps in debugging GPU memory and performance issues.

---

## D

### Data Augmentation
The practice of generating modified versions of existing training examples — rotated images, paraphrased sentences, added noise — to increase dataset diversity without collecting new data. Reduces overfitting and improves generalization.

### Decoder
In transformer architecture, a module that uses masked (causal) self-attention, meaning each position can only attend to earlier positions. This makes decoders well-suited for text generation. GPT models are decoder-only. BERT is encoder-only. T5 uses both an encoder and a decoder.

### Diffusion Model
A generative model trained to reverse a gradual noising process. During training, the model learns to predict and remove small amounts of noise added to data. At inference time, it starts from pure noise and iteratively denoises until a coherent output emerges. The basis for image generation systems like Stable Diffusion and DALL·E.

### DPO (Direct Preference Optimization)
A training technique that aligns a language model to human preferences without requiring a separately trained reward model. Instead of using reinforcement learning, DPO directly optimizes the model's weights to favor preferred responses over less preferred ones using paired human feedback data.

### Dropout
A regularization technique that randomly sets a fraction of activations to zero during training, preventing the network from over-relying on any single neuron. Dropout is turned off during inference. Simple, widely used, and effective across model types.

---

## E

### Embedding
A learned mapping that converts discrete items — words, documents, images, users — into dense numerical vectors in a continuous space. Items that are semantically similar end up geometrically close in this space. Embeddings are foundational to semantic search, recommendation systems, and retrieval-augmented generation.

### Encoder
In transformer architecture, a module that uses bidirectional self-attention, allowing each token to attend to all other tokens in both directions. Well-suited for understanding and classification tasks. BERT is encoder-only. Unlike decoders, encoders do not generate text — they produce rich representations of input.

### Epoch
One complete pass through the entire training dataset. Training typically runs for multiple epochs. More epochs can improve model performance but increase the risk of overfitting if not managed with regularization or early stopping.

### Explainability (XAI)
The field of methods and tools that make model decisions interpretable to humans. Techniques include attention visualization, saliency maps, SHAP values, and probing classifiers. Explainability is distinct from interpretability: explainability provides post-hoc reasoning; interpretability refers to models that are transparent by design (e.g., decision trees).

---

## F

### Feature
An individual measurable property used as input to a model. In classical machine learning, features are hand-engineered by domain experts. In deep learning, the network learns feature representations automatically from raw data.

### Few-Shot Prompting
Providing a small number of input-output examples in the prompt before the actual task, allowing the model to infer the desired pattern or format. Typically 2–5 examples. Distinct from fine-tuning, which bakes behavior into model weights through additional training.

### Fine-Tuning
Continuing the training of a pre-trained model on a smaller, task-specific dataset. Fine-tuning adjusts the model's existing weights to better suit a particular use case. It does not add new factual knowledge — it changes behavior, style, and format.

### Function Calling
A structured capability that allows language models to request execution of external functions. You define available tools with typed schemas; the model outputs a structured object specifying which function to call and with what arguments; your application executes it and returns the result. The mechanism that powers tool-using agents.

---

## G

### Generative AI
AI systems that create new content — text, images, code, audio, video — rather than just classifying or analyzing existing data. The term covers a broad family of architectures including autoregressive language models (GPT, Claude), diffusion models (Stable Diffusion, DALL·E), and GANs. Most modern generative AI is built on the transformer architecture. The practical distinction matters: generative models produce outputs that did not exist before, which introduces risks like hallucination and copyright concerns that purely analytical AI does not face.

### GAN (Generative Adversarial Network)
An architecture consisting of two competing networks: a generator that creates synthetic data and a discriminator that tries to distinguish real from fake. Adversarial training drives both networks to improve simultaneously. GANs were the dominant generative approach before diffusion models.

### GPT (Generative Pre-trained Transformer)
A decoder-only transformer architecture trained on large text corpora using next-token prediction. Generative refers to its ability to produce text; Pre-trained means it was trained once on a massive dataset before task-specific adaptation; Transformer is the underlying architecture. GPT-style models are the basis for most modern chat AI systems.

### Gradient
A vector of partial derivatives that indicates the direction and rate of steepest increase of a function with respect to its inputs. In machine learning, gradients are computed with respect to the loss function. Training moves parameters in the opposite direction of the gradient — hence gradient descent.

### Gradient Descent
An optimization algorithm that updates model parameters iteratively in the direction that reduces the loss function most steeply. Conceptually similar to descending a mountain by always stepping in the downhill direction. Variants include stochastic gradient descent (SGD), mini-batch gradient descent, and adaptive methods like Adam.

### Guardrails
Input and output validation layers that wrap a language model to detect and block harmful, off-topic, or policy-violating content. Can be rule-based (keyword filters, regex) or model-based (classifiers scoring safety). A production AI system typically includes input filtering, the core model, and output filtering as separate, composable layers.

---

## H

### Hallucination
When a model generates plausible-sounding text that is factually incorrect or not grounded in its context or training data. Hallucinations occur because language models are trained to produce statistically likely text, not to verify factual accuracy. They are a fundamental characteristic of autoregressive generation, not a bug to be fully patched.

### Hyperparameter
A configuration value set before training that governs the training process itself — learning rate, batch size, number of layers, dropout rate. Unlike model parameters (weights), hyperparameters are not learned from data; they are chosen by the practitioner.

---

## I

### Inference
Using a trained model to generate predictions or outputs on new data. No weight updates occur during inference. Inference is what runs in production. Optimizing inference — through quantization, batching, caching, and hardware selection — is a major engineering discipline in AI deployment.

### Inductive Bias
The set of assumptions baked into a model's architecture that shape what it can learn efficiently. CNNs assume local spatial patterns matter. RNNs assume sequential order is important. Transformers assume any position might be relevant to any other. Choosing an architecture with the right inductive bias for your data improves sample efficiency.

---

## J

### JAX
A numerical computing library from Google that adds automatic differentiation, JIT compilation, and multi-device parallelism to NumPy-style code. Unlike PyTorch's object-oriented approach, JAX is purely functional — no hidden state, no in-place mutation. Used by Google DeepMind for large-scale research including AlphaFold and Gemini.

---

## K

### KV Cache
A performance optimization for autoregressive inference. During text generation, the model caches the key and value matrices computed for each previous token, avoiding redundant recomputation at every step. Trades memory for inference speed. Essential for low-latency production LLM systems.

---

## L

### Latent Space
A compressed, learned representation space where similar inputs are mapped to nearby points. Autoencoders, VAEs, and diffusion models all operate in latent space. It is lower-dimensional than the raw input but captures the essential structure of the data in a form the model can manipulate.

### Learning Rate
A scalar that controls the step size taken during each gradient descent update. Too high and training overshoots and diverges. Too low and training is slow or gets stuck. The learning rate is generally considered the most important hyperparameter to tune. Learning rate schedules (warmup, cosine decay) are standard practice in transformer training.

### LLM (Large Language Model)
A transformer-based neural network with billions of parameters, trained on internet-scale text data to predict the next token in a sequence. The scale of data and compute produces emergent capabilities — instruction following, reasoning, code generation — that were not explicitly programmed. Not all LLMs are equal: architecture, data quality, and training methodology matter as much as raw size.

### LoRA (Low-Rank Adaptation)
A parameter-efficient fine-tuning technique that adds small, trainable low-rank matrices alongside the frozen weights of a pre-trained model. Only these small matrices are updated during fine-tuning, reducing memory and compute requirements by 10–100x compared to full fine-tuning with minimal performance loss.

### Loss Function
A function that quantifies the gap between a model's predictions and the correct output. Training minimizes this function. Common examples: mean squared error for regression, cross-entropy for classification, contrastive loss for embeddings. The loss function operationally defines what "correct" means for the model.

---

## M

### MCP (Model Context Protocol)
An open protocol that standardizes how AI applications connect to external data sources, tools, and services using typed JSON-RPC schemas. MCP enables modular, interoperable AI systems where models can invoke tools across different providers without custom integration for each one.

### Mixed Precision Training
A training strategy that uses 16-bit floating point (float16 or bfloat16) for most computations — which is faster and more memory-efficient — while keeping 32-bit precision for gradient accumulation and weight updates where numerical stability matters. Delivers approximately 2x speedup with negligible accuracy impact.

### MoE (Mixture of Experts)
An architecture where the model contains many specialized "expert" subnetworks. A learned routing mechanism selects a small subset of experts for each input, so the model's total parameter count is large but each forward pass is computationally cheap. Used in Mixtral and reportedly in GPT-4.

---

## N

### Normalization
The process of adjusting activation values to a standard range or distribution to stabilize training and enable higher learning rates. Batch normalization normalizes across examples in a batch. Layer normalization normalizes across the feature dimension within each example. Layer norm is standard in transformer architectures.

---

## O

### Optimizer
An algorithm that uses computed gradients to update model parameters. SGD is the simplest. Adam and AdamW are the most common in practice. Optimizers differ in convergence speed, memory requirements, and sensitivity to hyperparameter choices.

### Overfitting
When a model learns the training data so precisely that it performs poorly on new, unseen data. The model memorized noise rather than generalizing the underlying patterns. Common remedies: more training data, regularization techniques (dropout, weight decay), early stopping, and data augmentation.

---

## P

### Parameter
A single learnable value inside a model — typically a weight or bias. "A 7B parameter model" contains 7 billion such values. In float32 precision, each parameter takes 4 bytes of memory, so a 7B model requires roughly 28GB just to store the weights. Parameter count is a rough proxy for model capacity, not intelligence.

### Perplexity
A measure of how well a language model predicts a sample of text. It is the exponent of the average cross-entropy loss. Lower perplexity means the model assigns higher probability to the correct tokens — it is less "surprised" by the text. Used as an intrinsic evaluation metric for language models.

### Pre-training
The initial training phase where a model learns general patterns from massive amounts of data — typically internet-scale text for language models. During pre-training, the model learns syntax, facts, reasoning patterns, and world knowledge by predicting the next token across trillions of examples. This phase is by far the most expensive, often costing millions of dollars in compute. The result is a base model that understands language broadly but does not yet follow instructions or behave helpfully — that comes from subsequent fine-tuning and alignment.

### Precision & Recall
Two complementary evaluation metrics. Precision measures the fraction of predicted positives that are actually correct. Recall measures the fraction of actual positives that were correctly identified. They trade off against each other. F1 score is their harmonic mean. Use precision when false positives are costly; prioritize recall when false negatives are costly.

### Prompt
The complete input given to a language model for a single request. A prompt includes everything the model sees before generating a response: system instructions, conversation history, retrieved documents, user message, and any formatting directives. In API usage, prompts are structured as typed message arrays (system, user, assistant roles). Token count and ordering within the prompt directly affect model behavior, cost, and quality.

### Prompt Engineering
The practice of designing input text — including system prompts, instructions, few-shot examples, and output format specifications — to reliably elicit desired model behavior. Effective prompt engineering requires understanding tokenization, attention patterns, context window limits, and model-specific behaviors. It is a systems design discipline, not just conversational skill.

### Prompt Injection
An attack in which malicious text in the model's input overrides its instructions or system prompt. Direct injection occurs when a user explicitly attempts to override instructions. Indirect injection occurs when a retrieved document or tool output contains hidden instructions. No complete defense exists; mitigation relies on layered input validation, output filtering, and privilege separation.

---

## Q

### QLoRA (Quantized LoRA)
A memory-efficient fine-tuning technique that combines 4-bit quantization of the frozen base model with LoRA adapters trained in 16-bit precision. Reduces memory requirements by 3–4x compared to standard LoRA. A 7B model that requires 14GB with LoRA can fit in 4–6GB with QLoRA, with quality within ~1% of full fine-tuning on most benchmarks.

### Quantization
The process of reducing the numerical precision of model weights — from float32 (4 bytes) to int8 (1 byte) or int4 (0.5 bytes). Reduces memory footprint by 4–8x and speeds up inference, at a small cost to accuracy. Common formats include GPTQ, AWQ, and GGUF.

---

## R

### Reasoning Models
A category of language models specifically designed to perform multi-step reasoning before producing a final answer. These models generate an internal chain of thought — sometimes visible, sometimes hidden — that breaks complex problems into intermediate steps. Examples include OpenAI's o1 and o3 series and Anthropic's Claude with extended thinking. Reasoning models show significant improvements on math, logic, and coding benchmarks compared to standard models of similar size. The tradeoff is higher latency and token cost, since the reasoning trace consumes output tokens even when hidden from the user.

### RAG (Retrieval-Augmented Generation)
An architectural pattern for grounding LLM responses in external knowledge. At query time, relevant documents are retrieved from a knowledge base using embedding similarity, injected into the prompt as context, and the model generates its response based on that context. Preferred over fine-tuning when the goal is to incorporate specific, updatable factual knowledge.

### ReLU (Rectified Linear Unit)
The simplest widely used activation function: f(x) = max(0, x). Fast to compute, does not saturate for positive values, and works across most architectures. Common variants include LeakyReLU (allows small negative values), GELU (smoother approximation), and SiLU.

### RLHF (Reinforcement Learning from Human Feedback)
A training pipeline used to align language models with human preferences. It involves three steps: collecting human preference judgments on model outputs, training a reward model on those preferences, and using reinforcement learning (typically PPO) to optimize the language model to produce higher-reward responses. The technique behind instruction-following and helpfulness in most production chat models.

### ROUGE
Recall-Oriented Understudy for Gisting Evaluation. A set of metrics for evaluating generated summaries by measuring overlap with reference text. ROUGE-1 counts unigram matches, ROUGE-2 counts bigrams, ROUGE-L finds the longest common subsequence. Fast and widely used, but only captures surface-level similarity.

---

## S

### Scaling Laws
Empirical observations that model performance improves predictably as compute, dataset size, and parameter count increase. Kaplan et al. (2020) first quantified these power-law relationships for language models. The Chinchilla paper (Hoffmann et al., 2022) refined them, showing that most large models were over-parameterized relative to their training data — training a smaller model on more data yields better performance per compute dollar. Scaling laws guide decisions about model size, training budget, and data collection. They also predict emergent capabilities: abilities that appear suddenly at certain scale thresholds without being explicitly trained.

### Self-Attention
The core computation in transformer models. Each token produces query, key, and value vectors. The attention weight between any two tokens is computed as the scaled dot product of their query and key vectors, passed through a softmax. The output for each token is a weighted sum of all value vectors. This allows every token to incorporate information from every other token in a single operation.

### Semantic Search
Retrieval based on meaning rather than keyword matching. A query and all candidate documents are embedded into the same vector space, and documents closest to the query embedding are returned. "payment failed" can retrieve "transaction declined" even with no shared words. Powered by embedding models and vector databases.

### SFT (Supervised Fine-Tuning)
Fine-tuning a pre-trained base model on curated (instruction, response) pairs to teach it to follow instructions and produce helpful, formatted outputs. SFT is typically the first step in transforming a base model into a chat model, before alignment techniques like RLHF or DPO.

### Softmax
A function that converts a vector of arbitrary real numbers into a valid probability distribution — all values are positive and sum to 1. Used in classification output layers, attention weight computation, and anywhere a probability over discrete choices is needed. Temperature scaling is applied to logits before softmax to control output randomness.

### Streaming
Sending model output tokens to the client as they are generated, rather than waiting for the full response to complete. Uses Server-Sent Events (SSE) or WebSocket protocols. Dramatically reduces perceived latency — the user sees the first token in milliseconds rather than waiting seconds. Standard in production chat interfaces.

### Swarm (Multi-Agent)
A system of multiple AI agents that coordinate through shared state and message passing. Emergent behavior arises from simple individual rules rather than centralized control. Useful for parallelizing complex tasks across specialized agents, though coordination overhead and error propagation are real engineering challenges.

### System Prompt
A privileged instruction block processed at the start of a conversation, set by the application developer rather than the end user. Defines the model's persona, behavior constraints, output format preferences, and domain boundaries. Typically not visible to the user in production interfaces. Effectively the API contract between the developer and the model.

---

## T

### Temperature
A scalar applied to model logits before the softmax step, controlling the randomness of token selection. Higher temperature flattens the probability distribution, making less likely tokens more probable — increasing output variability. Lower temperature sharpens the distribution, making outputs more deterministic. Temperature = 0 is equivalent to always selecting the highest-probability token.

### Tensor
The fundamental data structure in deep learning frameworks. A generalization of scalars, vectors, and matrices to arbitrary dimensions. All model inputs, outputs, weights, and gradients are tensors. Frameworks like PyTorch and JAX track tensor operations automatically for gradient computation and can execute them on GPU or specialized hardware.

### Token
The basic unit of text that language models process. Produced by a tokenizer (commonly Byte Pair Encoding), tokens typically correspond to subword units — roughly 3–4 characters in English. One word may be one token or several. Understanding tokenization matters for prompt design, cost estimation, and debugging unexpected model behavior.

### Transfer Learning
Adapting a model pre-trained on one large task to a different, typically smaller task. Early layers in deep networks learn general representations (edges, syntax, semantics) that transfer across tasks. Later layers are task-specific and require adaptation. Transfer learning is why you can fine-tune a general-purpose model for a specialized domain with relatively little data.

### Transformer
The dominant neural network architecture in modern AI. Processes input sequences using self-attention, allowing every position to relate to every other position simultaneously. Unlike recurrent models, transformers parallelize over the full sequence, enabling training on massive datasets at scale. Introduced in the 2017 paper "Attention Is All You Need."

---

## U

### Underfitting
When a model is too simple to capture the patterns in the training data. Training loss remains high. Remedies include increasing model capacity (more layers or parameters), training longer, or reducing regularization.

---

## V

### VAE (Variational Autoencoder)
A generative model that learns a structured latent space by training the encoder to produce a probability distribution (typically Gaussian) rather than a fixed vector. Sampling from this distribution and decoding produces new data. The reparameterization trick makes the sampling step differentiable, enabling end-to-end training via backpropagation.

### Vector Database
A database optimized for storing high-dimensional dense vectors and performing fast approximate nearest-neighbor (ANN) search. The core infrastructure component for semantic search, RAG pipelines, and recommendation systems. Examples include Pinecone, Weaviate, Qdrant, and pgvector.

---

## W

### Weight
A single learnable parameter in a model — one number in a parameter matrix. Training adjusts weights to minimize the loss function. The full set of weights encodes everything the model has learned from training data.

### Weight Decay
A regularization technique that adds a penalty proportional to the magnitude of model weights to the loss function. Equivalent to L2 regularization. Prevents weights from growing excessively large, which can lead to overfitting. Typical values range from 0.01 to 0.1.

---

## Z

### Zero-Shot
Using a model on a task without providing any task-specific examples in the prompt. The model generalizes from patterns learned during pre-training. Effective for large models that have seen enough variety of tasks. Contrasts with few-shot (examples in the prompt) and fine-tuning (examples baked into weights).

---

*Last updated: April 2026 | Contributions welcome*
