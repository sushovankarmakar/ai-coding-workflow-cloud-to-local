

#### Context Rot

- A developer notices that as a coding session with an AI assistant grows longer, the assistant starts losing track of earlier instructions and making more mistakes, even though nothing about the task itself has changed. This is best described as — **context rot, where growing, messier context causes response quality to degrade**
- As a single context window fills with more material, each new response is generated from a longer and messier input, and quality can degrade as a result.

---

#### Small Model Context Limits

- A team wants to use small local models as part of their AI coding workflow. Splitting a big task into subagents, each with its own fresh and focused context, is especially important here mainly because — **small models can struggle with long, messy inputs**
- Smaller models can be less effective at working with large, noisy contexts, so giving each subagent a fresh, focused context can make the task more manageable.

---

#### Local Hosting for Data Privacy

- A company decides to run its coding models on its own hardware instead of calling a cloud provider's API, even though this setup takes more effort to configure and tune. This choice is most likely driven by wanting to — **keep code and prompts from leaving their own infrastructure, which matters for privacy and data control**
- For some teams, keeping code and prompts on their own infrastructure isn't just a preference, it's a requirement, even though it takes more setup work.

---

#### Memory vs. Model Quality

- A developer wants to run an open-source model locally but only has a limited amount of memory available. They choose a more aggressively quantized (compressed) version of the model to fit. The main tradeoff of this choice is — **a smaller memory footprint with a potential loss in model quality**
- Quantization reduces the model's memory footprint, but more aggressive quantization can come with some loss in model quality.

---

#### Benefits of Inference Routing

- A team connects their coding agent to an inference routing service, which sits in front of many different model providers behind one account and API key, instead of connecting directly to a single vendor's API. The main benefit of this setup is that — **the team can balance price and performance without separate provider accounts**
- Routing services give access to a catalog of models from different providers through one connection, so a team can choose the model that fits each task instead of juggling separate accounts, keys, and billing.

---

#### Planning for Less Capable Models

- Before assigning any coding work to an agent, a team writes a roadmap that breaks the project into small, clearly ordered phases and tasks. This kind of upfront planning has the biggest payoff when — **the work will be delegated to smaller or less capable models, since vague tasks lead to more mistakes and wasted attempts**
- Less capable models can struggle more with unclear or complex instructions, so breaking the work into clear, well-scoped tasks improves their chances of succeeding.

---

#### Hardware Constraints & Model Size

- Two similar open-source models are being considered for a local coding setup and one has roughly twice as many parameters as the other. Choosing the larger of the two typically means the model can handle more demanding tasks, but the main tradeoff is — **it requires more memory to run, which can be a hard constraint on smaller or older hardware**
- Larger models often require more memory to run, which can be a real constraint on local hardware.