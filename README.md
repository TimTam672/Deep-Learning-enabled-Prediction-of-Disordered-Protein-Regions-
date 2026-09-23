# Deep-Learning-enabled Prediction of Disordered Protein Regions

Developed and optimized advanced deep learning and hybrid machine learning models to identify and predict intrinsically disordered regions (IDPs) within protein sequences, bypassing the need for costly and resource-intensive experimental characterization.

---

## 🚀 Key Highlights & Methodology

* **Data Engineering & Curation**: Aggregated, cleaned, and cross-checked **3,901 structural protein sequences** from three primary biological repositories (**DisProt, LLPSDB, and FuzDB**) to build a high-quality dataset, isolating **9% for strict independent external validation**.
* **Deep Learning Architecture**: Built a direct sequence-to-disorder model using a combined **3x Convolutional Neural Network (CNN)** and **5x Multi-Head Attention (MHA)** framework to capture local motifs and non-consecutive long-range amino acid interactions.
* **Hybrid PLM & Gradient Boosting Pipeline**: Engineered a state-of-the-art hybrid architecture leveraging high-dimensional embeddings from the **ESM-2** protein language model as automated features for downstream gradient boosting tree algorithms, including **XGBoost, LightGBM, and CatBoost**.
* **Optimization & Imbalance Handling**: Tackled a severe class imbalance (**19.8% minority disordered class**) by implementing a custom loss function combining dataset-weighted **Focal Loss** and **Total Variation (TV) Regularization** de-noising to maintain structural contiguity.
* **Post-Processing & Evaluation**: Utilized 5-fold cross-validation and threshold optimization (shifting thresholds to **0.66–0.68**) to boost the **Test Macro F1-score to 0.70** and **Accuracy to 0.82**. Applied Hard/Soft voting ensemble strategies and advanced smoothing techniques (**Savitzky-Golay, Median, and Moving Average filters**) to eliminate residue intermixing noise.

---

## 📊 Workflow Architecture

### Method 1

![Workflow Architecture](https://github.com/TimTam672/Deep-Learning-enabled-Prediction-of-Disordered-Protein-Regions-/blob/30442bd1d2440b19f43be487d44d1208214af945/Method1_Workflow.png)

### Method 2
![Workflow Architecture](https://github.com/TimTam672/Deep-Learning-enabled-Prediction-of-Disordered-Protein-Regions-/blob/30442bd1d2440b19f43be487d44d1208214af945/Method2_Workflow.png)

---

##  Model Performance
![Performance](https://github.com/TimTam672/Deep-Learning-enabled-Prediction-of-Disordered-Protein-Regions-/blob/2eaa193d5bf1f1f36df56c27be68633908c4942c/Summarization%20of%20Model%20Performance.pngg)

## 📂 Repository File Structure

### 📑 Documentation & Deliverables
* **`REPORT.pdf`**: The comprehensive research report detailing the scientific background, implementation, and rigorous benchmarks.
* **`Presentation_PowerPoint.pdf`**: The PDF-formatted slide deck summarizing the project outcomes and architecture.

### 🗃️ Datasets
Both datasets contain sequence records mapping `UniProt ACC` identities and their corresponding `Full_Sequence` strings:
* **`Deepdisprot_train_combined_dataset.csv`**: The benchmark training dataset curated from DisProt, LLPSDB, and FuzDB.
* **`Deepdisprot_external_combined_dataset.csv`**: The isolated 9% independent external validation test set.

### 🧪 Embedded Features
High-dimensional protein language model representations used for training and testing downstream tree-based ensembles:
* **`trained_esm2_embeddings_external.npz`**: The feature extraction embeddings array for the external validation test set (managed via Git LFS).
* *Note on Training Embeddings*: The raw `trained_esm2_embeddings.npz` training array exceeds GitHub LFS individual file boundaries (~2.5GB). You can regenerate these local features locally using the evaluation notebook below.

### ⚙️ Source Notebooks
* **`ESM35M.ipynb`**: Handles feature extraction, logs ESM-2 protein language model evaluations, and serializes high-dimensional embeddings.
* **`Boosting_CVTuning_Smoothing.ipynb`**: Executes cross-validation parameter tuning for `XGBoost`, `LightGBM`, and `CatBoost` estimators, builds the hybrid Hard/Soft ensemble voting meta-models, and applies localized smoothing adjustments.

---
