# Project-Resume-Classification

## Problem Statement & Business Objectives

Recruiters and HR teams often receive hundreds or thousands of resumes for a single job opening. Manually reviewing each resume is extremely time-consuming, prone to human error and bias, and inefficient — wasting valuable time, money, and productivity.

**Business Objective**  
The goal of this project is to build an automated **resume classification solution** that:  
- Significantly reduces manual effort in the HRM (Human Resource Management) process  
- Achieves high accuracy in categorizing resumes into job profiles  
- Enables minimal human intervention  
- Extracts key skills automatically to support faster shortlisting  

By classifying resumes into categories such as **PeopleSoft**, **SQL Developer**, **React JS Developer**, and **Workday**, recruiters can quickly filter and prioritize suitable candidates.

## Abstract

Resumes represent classic unstructured data — no standard format exists, layouts vary widely, sections have inconsistent headings, and important information is scattered. Parsing and classifying such documents manually is challenging.

This project develops a complete **resume classification pipeline** using **Natural Language Processing (NLP)** and **Machine Learning** to:  
- Extract clean text from PDF and DOCX resumes  
- Preprocess text (lowercasing, tokenization, stopword removal, lemmatization)  
- Classify resumes into predefined job categories using a trained model  
- Extract relevant technical and domain-specific **skills** using spaCy noun chunks and a custom skill list  

A **Streamlit web application** provides an intuitive interface for uploading multiple resumes, viewing predictions, extracted skills, and filtering by category.

**Key achievements**:  
- Built and compared multiple ML classifiers (KNN, Decision Tree, Random Forest, SVM, Logistic Regression, Naive Bayes, Bagging, AdaBoost, Gradient Boosting)  
- Deployed a production-ready Decision Tree model with ~85% test accuracy (see notebook for details)  
- Added practical skill extraction to enhance usability beyond simple classification  

## Business Value

- Automates the initial screening stage → saves 70–90% of manual review time  
- Improves consistency and reduces bias in shortlisting  
- Helps recruiters focus on high-potential candidates  
- Extracts skills automatically → enables better keyword-based matching and candidate profiling  
- Scalable for large volumes of applications  

## Approach & Methodology

1. **Data Collection**  
   - Labeled resumes collected in folders by category (PeopleSoft, React JS Developer, SQL Developer, Workday)  

2. **Text Extraction & Cleaning**  
   - PDF → pdfplumber + PyPDF2  
   - DOCX → docx2txt  
   - Preprocessing: lowercase, remove URLs/numbers/HTML, tokenization, stopword removal (spaCy), lemmatization (NLTK)  

3. **Feature Engineering**  
   - TF-IDF Vectorization for classification  
   - spaCy noun chunks + custom skill list for skill extraction  

4. **Model Building & Comparison**  
   - Algorithms evaluated in `Resume_Project.ipynb`:  
     - K-Nearest Neighbors  
     - Decision Tree (final choice for deployment)  
     - Random Forest  
     - Support Vector Machine  
     - Logistic Regression  
     - Bagging Classifier  
     - AdaBoost Classifier  
     - Gradient Boosting  
     - Naive Bayes  
   - Best model serialized using joblib  

5. **Application Layer**  
   - Streamlit app (`app.py`) for file upload, batch processing, category filtering, and skill display  

## Technologies & Libraries

- **Core**: Python 3, scikit-learn, joblib  
- **NLP**: spaCy (en_core_web_sm), NLTK (lemmatizer, stopwords)  
- **Parsing**: pdfplumber, PyPDF2, docx2txt  
- **Vectorization**: TfidfVectorizer  
- **Web App**: Streamlit  
- **Data Handling**: pandas  

## Results & Model Performance

- **Decision Tree** (deployed model): ~85% accuracy on test set  
- Multiple algorithms compared — see `Resume_Project.ipynb` for confusion matrices, classification reports, and accuracy plots  
- Skill extraction successfully identifies one-word and multi-word skills (e.g., "Python", "Machine Learning", "SQL Server")
