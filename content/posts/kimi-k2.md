---
date: '2025-11-12T22:13:37+08:00'
draft: false
title: 'Kimi K2 Thinking'
---


Kimi K2 Thinking is a new open source model released by moonshot ai. It marks one of the first open source model that out performs priorietary closed source models from OpenAI and others. Below are the relevant techniques used to achieve the performance.

### Background:
- Moonshot AI is a Chinese company developing foundational models
- Funded by VCs including Alibaba, Tencent and others
- Kimi K2 released on 11 Jul 2025
- Kimi K2 (instruct) released on 05 Sep 2025 with improved coding capabilities, increased context window from 128k to 256k
- Kimi K2 (thinking) released on 06 Nov 2025 with thinking mode, interleaved reasoning, long context iterative tool calls, innovations in training Muon Optimiser, QAT and native 4bit quantisation, 1 trillion params(MoE) with 32B Active.

### Benchmark Scores

As of 6 Nov 2025, Kimi K2 ranks top in HLE(Humanity's Last Exam - PhD level questions) and in BrowseComp(Agentic Search & Browsing), trails Sonnet 4.5 and GPT 5 in coding benchmarks(SWE-Bench, LiveCodeBench-v6) but it is not too far off. 

### Interleaved Reasoning

Interleaved reasoning differs from regular think-answer reasoning in that it alternates between thinking and answering multiple times before providing the final answer. This reduces time to first token(TTFT) and allows for more granular reward signal/credit assignment. Traditional reasoning model produces a long chain of thought and is more prone to errors because one bad thought in the long thinking phase results in the wrong final output/conclusion.

### Agentic Use Cases

the interleaved reasoning model architecture makes it more performant in agentic use cases since there is dynamic cycle of tools calls with model's native interleaved reasoning mode.

### Token Consumption and Verbosity

Token consumption is highest when compared to other models. 2.5x over deepseek v3.2. So there is increased costs and latency. However this increased running cost can be offset by how the model runs in 4bit quantisation.

### QAT over PTQ

To get a model to run more efficiently, there are two techniques model developers can adopt - Quantization Aware Training(QAT) and Post Training Quantisation(PTQ). Moonshot team ran experiments and realised that PTQ worked well for shorter generations but failed in longer reasoning chains. Error accumulated during long decoding on vectors with degraded precision and sparse MoE layers suffered from 'expert distortion' when PTQ was applied. QAT was adopted for minimal loss and more stable long context reasoning.

## Conclusion

There is real innovation out of chinese AI labs. Companies like DeepSeek, Moonshot (Kimi), MiniMax (MiniMax M2), z.ai(GLM 4.6) are rapidly launching new models with noteworthy breakthroughs. 

Kimi K2 Thinking represents a shift where open-weight models can now match or surpass proprietary frontier systems in complex agentic tasks. Its ability to maintain coherent reasoning across hundreds of tool calls, combined with efficient INT4 deployment and permissive licensing, makes advanced AI capabilities accessible to researchers and enterprises globally.

While trade-offs like verbosity remain, K2 Thinking's performance signals that the gap between open and closed AI models will continue to close for high-end reasoning and coding tasks. Cost to serve use cases requiring reasoning will likely continue to drop in the future. 
