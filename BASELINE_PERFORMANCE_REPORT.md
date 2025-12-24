# Shared Task: Baseline Performance Report

## Overview
This report presents baseline performance metrics for the dialogue-to-clinical-note generation task. Three state-of-the-art language models were evaluated on the test set to establish performance benchmarks for participants.

---

## Task Description
**Objective:** Generate clinical notes from doctor-patient dialogues

**Evaluation Set:** 1,506 dialogue-note pairs

**Metrics:**
- **BLEU:** Measures n-gram overlap between generated and reference notes
- **ROUGE-1/2/L:** Evaluates recall of unigrams, bigrams, and longest common subsequences
- **METEOR:** Considers synonyms and stemming for semantic similarity


---

## Baseline Results

### Model Performance Summary

| Model | BLEU | ROUGE-1 | ROUGE-2 | ROUGE-L | METEOR |
|-------|------|---------|---------|---------|--------|
| **Mistral-7B-Instruct-v0.3** | **0.5346** | **0.7441** | **0.5150** | **0.5885** | **0.6589** |
| **Llama-3-8B-Instruct** | 0.5206 | 0.7341 | 0.5020 | 0.5740 | 0.6487 |
| **GPT-4o** | 0.2616 | 0.6525 | 0.3953 | 0.4818 | 0.4754 |

*Bold indicates best performance per metric*

---

## Key Findings

### 1. Top Performer: Mistral-7B-Instruct-v0.3, 4-bit quantized fine tuned on the training set
- Achieved highest scores across all metrics
- ROUGE-1 score of 0.744 indicates strong content recall
- METEOR score of 0.659 suggests good semantic alignment
- Demonstrates that smaller, specialized models can excel at clinical text generation

### 2. Strong Competitor: Llama-3-8B-Instruct, 4-bit quantized fine tuned on the training set
- Performance very close to Mistral-7B (within 1-2% on most metrics)
- Consistent second-place ranking across all metrics
- Represents a viable alternative baseline

### 3. GPT-4o Performance, zero-shot prompting
- Lower performance compared to open-source alternatives
- BLEU score of 0.262 suggests different generation strategy
- May prioritize paraphrasing over literal reproduction
- Results evaluated on August 15, 2024

---

## Performance Targets for Participants

### Competitive Performance Thresholds

**Minimum Competitive:**
- BLEU ≥ 0.26 (GPT-4o baseline)
- ROUGE-1 ≥ 0.65
- METEOR ≥ 0.48

**Strong Performance:**
- BLEU ≥ 0.52 (Llama-3-8B baseline)
- ROUGE-1 ≥ 0.73
- METEOR ≥ 0.65

**State-of-the-Art:**
- BLEU > 0.53 (exceed Mistral-7B)
- ROUGE-1 > 0.74
- METEOR > 0.66

---

## Evaluation Details

**Test Set Size:** 1,506 samples  
**Evaluation Period:** August 2024  
**Metrics Computed:** BLEU, ROUGE (1/2/L/Lsum), METEOR  


---

## Submission Guidelines

### Required Submission Format
Your submission should be a CSV file with the following columns:
```csv
id,generated_note
1,"Patient presents with..."
2,"Chief complaint is..."
```

### Evaluation Process
1. Submit your CSV file with predictions for all 1,506 test samples
2. Ensure 100% coverage (all IDs from evaluation set must be present)
3. Your submission will be evaluated using the `evaluate_dialogue_to_note.py` script
4. Results will include: BLEU, ROUGE-1, ROUGE-2, ROUGE-L, ROUGE-Lsum, and METEOR

### Coverage Requirement
- **Required:** 100% coverage (all 1,506 samples)
- Partial submissions will be accepted but coverage will be reported
- Missing predictions will receive a warning in evaluation output

---

## How to Use This Benchmark

1. **Set Your Target:** Choose a performance tier based on your approach
2. **Iterative Development:** Use these metrics to track your progress
3. **Compare Fairly:** All baselines evaluated on the same evaluation set
4. **Consider Trade-offs:** Higher metrics don't always mean better clinical utility

---

## Questions?

For questions about the baseline results or evaluation process, please refer to:
- Evaluation scripts: `evaluate_dialogue_to_note.py`
- Sample data: `dataset/shared_task_train.csv` (training data with IDs)
- Test set: `dataset/shared_task_eval.csv` (for evaluation only)

---