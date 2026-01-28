---
title: "LUNAA 2.0"
date: 2024-04-07T14:30:00+08:00
draft: false
slug: lunaa2
description: "Teaching Reinforcement Learning agents when to trust human advice—and when to rely on their own policy."
summary: "Teaching Reinforcement Learning agents when to trust human advice—and when to rely on their own policy."
featured: true
tags:
  - Machine Learning
  - Reinforcement Learning
  - Human-AI
  - Interactive AI
  - Trustworthy AI
  
categories:
  - projects
cover: "lunaa2.png"
#github: "https://github.com"
#demo: "https://example.com"
#website: "https://example.com"
#paper: "https://example.com"
# tech_stack:
#   - Python
project_members: "Christian Maurer supervised by Lisa Kempf and Dorothea Koert"
status: "completed"
---

### Project Overview

Interactive Reinforcement Learning (IntRL) enables agents to learn faster by incorporating human action advice during training. However, many existing approaches assume that human advice is always correct or that its reliability is uniform across all states. In real-world scenarios, this assumption rarely holds---humans may give good advice in some situations and misleading advice in others.

This student research project investigates how an agent can reason about the reliability of both human advice and its own policy, and selectively decide when to follow or reject guidance. The result is a more robust IntRL algorithm that improves learning speed while remaining resilient to partially incorrect or inconsistent human input.

### Motivation

The strength of Interactive Reinforcement Learning lies in combining
- **human expertise**, and
- **autonomous decision-making** through Reinforcement Learning (RL).

However, in practice:
- Humans may lack knowledge in certain states
- Advice may be inconsistent or systematically wrong
- Blindly trusting advice can degrade performance

Most prior work addresses this by assigning a global trust level to the human teacher. This ignores the fact that advice quality is often state-dependent, which can lead to poor learning behavior in critical states.


### Approach

We propose a novel Interactive Reinforcement Learning algorithm that combines
- **state-dependent trust in human action advice**
- **state-dependent trust in the agent’s own policy**, derived from policy uncertainty.

The method builds upon the LUNAA algorithm and operates in environments modeled as **Markov Decision Processes (MDPs)**. We extend the approach by using a probabilistic RL method, called Bayesian Q-learning.
To efficiently use sparse human input, the agent learns a model of human advice, which:
- Captures advice given during interaction
- Predicts likely human actions when no explicit advice is provided

Since human advice can be partially incorrect, we compute trust in advice using three indicators:
- **Consistency** -- how stable the advice is across time
- **Retrospective optimality** -- how well advice aligns with observed outcomes
- **Behavioral cues** -- signals indicating confidence or hesitation


### Policy Uncertainty Estimation

In addition to evaluating human advice, the agent estimates its own uncertainty in each state. We introduce and compare five policy uncertainty measures, each producing a normalized uncertainty score per state.

These uncertainty estimates allow the agent to determine when:
- Its policy is reliable enough to act independently
- External guidance is likely to be beneficial


### Key Insights & Contributions

- Introduced state-dependent trust for both policy and human advice
- Demonstrated that policy uncertainty is critical for robust IntRL
- Showed how behavioral cues improve robustness against systematic wrong advice
- Identified uncertainty measures suitable beyond Bayesian RL, enabling potential transfer to classical algorithms such as Q-learning


### Publications

This work contributed to publications in the following venues:
- Kempf, L., Maurer, C., Turan-Schwiewager, C., & Koert, D. (2025). Can I Trust You? - Handling Unreliable Human Action Advice in Interactive Reinforcement Learning. ACM Transactions on Human-Robot Interaction. https://dl.acm.org/doi/full/10.1145/3736424
- Scherf, L., Maurer, C., & Koert, D. (2024). Combining State-Dependent Trust in Policy and
Human Advice for Interactive Reinforcement Learning. Presented at Human-Interactive Robot
Learning Workshop (HIRL), 19th Annual ACM/IEEE International Conference on Human Robot
Interaction (HRI)