# BigMart-Sales-Prediction
![Python](https://img.shields.io/badge/Python-3.11-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-blue?logo=pandas)
![Scikit-learn](https://img.shields.io/badge/Scikit--Learn-ML-orange?logo=scikitlearn)
![XGBoost](https://img.shields.io/badge/XGBoost-Regressor-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

An end-to-end Machine Learning project for predicting BigMart product sales using data preprocessing, feature engineering, and XGBoost.
## 📌 Project Overview
This project aims to predict the sales of products across different BigMart outlets using Machine Learning techniques. The project follows a complete end-to-end Data Science workflow, including data preprocessing, feature engineering, exploratory data analysis (EDA), model building, evaluation, and prediction.

Multiple regression algorithms were implemented and compared to identify the best-performing model. Finally, XGBoost Regressor was selected for generating predictions due to its superior performance.

---

## 🎯 Business Problem

BigMart wants to predict the sales of products across different stores before they are sold. Accurate sales prediction helps the business in inventory management, demand forecasting, pricing strategies, and improving overall operational efficiency.

The objective of this project is to build a Machine Learning model capable of accurately predicting the sales of products based on their characteristics and outlet information.

---

## 📂 Dataset Information

The dataset contains information about products sold in different BigMart outlets.

### Training Dataset
- Records: 8,523
- Features: 12
- Target Variable: `Item_Outlet_Sales`

### Test Dataset
- Records: 5,681
- Features: 11

The dataset contains information related to:

- Product characteristics
- Product weight
- Product visibility
- Product type
- Fat content
- Maximum Retail Price (MRP)
- Outlet establishment year
- Outlet size
- Outlet location
- Outlet type

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- Jupyter Notebook
- Git & GitHub

---

## ⚙️ Data Preprocessing

Before training the Machine Learning models, the raw dataset was thoroughly preprocessed to improve data quality and ensure better model performance.

The following preprocessing steps were performed:

### Missing Value Treatment

- Imputed missing values in `Item_Weight` using the median.
- Filled missing values in `Outlet_Size` based on the mode of each `Outlet_Type`.

### Data Cleaning

- Standardized inconsistent values in `Item_Fat_Content` (e.g., *LF*, *low fat*, and *reg*) into consistent categories.
- Corrected zero values in `Item_Visibility` by replacing them with the average visibility of the corresponding product.

### Feature Selection

- Removed `Item_Identifier` and `Outlet_Identifier` as they are unique identifiers and do not contribute meaningful predictive information.

### Categorical Data Encoding

- Applied Label Encoding to nominal categorical features.
- Applied Ordinal Encoding to ordinal categorical features.
- Applied One-Hot Encoding where appropriate to convert categorical variables into numerical format.

### Data Validation

- Verified that there were no missing values after preprocessing.
- Ensured that the training and test datasets had consistent feature structures before model training.

---

## 🧠 Feature Engineering

Feature engineering was performed to create more meaningful features and improve the predictive performance of the machine learning models.

The following feature engineering techniques were applied:

### Item Category Creation

- Created a new feature `Item_Category` by extracting the product category from the `Item_Identifier`.
- This simplified product identification into meaningful business categories such as **Food**, **Drinks**, and **Non-Consumable**.

### Outlet Age

- Created a new feature `Outlet_Age` by calculating the age of each outlet using the establishment year.
- This feature helps capture the impact of outlet maturity on product sales.

### Item Visibility Correction

- Replaced zero values in `Item_Visibility` with the average visibility of the corresponding product.
- This ensured realistic visibility values and improved data quality.

### Standardization of Item Fat Content

- Standardized inconsistent values such as **LF**, **low fat**, and **reg** into consistent categories.
- Assigned **Non-Edible** to products that do not have a fat content category.

### Feature Removal

The following features were removed because they do not provide meaningful predictive information:

- `Item_Identifier`
- `Outlet_Identifier`

Removing these identifier columns reduced unnecessary model complexity and helped prevent overfitting.

---

## 🤖 Machine Learning Models

To identify the most suitable algorithm for predicting product sales, multiple regression models were trained, evaluated, and compared. Each model was assessed using the same training and testing datasets to ensure a fair comparison.

The following machine learning algorithms were implemented:

### Linear Regression

- Used as the baseline regression model.
- Helped understand the linear relationship between features and the target variable.

### Ridge Regression

- Applied L2 regularization to reduce overfitting while maintaining model simplicity.

### Lasso Regression

- Applied L1 regularization to perform feature selection and reduce model complexity.

### Random Forest Regressor

- Implemented as an ensemble learning algorithm to capture non-linear relationships.
- Although it achieved excellent training performance, it showed signs of overfitting on the test dataset.

### XGBoost Regressor

- Implemented as the final ensemble model.
- Delivered the best predictive performance among all the evaluated models.
- Selected as the final model for generating predictions on the unseen test dataset.

---

## 📈 Model Performance

The performance of all regression models was evaluated using the R² Score, Mean Absolute Error (MAE), and Root Mean Squared Error (RMSE). The results are summarized below:

| Model | Test R² Score | Test MAE | Test RMSE |
|--------|--------------:|---------:|----------:|
| Linear Regression | 0.5799 | 791.69 | 1068.57 |
| Ridge Regression | 0.5799 | 791.59 | 1068.55 |
| Lasso Regression | 0.5802 | 790.78 | 1068.18 |
| Random Forest Regressor | 0.5634 | 760.30 | 1089.39 |
| **XGBoost Regressor** | **0.6045** | **725.08** | **1036.80** |

### Best Performing Model

Among all the evaluated models, **XGBoost Regressor** achieved the highest Test R² Score and the lowest prediction error. Therefore, it was selected as the final model for generating predictions on the unseen test dataset.

---

## 💡 Key Learnings

Throughout this project, I gained hands-on experience in:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Feature engineering
- Handling missing values and inconsistent data
- Encoding categorical variables
- Building and comparing multiple regression models
- Model evaluation using R² Score, MAE, and RMSE
- Feature importance analysis using XGBoost
- Generating predictions for unseen data
- Creating a complete end-to-end Machine Learning pipeline

---

## 📁 Project Structure

The project is organized into the following directory structure:

```text
BigMart-Sales-Prediction/
│
├── data/
│   ├── Train.csv
│   └── Test.csv
│
├── notebooks/
│   └── BigMart_Sales_Prediction.ipynb
│
├── outputs/
│   └── submission.csv
│
├── images/
│   ├── EDA/
│   └── Feature_Importance/
│
├── README.md
├── requirements.txt
├── .gitignore
└── LICENSE
```

### Directory Description

- **data/** – Contains the training and testing datasets.
- **notebooks/** – Contains the Jupyter Notebook used for data analysis, preprocessing, model building, and evaluation.
- **outputs/** – Stores the final prediction file (`submission.csv`).
- **images/** – Contains plots, visualizations, and feature importance charts used in the README.
- **README.md** – Provides complete documentation of the project.
- **requirements.txt** – Lists all Python libraries required to run the project.
- **.gitignore** – Specifies files and folders that Git should ignore.
- **LICENSE** – Defines the project's license.

---

## 🚀 Installation & How to Run

To run this project on your local machine, follow these steps:

### 1. Clone the Repository

```bash
git clone https://github.com/bytes-saurabh/BigMart-Sales-Prediction.git
```

### 2. Navigate to the Project Directory

```bash
cd BigMart-Sales-Prediction
```

### 3. Install the Required Libraries

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 5. Open the Notebook

Open **BigMart_Sales_Prediction.ipynb** and run all the cells in sequence to reproduce the complete machine learning workflow.

---

## 📌 Project Conclusion

This project successfully demonstrates an end-to-end Machine Learning workflow for predicting product sales across different BigMart outlets. Starting from raw data preprocessing and feature engineering to model building, evaluation, and prediction, every stage of the Machine Learning pipeline was implemented and analyzed.

Multiple regression models were trained and compared to identify the most suitable algorithm for this business problem. Among all the evaluated models, **XGBoost Regressor** achieved the best predictive performance with the highest Test R² Score and the lowest prediction error.

This project strengthened my understanding of data preprocessing, feature engineering, regression modeling, model evaluation, and the importance of selecting the right algorithm for real-world business problems.

---

## 🔮 Future Improvements

The following enhancements can further improve the performance and usability of this project:

- Perform advanced hyperparameter tuning using GridSearchCV or Optuna.
- Apply feature selection techniques to identify the most significant predictors.
- Use SHAP values for better model interpretability.
- Deploy the trained model using Streamlit or Flask for real-time sales prediction.
- Automate the complete Machine Learning pipeline using Scikit-learn Pipelines.
- Integrate CI/CD workflows for continuous testing and deployment.
- Experiment with advanced boosting algorithms such as LightGBM and CatBoost.

---

## 👨‍💻 Author

**Saurabh Singh**

Aspiring Data Scientist | Data Analyst

### Connect with Me

- **GitHub:** https://github.com/bytes-saurabh
- **LinkedIn:** https://www.linkedin.com/in/saurabh-singh-8bba43348/

If you found this project helpful, feel free to ⭐ star this repository and share your feedback.
