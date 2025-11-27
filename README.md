# Hospital Readmissions Prediction

## Project Overview

This project aims to predict whether a patient is likely to be readmitted to the hospital within 30 days of discharge. It involves data cleaning, preprocessing, training a machine learning model to handle missing data, training a final prediction model, and deploying the model as an interactive web application using Streamlit.

---

## File Descriptions

This section details the role of each file within the project.

### Data Files (`.csv`)

-   **`hospital_readmissions.csv`**: The raw, original dataset containing patient and encounter information. This is the starting point for the project.
-   **`hospital_readmissions_only_int.csv`**: An intermediate version of the dataset where categorical features have likely been encoded into integer representations.
-   **`hospital_with_actual_A1C.csv`**: A subset of the data containing records where the `A1C_Result` was present.
-   **`hospital_with_predicted_A1C.csv`**: The dataset after predicting and filling in missing `A1C_Result` values.
-   **`hospital_readmissions_final.csv`**: The final, cleaned, and preprocessed dataset used for training the primary readmission prediction model. It contains the complete set of features and the target variable (`Readmitted`).

### Jupyter Notebooks (`.ipynb`)

-   **`Replacing_A1C.ipynb`**: This notebook likely details the process of handling missing `A1C_Result` values. It probably explores the data, identifies missing values, and outlines the strategy for imputation.
-   **`A1C_Model.ipynb`**: This notebook is used to train a machine learning model to predict the `A1C_Result` based on other patient features. This is a common technique to handle missing data for an important feature.
-   **`Readmitted_Model.ipynb`**: This is the core notebook for the project. It uses the `hospital_readmissions_final.csv` dataset to train, evaluate, and save the final model for predicting patient readmission.

### Model Files (`.pkl`)

-   **`A1C_Model.pkl`**: A serialized, pre-trained machine learning model generated from the `A1C_Model.ipynb` notebook. Its purpose is to predict missing `A1C_Result` values.
-   **`Readmission_Model.pkl`**: The final, serialized machine learning model for predicting hospital readmission. This model is generated from the `Readmitted_Model.ipynb` notebook and is used by the Streamlit application.

### Application File (`.py`)

-   **`Hospital_Streamlit.py`**: A Python script that creates an interactive web application using the Streamlit framework. It loads the `Readmission_Model.pkl` model and allows users to input patient data to get a real-time prediction on whether the patient will be readmitted.

### Project Management

-   **`README.md`**: This file, providing a comprehensive guide to the project structure, files, and how to run the application.

---

## Data Flow

1.  The process starts with the raw **`hospital_readmissions.csv`**.
2.  The **`Replacing_A1C.ipynb`** notebook is used to analyze missing A1C values.
3.  The **`A1C_Model.ipynb`** notebook trains a model (**`A1C_Model.pkl`**) on data where the A1C result is known (**`hospital_with_actual_A1C.csv`**).
4.  This model is then used to predict and fill in missing A1C values, resulting in **`hospital_with_predicted_A1C.csv`**.
5.  Further preprocessing and cleaning in the **`Readmitted_Model.ipynb`** notebook lead to the creation of the **`hospital_readmissions_final.csv`** dataset.
6.  This final dataset is used to train the primary prediction model, which is saved as **`Readmission_Model.pkl`**.

---

## How to Run the Application

To run the web application and see the model in action, follow these steps:

**1. Install Dependencies:**

Make sure you have the required Python libraries installed.

```bash
pip install streamlit pandas numpy streamlit-option-menu Pillow scikit-learn
```

**2. Run the Streamlit App:**

Open your terminal, navigate to the project directory, and run the following command:

```bash
streamlit run Hospital_Streamlit.py
```

This will start a local web server and open the application in your browser. You can then navigate to the "Readmission" page, input patient details, and get a prediction from the model.