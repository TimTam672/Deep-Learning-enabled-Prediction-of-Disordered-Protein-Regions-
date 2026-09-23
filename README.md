# Deep-Learning-enabled-Prediction-of-Disordered-Protein-Regions-

Developed and optimized advanced deep learning and hybrid machine learning models to identify and predict intrinsically disordered regions (IDPs) within protein sequences, bypassing the need for costly and resource-intensive experimental characterization.

Data Engineering: Aggregated, cleaned, and cross-checked 3,901 structural protein sequences from three primary biological repositories (DisProt, LLPSDB, and FuzDB) to build a high-quality dataset, isolating 9% for strict independent external validation.

Deep Learning Architecture: Built a direct sequence-to-disorder model using a combined 3x Convolutional Neural Network (CNN) and 5x Multi-Head Attention (MHA) framework to capture local motifs and non-consecutive long-range amino acid interactions.

Hybrid PLM & Gradient Boosting Pipeline: Engineered a state-of-the-art hybrid architecture leveraging high-dimensional embeddings from the ESM-2 protein language model as automated features for downstream gradient boosting tree algorithms, including XGBoost, LightGBM, and CatBoost.

Optimization & Imbalance Handling: Tackled a severe class imbalance (19.8% minority disordered class) by implementing a custom loss function combining dataset-weighted Focal Loss and Total Variation (TV) Regularization de-noising to maintain structural contiguity.

Post-Processing & Evaluation: Utilized 5-fold cross-validation and threshold optimization (shifting thresholds to 0.66–0.68) to boost the Test Macro F1-score to 0.70 and accuracy to 0.82 (pp. 17, 19). Applied Hard/Soft voting ensemble strategies and advanced smoothing techniques (Savitzky-Golay, Median, and Moving Average filters) to eliminate residue intermixing noise.
