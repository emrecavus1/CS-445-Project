Overview

This project addresses SemEval-2026 Task 2, which focuses on predicting emotional valence and arousal from ecological essays. The task formulates emotion as a continuous, ordinal signal rather than discrete emotion classes, requiring models that can capture both semantic meaning and relative emotional intensity.

Our goal is to build a robust text-based system that predicts valence and arousal values for each input instance, following the official task setup. Due to the hidden nature of the test set, all development and evaluation are conducted on the provided training and trial splits.

Approach Summary

Our system is built around a transformer-based textual encoder combined with ordinal-aware prediction heads for valence and arousal.

Key Components

Text Encoder
We use a pretrained RoBERTa-based encoder to obtain contextualized representations of the input essays. RoBERTa was chosen due to its strong performance on emotion and sentiment-related NLP tasks.

Ordinal Modeling of Emotion
Instead of treating valence and arousal as purely categorical labels, we model them as ordered variables. This allows the system to penalize large emotional mispredictions more heavily than small ones (e.g., predicting “slightly positive” instead of “very positive” is less severe than predicting “very negative”).

Regression-to-Ordinal Pipeline
The model first learns continuous emotion scores and then maps them to discrete ordinal labels during evaluation. This setup helps stabilize training while preserving ordinal structure.

Loss Design
We experiment with regression-based objectives (e.g., MSE / ordinal-aware losses) to better align optimization with the task’s evaluation criteria and emotional distance sensitivity.

Evaluation Strategy

All experiments are conducted exclusively on the provided training and trial data, as the official test set is not publicly available.

Fixed random seeds are used to ensure reproducibility, which is especially important given the small size of the trial set.

Performance is assessed using task-relevant metrics, with additional analysis via confusion matrices and error-distance inspection to understand ordinal behavior.

Notes

This repository contains only our original implementation and experiments.

External libraries (e.g., HuggingFace Transformers, PyTorch) are used strictly as supporting tools.

The project prioritizes methodological contribution and analysis over leaderboard optimization, in line with CS 445 project guidelines.
