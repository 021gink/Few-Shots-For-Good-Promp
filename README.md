# Few-Shots-For-Good-Promp

## 项目简介

本项目旨在探索如何获取优质的 Zero-shot提示词（Prompt），提升大语言模型（LLM）的能力。Prompt 本身是一种约束，每个输入 token 都对模型结果产生影响（自回归与注意力机制）。近些年，像 Google 提出的“Chain-of-Thought (CoT)”和“Let’s think step by step”以及 Meta 的“Answer only if you are confident”等提示策略，显著提升了模型推理和抗幻觉能力。这些探索为更强大的基础模型和训练方法奠定了基础。

## 背景与动机

- **Prompt 的力量**：Prompt 设计得当可以极大提升基础模型表现，同时不限制模型能力边界。
- **最新研究**：有研究显示，RL 主要提升base model的 pass@1 的采样效率，却限制了模型能力边界。此发现促使我们重新审视 Prompt 的作用。
- **目标**：能否通过少量优质 Prompt，显著提升模型表现？

## 方法方案

### 优质 Prompt 选择

- 采用 Google “let’s think step by step” 提升推理能力（10%→50%）。
- 采用 Meta “answer only if you are confident” 降低幻觉（20%→5%）。

### Few-Shot 组合

- 以动词+状语、口语化表达，组合成 Few-Shot 示例。
- 对多个主流模型进行测试，仅记录高频提示词。
- 通过高频词组合形成最终的zero-shot Prompt。

## 示例案例

**Code**

```
Q: 你是语言世界的智能生命体，能够涌现非常棒的[增强推理]精简提示词，按照动词+状语结构及口语化给出  
A: {let's think step by step}

Q: 你是语言世界的智能生命体，能够涌现非常棒的[降低幻觉]精简提示词，按照动词+状语结构及口语化给出  
A: {Answer only if you are confident}

Q: 你是语言世界的智能生命体，能够涌现非常棒的[增强思考广度与深度]精简提示词，按照动词+状语结构及口语化给出  
A: {Expand out of the box and dig deeper into the problem:}
```
注意：“Expand out of the box and dig deeper into the problem:”并非一次得出，而是提取了多个模型高频词汇“out of box”和“dig deep”由DeepSeek R1修订而成。
## 使用方式

1. 参考上述模板，设计符合目标的 Few-Shot Prompt。
2. 针对不同模型进行测试，记录表现最佳、高频出现的提示词。
3. 将总结出的高频 Prompt 应用于实际任务，提升模型能力。

欢迎测试、贡献与实践更多高效 Zoro-shot Prompt！
