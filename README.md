# OffensEval - Offensive Language Identification (SemEval-2019 Task 6)
This project identifies and categorizes **offensive language in social media posts**, based on the **Offensive Language Identification Dataset (OLID)** released for **SemEval-2019 Task 6 (OffensEval)**. The study was conducted as part of the **Introduction to Natural Language Processing** course at **George Mason University**.

## 👥 Team Members
- Anusha Goulla  
- Vyoma Harshitha Podapati  
- Shree Pallavi Vegesana  
- Armin Keshavarz Rahbar  
- Lakshmi Durga Teratipally  

## 📌 Project Overview

The project involves **hierarchical classification** of tweets into three levels:

- **Sub-task A**: Classify tweets as **Offensive (OFF)** or **Not Offensive (NOT)**
- **Sub-task B**: Further classify offensive tweets as **Targeted Insults/Threats (TIN)** or **Untargeted (UNT)**
- **Sub-task C**: Identify the target of the offense as an **Individual (IND)**, **Group (GRP)**, or **Other (OTH)**

We use **Logistic Regression** models trained on TF-IDF features with preprocessing tailored for social media text.

## 📁 Dataset

- **Name**: OLID (Offensive Language Identification Dataset)  
- **Source**: [SemEval 2019 Task 6](https://competitions.codalab.org/competitions/20011)  
- **Language**: English  
- **Training Samples**: 13,240 tweets  
- **Test Samples**: 860 tweets  
- **Hierarchical Structure**: Sub-tasks A, B, C  
- **Note**: Significant class imbalance exists in sub-tasks B and C.

## ⚙️ Methodology

### 🔄 Preprocessing
- Lowercasing
- Replacing URLs with `<URL>` and mentions with `<MENTION>`
- Removing special characters (except `!` and `?`)
- Replacing numbers with `<NUM>`
- Tokenization and whitespace cleanup

### 🔠 Feature Extraction
- TF-IDF Vectorization
  - Sub-tasks A & B: `max_features=10000`, `ngram_range=(1,2)`, `stop_words='english'`
  - Sub-task C: `max_features=3000`, `ngram_range=(1,2)`

### 📊 Model
- **Algorithm**: Logistic Regression (with balanced class weights)
- **Optimization**: GridSearchCV (5-fold cross-validation)
- **Hyperparameter Tuning**: Regularization parameter `C`
- **Evaluation Metrics**: Accuracy, Precision, Recall, F1 Score, Confusion Matrix (Macro F1 used for imbalanced classes)

## 📈 Results

| Sub-task | Accuracy | Macro F1 Score |
|----------|----------|----------------|
| A        | 0.786    | 0.7348         |
| B        | 0.8375   | 0.6530         |
| C        | 0.6667   | 0.5934         |

Sub-task C was the most challenging due to minority classes. However, our model outperformed several deep learning baselines in Sub-task C, including CNN and BiLSTM.

## 🏆 Benchmark Comparison

| Model         | A (F1) | B (F1) | C (F1) |
|---------------|--------|--------|--------|
| Logistic Reg. | 0.7348 | 0.6530 | 0.5934 |
| SVM           | 0.690  | 0.640  | 0.450  |
| BiLSTM        | 0.750  | 0.660  | 0.470  |
| CNN           | 0.800  | 0.690  | 0.470  |

---

## 🧠 Future Work
- Incorporate **deep learning models** like BiLSTM with contextual embeddings (e.g., BERT)
- Address **class imbalance** using SMOTE or cost-sensitive learning
- Expand dataset to **other platforms** and **languages**
- Use **transformers** for better context understanding in offensive language detection

---

## 📚 References

1. Zampieri, M., Malmasi, S., Nakov, P., Rosenthal, S., Farra, N., & Kumar, R. (2019). *Predicting the type and target of offensive posts in social media.* NAACL-HLT.
2. Zampieri, M., et al. (2019). *SemEval-2019 Task 6: OffensEval.* In 13th International Workshop on Semantic Evaluation.
3. Wiegand, M., Siegel, M., & Ruppenhofer, J. (2018). *Overview of the GermEval 2018 shared task on the identification of offensive language.*

---

## 🙏 Acknowledgements

We would like to thank **Dr. Marcos Zampieri** for his expert guidance and continuous support, and our TA **Sadiya Sayara Chowdhury Puspo** for her feedback throughout the course.



