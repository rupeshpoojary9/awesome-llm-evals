# Awesome LLM Evals [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of frameworks, benchmarks, and research for evaluating large language models and LLM-powered systems.

Shipping an LLM feature is easy. Knowing whether it actually works, and proving it still works after the next change, is the hard part. This list collects the tools and reading that make LLM evaluation rigorous: unit-test-style eval frameworks, LLM-as-judge methods, RAG and agent evaluation, safety and red-teaming, observability, and the benchmarks the field is actually measured against.

Curated by [Rupesh Poojary](https://github.com/rupeshpoojary9). Contributions welcome.

## Contents

- [Why Evaluate](#why-evaluate)
- [Evaluation Frameworks and Libraries](#evaluation-frameworks-and-libraries)
- [LLM-as-a-Judge](#llm-as-a-judge)
- [RAG Evaluation](#rag-evaluation)
- [Agent and Tool-Use Evaluation](#agent-and-tool-use-evaluation)
- [Safety, Red-Teaming and Guardrails](#safety-red-teaming-and-guardrails)
- [Observability and Tracing](#observability-and-tracing)
- [Benchmarks and Datasets](#benchmarks-and-datasets)
- [Leaderboards](#leaderboards)
- [Key Papers](#key-papers)
- [Guides and Articles](#guides-and-articles)

## Why Evaluate

LLMs are non-deterministic, and small prompt or model changes cause silent regressions that unit tests never catch. A real evaluation setup lets you compare models, prompts, and retrieval strategies with numbers instead of vibes; catch regressions before they ship, the way CI catches broken builds; justify decisions ("hybrid retrieval lifted recall@5 from 0.74 to 0.93") to stakeholders; and measure safety, jailbreak resistance, PII leakage, and hallucination rate as first-class metrics.

## Evaluation Frameworks and Libraries

General-purpose frameworks for building and running LLM evaluations.

- [lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) - EleutherAI's de-facto standard harness for few-shot benchmark evaluation across hundreds of tasks.
- [OpenAI Evals](https://github.com/openai/evals) - Framework and open registry of evals for benchmarking models and prompt chains.
- [HELM](https://github.com/stanford-crfm/helm) - Stanford CRFM's Holistic Evaluation of Language Models, a broad standardized multi-metric suite.
- [DeepEval](https://github.com/confident-ai/deepeval) - Pytest-style unit testing for LLMs with metrics like faithfulness, relevancy, and hallucination.
- [promptfoo](https://github.com/promptfoo/promptfoo) - Test-driven prompt and model evaluation with a config-first workflow and CI integration.
- [Inspect AI](https://github.com/UKGovernmentBEIS/inspect_ai) - The UK AI Safety Institute's framework for large-scale LLM evaluations.
- [OpenCompass](https://github.com/open-compass/opencompass) - Comprehensive one-stop evaluation platform covering 100+ datasets.
- [LightEval](https://github.com/huggingface/lighteval) - Hugging Face's lightweight all-in-one evaluation suite.
- [Giskard](https://github.com/Giskard-AI/giskard) - Testing framework that automatically scans LLM apps for vulnerabilities and quality issues.
- [Evidently](https://github.com/evidentlyai/evidently) - Evaluation and monitoring for ML and LLM systems with 100+ built-in checks.
- [UpTrain](https://github.com/uptrain-ai/uptrain) - Open-source toolkit to evaluate and improve LLM applications with pre-built metrics.
- [Weave](https://github.com/wandb/weave) - Weights and Biases toolkit for tracking, evaluating, and iterating on LLM apps.

## LLM-as-a-Judge

Using strong models to score outputs, plus the methods that make judging reliable.

- [FastChat and MT-Bench](https://github.com/lm-sys/FastChat) - The original MT-Bench multi-turn benchmark and LLM-as-judge pipeline from LMSYS.
- [AlpacaEval](https://github.com/tatsu-lab/alpaca_eval) - Automatic length-controlled LLM-based evaluator with high human agreement.
- [Arena-Hard-Auto](https://github.com/lmarena/arena-hard-auto) - Automatic pipeline that builds hard benchmarks and judges with strong models.
- [Prometheus](https://github.com/prometheus-eval/prometheus-eval) - Open-source evaluator LLMs specialized for fine-grained rubric-based judging.
- [JudgeLM](https://github.com/baaivision/JudgeLM) - Fine-tuned open judge models for scalable LLM evaluation.

## RAG Evaluation

Measuring retrieval quality and answer faithfulness in RAG pipelines.

- [Ragas](https://github.com/explodinggradients/ragas) - The most-used RAG evaluation library, covering faithfulness, answer relevancy, and context precision and recall.
- [ARES](https://github.com/stanford-futuredata/ARES) - Automated RAG evaluation system using synthetic data and fine-tuned judges.
- [RAGChecker](https://github.com/amazon-science/RAGChecker) - Amazon's fine-grained diagnostic framework separating retriever and generator errors.
- [Continuous Eval](https://github.com/relari-ai/continuous-eval) - Data-driven evaluation for RAG and LLM pipelines with modular metrics.
- [AutoRAG](https://github.com/Marker-Inc-Korea/AutoRAG) - AutoML-style tool that evaluates and optimizes RAG pipeline configurations.

## Agent and Tool-Use Evaluation

Benchmarks and harnesses for autonomous agents, tool use, and multi-step tasks.

- [SWE-bench](https://github.com/princeton-nlp/SWE-bench) - Can agents resolve real GitHub issues? The benchmark that reshaped coding-agent evaluation.
- [AgentBench](https://github.com/THUDM/AgentBench) - Multi-environment benchmark evaluating LLMs as agents across 8 distinct settings.
- [tau-bench](https://github.com/sierra-research/tau-bench) - Sierra's benchmark for tool-agent-user interaction in real-world domains.
- [ToolBench](https://github.com/OpenBMB/ToolBench) - Large-scale dataset and evaluator for tool-use and API-calling ability.
- [WebArena](https://github.com/web-arena-x/webarena) - Realistic self-hostable web environment for evaluating autonomous web agents.

## Safety, Red-Teaming and Guardrails

Adversarial testing, jailbreak resistance, and harm measurement.

- [garak](https://github.com/NVIDIA/garak) - NVIDIA's LLM vulnerability scanner probing for jailbreaks, prompt injection, toxicity, and data leakage.
- [PyRIT](https://github.com/Azure/PyRIT) - Microsoft's Python Risk Identification Toolkit for generative-AI red-teaming.
- [HarmBench](https://github.com/centerforaisafety/HarmBench) - Standardized evaluation framework for automated red-teaming and refusal.
- [JailbreakBench](https://github.com/JailbreakBench/jailbreakbench) - Open benchmark and leaderboard for tracking jailbreak attacks and defenses.
- [PromptBench](https://github.com/microsoft/promptbench) - Microsoft's unified library for evaluating LLM robustness to adversarial prompts.

## Observability and Tracing

Production monitoring, trace capture, and online evaluation platforms.

- [Phoenix](https://github.com/Arize-ai/phoenix) - Arize's open-source LLM observability and evaluation platform built on OpenTelemetry.
- [Langfuse](https://github.com/langfuse/langfuse) - Open-source LLM engineering platform for tracing, evals, prompt management, and metrics.
- [TruLens](https://github.com/truera/trulens) - Instrumentation and feedback-function evaluation for LLM apps, strong on the RAG triad.
- [OpenLLMetry](https://github.com/traceloop/openllmetry) - OpenTelemetry-based observability for LLM applications by Traceloop.

## Benchmarks and Datasets

Knowledge and reasoning.

- [MMLU](https://github.com/hendrycks/test) - 57-subject multiple-choice benchmark, the long-standing knowledge standard.
- [MMLU-Pro](https://github.com/TIGER-AI-Lab/MMLU-Pro) - Harder, more reasoning-focused 10-option successor to MMLU.
- [GPQA](https://github.com/idavidrein/gpqa) - Graduate-level Google-proof science questions written by domain experts.
- [BIG-bench](https://github.com/google/BIG-bench) - 200+ collaboratively-authored tasks probing capabilities beyond current models.
- [BIG-Bench Hard](https://github.com/suzgunmirac/BIG-Bench-Hard) - The 23 hardest BIG-bench tasks where models trailed humans.

Math.

- [GSM8K](https://github.com/openai/grade-school-math) - 8.5K grade-school word problems, the standard multi-step arithmetic reasoning test.
- [MATH](https://github.com/hendrycks/math) - 12.5K competition math problems with step-by-step solutions.

Coding.

- [HumanEval](https://github.com/openai/human-eval) - OpenAI's hand-written programming problems evaluated by functional correctness (pass@k).
- [LiveCodeBench](https://github.com/LiveCodeBench/LiveCodeBench) - Contamination-free coding benchmark using continuously-collected recent problems.

Agentic and real-world tasks.

- [LiveBench](https://github.com/livebench/livebench) - Contamination-free benchmark with monthly-refreshed questions and objective ground truth.

Long context.

- [RULER](https://github.com/NVIDIA/RULER) - NVIDIA's synthetic benchmark measuring real usable context length beyond needle-in-haystack.
- [LongBench](https://github.com/THUDM/LongBench) - Bilingual multi-task benchmark for long-context understanding.

Instruction following.

- [IFEval](https://github.com/google-research/google-research/tree/master/instruction_following_eval) - Google's benchmark of verifiable instruction-following constraints.

Multimodal.

- [MMMU](https://github.com/MMMU-Benchmark/MMMU) - Massive multi-discipline multimodal understanding and reasoning benchmark.

## Leaderboards

- [LMArena (Chatbot Arena)](https://lmarena.ai) - Crowdsourced pairwise human-preference rankings via blind battles.
- [Artificial Analysis](https://artificialanalysis.ai) - Independent comparison of models across quality, speed, and price.
- [HELM Leaderboards](https://crfm.stanford.edu/helm/) - Stanford CRFM's standardized transparent multi-scenario leaderboards.
- [SEAL Leaderboards](https://scale.com/leaderboard) - Scale AI's private expert-curated evaluations resistant to contamination.

## Key Papers

- [Holistic Evaluation of Language Models (HELM)](https://arxiv.org/abs/2211.09110) - Liang et al., 2022. The case for broad, multi-metric evaluation.
- [Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena](https://arxiv.org/abs/2306.05685) - Zheng et al., 2023. Establishes LLM-as-judge validity and its biases.
- [G-Eval: NLG Evaluation using GPT-4 with Better Human Alignment](https://arxiv.org/abs/2303.16634) - Liu et al., 2023. Chain-of-thought LLM scoring.
- [RAGAS: Automated Evaluation of Retrieval Augmented Generation](https://arxiv.org/abs/2309.15217) - Es et al., 2023. Reference-free RAG metrics.
- [SWE-bench: Can Language Models Resolve Real-World GitHub Issues?](https://arxiv.org/abs/2310.06770) - Jimenez et al., 2023.
- [A Survey on Evaluation of Large Language Models](https://arxiv.org/abs/2307.03109) - Chang et al., 2023. Broad map of what, where, and how to evaluate.

## Guides and Articles

- [Hugging Face LLM Evaluation Guidebook](https://github.com/huggingface/evaluation-guidebook) - Practical opinionated field guide to designing and running evals.
- [Chip Huyen on Agents](https://huyenchip.com/2025/01/07/agents.html) - Deep dive on building agents with a substantial treatment of why evaluation is the hard part.

## Contributing

Contributions are very welcome. Please read [the contribution guidelines](CONTRIBUTING.md) first. In short: one item per line, keep the description factual and under 25 words, put items in the right section, and make sure the link works.
