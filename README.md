# HR Bias Detection System

Web app built for my bachelor thesis at the German University in Cairo (2026):
*Detecting Bias in Performance Evaluations: AI Approaches for Fairness in HR Feedback Systems*.

**Live demo:** https://mooo-9.github.io/hr-bias-detection/

It helps HR teams and managers spot bias in performance evaluations, both in the written feedback and in the ratings, while keeping a human in the loop.

## Modules

1. **Evaluation Form**: submit an evaluation and get an instant bias gauge, flagged phrases and a suggested neutral rewrite.
2. **Analytics Dashboard**: fairness cards, charts and a department heatmap across all evaluations.
3. **ML Bias Predictor**: compares each rating with the rating expected from KPI, tenure and peer scores, and flags large deviations.
4. **NLP Analyzer**: rule-based detection of gendered, personality-focused, vague and recency-biased language.
5. **Fairness Framework**: demographic parity, disparate impact and equal opportunity metrics.
6. **XAI Explainability**: shows which factors drove each flag.

The demo runs entirely in the browser with 50 seeded sample evaluations, and you can download a bias report.

## Thesis results

The models were trained in Python with scikit-learn on 1,000 synthetic HR records, using a stratified 80/20 split and 5-fold cross-validation.

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---|---|---|---|---|
| Logistic Regression | 74.0% | 71.7% | 55.1% | 62.3% | 78.5% |
| **Decision Tree** | **89.0%** | **90.0%** | **80.8%** | **85.1%** | **94.2%** |
| Random Forest | 83.0% | 100.0% | 56.4% | 72.1% | 98.6% |

**Fairness audit (Decision Tree):** a disparate impact of 0.91 passes the four-fifths rule. However, the true positive rate for women was 17 points lower than for men (73.5% vs 90.5%), so fairness-constrained training is the next step.

## Files

- `index.html`: the app (React 18, Tailwind CSS, Chart.js; no build step)
- `bias_detection_hr.bpmn`: BPMN process model (open in Camunda Modeler or bpmn.io)
- `UseCase_BiasDetection_HR.drawio`: UML use case diagram (open in diagrams.net)

## Run locally

Open `index.html` in a browser.
