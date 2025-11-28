# Detection of Fake Banknotes using SVM

Overview
- This repository contains an end-to-end Jupyter Notebook implementation that reproduces and extends the experiments from the research paper "Machine Learning Based Approach for Detection of Fake Banknotes Using Support Vector Machine." The notebook performs EDA, data preprocessing, implements SVM classifiers (linear, polynomial), tunes hyperparameters, evaluates model performance, and compares results with the referenced paper.

Repository contents
- individual project.ipynb — main Jupyter Notebook that contains:
  - Research paper summary and dataset description
  - Exploratory Data Analysis (EDA) and visualizations
  - Data preprocessing (outlier handling by group, train/test split with stratification)
  - SVM experiments using linear and polynomial kernels
  - Hyperparameter tuning (RandomizedSearchCV) and final model evaluation
  - Results and brief discussion

- banknotes.xlsx — dataset used by the notebook (UCI Banknote Authentication dataset exported as an XLSX file)

Note: Notebook source (for convenience):
https://github.com/Ginidu2003/Detection-of-Fake-Bank-notes-using-SVM/blob/main/individual%20project.ipynb

Project summary
- Dataset: Banknote Authentication dataset (UCI). 1372 samples with 4 features extracted via wavelet transform:
  - Variance — pixel variance from nearby pixels
  - Skewness — measure of asymmetry of the transformed image
  - Curtosis (Kurtosis) — measure of tail-heaviness relative to a normal distribution
  - Entrophy (Entropy) — measure of image randomness
  - Class — 0 = genuine, 1 = fake
- Typical class counts in the dataset: 762 genuine (class 0), 610 fake (class 1).
- Approach:
  - EDA and visualization (boxplots, histograms, correlation heatmap)
  - Train/test split: stratified split (30% test) with a fixed random_state for reproducibility
  - Outlier handling: Curtosis and Entrophy outliers replaced with the group mean (calculated per class using IQR bounds)
  - Models: SVM with linear kernel, SVM with polynomial kernel
  - Hyperparameter tuning: RandomizedSearchCV over polynomial kernel parameters (C, degree, coef0) with cross-validation
  - Evaluation: confusion matrix, precision/recall/F1, accuracy

Key results (as produced in the notebook)
- SVM (linear kernel): ~99% accuracy on the test split (a few misclassifications observed).
- SVM (polynomial kernel): substantially improved performance; with tuned hyperparameters the notebook reports 100% accuracy on the held-out test set for the particular train/test split and preprocessing employed.
  

How to run
1. Clone the repository:
   git clone https://github.com/Ginidu2003/Detection-of-Fake-Bank-notes-using-SVM.git
   cd Detection-of-Fake-Bank-notes-using-SVM

2. (Optional) Create and activate a virtual environment:
   python -m venv venv
   source venv/bin/activate   # macOS / Linux
   venv\Scripts\activate      # Windows

3. Install required packages:
   Install the common packages used in the notebook:
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter openpyxl

4. Open and run the notebook:
   jupyter notebook
   - Open "individual project.ipynb" and run the cells sequentially.
   - Alternatively, open the notebook in Google Colab via GitHub integration.

Reproducibility notes
- The notebook uses a fixed random_state in train_test_split and in SVM model creation where applicable. To reproduce results exactly, ensure the same random_state and package versions.


Citations and references
- Research paper referenced in the notebook: "Machine Learning Based Approach for Detection of Fake Banknotes Using Support Vector Machine"
- UCI Banknote Authentication dataset: https://archive.ics.uci.edu/ml/datasets/banknote+authentication


Contact
 https://github.com/Ginidu2003

