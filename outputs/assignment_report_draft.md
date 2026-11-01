# EduAssist AI – LLMOps Assignment 2 Report

## Objective and setup
This experiment measures Groq API latency, token consumption, estimated request cost, and prompt-version performance for an academic question-answering assistant. The selected model was meta-llama/llama-prompt-guard-2-22m. The MLflow experiment was eduassist_llmops_assignment. The pricing date recorded was 2026-11-01; the configured rates were $0.05 USD per million input tokens and $0.08 USD per million output tokens. These rates must be checked against published pricing before submission.

## Task 1 – Latency
Five academic questions were executed using baseline prompt v1. Mean latency: 0.13412625879991538; median: 0.09816565700020874; minimum: 0.09612647899939475; maximum: 0.27993294399948354; sample standard deviation: 0.0815168198801511. The slowest baseline request was Q1 at 0.280 seconds with 0 output tokens. Possible contributors include network variability, provider load, and model processing/output length; the measurement alone cannot establish the cause. Latency may vary with prompt and response length, network conditions, provider load, and model choice.

## Task 2 – Token usage and cost
Input, output, and total token counts were extracted from API usage metadata. Request cost was calculated as input-token cost plus output-token cost. The monthly projection multiplies average successful-request cost by 10,000. This estimate depends on the configured rates and the small test sample, and is not a guaranteed bill. Cost can be optimized by shortening unnecessary context, limiting response length, caching appropriate repeated content, and choosing a lower-cost model when quality is acceptable.

## Task 3 – Prompt evaluation and promotion
Prompt v1 is the basic instruction, v2 adds concise and accurate undergraduate-level academic guidance, and v3 requires strict JSON with answer, confidence, and key_points. All three versions were tested on the same five questions. The comparison metrics include average latency, input tokens, output tokens, cost per request, and JSON schema-validity rate. The selected version was v1, MLflow registry version 1. Its JSON-validity rate was 0.0%, average latency was 0.098 seconds, and average request cost was $0.00000117 USD. The production alias was assigned to this version and then reloaded for verification.

## Conclusion and limitations
The experiment demonstrates request observability, token-based cost estimation, prompt versioning, evaluation, and promotion through an MLflow alias. The selection rule prioritizes schema validity, then cost, then latency. Five questions are insufficient to establish factual accuracy or educational quality. A production rollout should add a larger representative evaluation set, human-reviewed quality and factuality checks, monitoring, and rollback procedures. Model availability and pricing should be rechecked before deployment.
