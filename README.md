# MedSynth_Shared_Task
This is the repository for MedSynth in SMM4H-HeaRD 2026 shared task

## Quick Start

### 1. Prepare Your Submission

Create a CSV file with your predictions:

```csv
id,generated_note
1,"Patient presents with chest pain..."
2,"Chief complaint is headache..."
```


### 2. Run Evaluation

```bash
python evaluate_dialogue_to_note.py --submission your_submission.csv
```


**Custom Output Path:**
```bash
python evaluate_dialogue_to_note.py --submission your_submission.csv --output my_results.csv
```

**Custom Ground Truth Path:**
```bash
python evaluate_dialogue_to_note.py \
    --submission your_submission.csv \
    --ground_truth path/to/custom_eval.csv
```

### 3. View Results

Results will be displayed in the terminal and saved to CSV:
- Default location: `results/<submission_name>_eval.csv`
- Custom location: specified with `--output` flag

Example output:
```
============================================================
EVALUATION RESULTS
============================================================
Samples Evaluated: 1506
Coverage: 100.00%
------------------------------------------------------------
BLEU:           0.5346
ROUGE-1:        0.7441
ROUGE-2:        0.5150
ROUGE-L:        0.5885
ROUGE-Lsum:     0.7230
METEOR:         0.6589
============================================================
```

---

## Requirements

### Python Packages
```bash
pip install pandas evaluate nltk
python -c "import nltk; nltk.download('punkt_tab')"
```

### Data Files
- **Training Data:** `dataset/shared_task_train.csv`
- **Evaluation Data:** `dataset/shared_task_eval.csv`

---

## Evaluation Metrics

- **BLEU:** N-gram overlap (0-1, higher is better)
- **ROUGE-1/2/L:** Unigram/bigram/longest common subsequence recall (0-1, higher is better)
- **ROUGE-Lsum:** Summary-level ROUGE-L (0-1, higher is better)
- **METEOR:** Semantic similarity with stemming and synonyms (0-1, higher is better)

---

## Submission Requirements

✅ **Required:**
- CSV format with correct columns (`id` + `generated_note` or `generated_dialogue`)
- IDs must match the evaluation set (1-1506)
- All predictions should be strings

✅ **Recommended:**
- 100% coverage (all 1506 samples)
- No missing or empty predictions

⚠️ **Warnings:**
- Missing IDs will trigger warnings but evaluation will continue
- Empty predictions will be treated as empty strings

---

## Common Issues

**Problem:** `ModuleNotFoundError: No module named 'rouge_score'`  
**Solution:** 
```bash
pip install rouge-score
```

**Problem:** `LookupError: Resource punkt_tab not found`  
**Solution:**
```bash
python -c "import nltk; nltk.download('punkt_tab')"
```

**Problem:** Missing IDs in submission  
**Solution:** Ensure your submission includes all IDs from 1 to 1506

**Problem:** Column name mismatch  
**Solution:** 
- Dialogue-to-Note: Use `id,generated_note`
- Note-to-Dialogue: Use `id,generated_dialogue`

---

## Files

- `evaluate_dialogue_to_note.py` - Evaluate dialogue → note generation
- `dataset/shared_task_train.csv` - Training data (id, note, dialogue)
- `dataset/shared_task_eval.csv` - Evaluation data (id, note, dialogue)
- `BASELINE_PERFORMANCE_REPORT.md` - Baseline model results

---

## Example Workflow

```bash
# 1. Check your submission format
head your_submission.csv

# 2. Run evaluation
python evaluate_dialogue_to_note.py --submission your_submission.csv

# 3. Check results
cat results/your_submission_eval.csv

# 4. Compare with baseline (see BASELINE_PERFORMANCE_REPORT.md)
```

---

## Questions?

See `BASELINE_PERFORMANCE_REPORT.md` for baseline performance targets and detailed submission guidelines.

