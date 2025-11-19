# Slip 2

Below are step-by-step instructions to perform the required tasks inside WEKA (Explorer). Each subquestion includes: dataset to use, WEKA steps, how to record results, and how to compute metrics.

## Q1
**Task:** Q1: Neural network classifier (attribute selection compare).

### Datasets (likely):
- iris.arff, weather.arff/ weather.nominal.arff, cancer.arff, supermarket.arff, sales_data_sample.csv (depending on Q)

### WEKA Steps (general for classification tasks):
1. Open WEKA → Explorer.
2. Preprocess → Open file → select the dataset (e.g., iris.arff).
3. Click the 'Classify' tab.
4. Choose an appropriate classifier (e.g., NaiveBayes: bayes → NaiveBayes; J48: trees → J48; MultilayerPerceptron: functions → MultilayerPerceptron).
5. In 'Test options', select 'Cross-validation' and set folds = 10 (for 10-fold CV) unless specified otherwise.
6. Click 'Start'.
7. In the 'Result list', click the output to view the 'Confusion Matrix' and performance metrics.

### How to report results:
- Copy the confusion matrix shown in WEKA.
- Compute accuracy using: Accuracy = (TP + TN) / (TP + TN + FP + FN) * 100%
- Also report Precision, Recall, F-measure, and ROC Area (if present).

### If attribute selection is requested:
1. Go to 'Select attributes' tab.
2. Choose evaluator: e.g., CfsSubsetEval or InfoGainAttributeEval.
3. Choose search method: BestFirst or Ranker. Click 'Start'.
4. Note selected attributes, then go back to 'Classify' and train classifier using only selected attributes (use 'Filter' → 'Remove' to remove unwanted attributes).
5. Compare accuracies and mention which attributes improved performance and why (intuitively).


## Q2
**Task:** Q2: K-Means clustering on sales_data_sample.csv (elbow method) OR EM clustering (confusion matrix & accuracy).

### Clustering Steps (K-Means / EM / Hierarchical):
1. Open WEKA → Explorer → Cluster tab.
2. Open file → select dataset (e.g., sales_data_sample.csv — convert CSV to ARFF if needed: Tools → ArffViewer or use 'Open file' on CSV; WEKA can open CSV).
3. Choose clusterer: SimpleKMeans (for K-Means), EM, or HierarchicalClusterer.
4. For K-Means, set 'numClusters' to values 2..6 and note the 'Within cluster sum of squared errors' (WCSS)
5. Use the elbow method: run K values and record WCSS; plot K vs WCSS and pick the 'elbow' (the K after which WCSS reduction slows).
6. For Hierarchical, run and view dendrogram in results.
7. Record cluster centroids (for K-Means) or cluster assignments; if class labels exist, use 'Classes to clusters evaluation' to get a confusion matrix-like mapping.


### Final reporting for Q2:
- Copy results tables, cluster summaries or rules. Provide interpretation (why clusters make sense, what top rules imply, how normalization changed statistics, etc.).

----

### Quick tips & Common pitfalls
- Always set the correct class attribute (in 'Preprocess', use the drop-down 'Class').
- For CSVs, ensure nominal attributes are properly handled (convert or set attribute types in ARFF).
- If saving models: In 'Classify', after training, click 'Save model' to disk; reload via 'Supplied test set' → 'Set' → 'Load model'.
- Mention exact numeric values from WEKA output in your exam answers (confusion matrix numbers, accuracy%, ROC area etc.).

### References
- WEKA documentation: 'Explorer' interface steps.
