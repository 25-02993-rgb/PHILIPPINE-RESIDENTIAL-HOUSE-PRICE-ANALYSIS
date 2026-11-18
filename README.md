# PHILIPPINE-RESIDENTIAL-HOUSE-PRICE-ANALYSIS
*Application of Linear Algebra in Predicting Residential House Asking Prices*

## **A. Proposed Study**

This project aims to analyze residential house asking prices in the Philippines using Linear Algebra and Multiple Linear Regression. It will examine how property characteristics, such as floor area, lot area, number of bedrooms, and number of bathrooms, influence the asking prices of residential houses.

The study will use the Philippines Real Estate Asking Prices dataset, which contains property listings from different regions in the country. By organizing the data into matrices and applying Linear Algebra concepts, the group will examine relationships among property features, identify patterns, and develop a regression model to estimate house asking prices.

The main goal is to demonstrate how mathematical and computational techniques can be applied to Philippine housing data. The findings may help explain how property characteristics are associated with residential asking prices and provide insights relevant to housing affordability and sustainable communities.

## **B. Objectives**

1. Organize residential property data into numerical matrices using Python and NumPy.
2. Apply Linear Algebra operations to examine relationships among property characteristics.
3. Determine the rank and linear independence of the selected numerical features.
4. Apply standardization and Principal Component Analysis (PCA) to prepare the data for analysis.
5. Develop a Multiple Linear Regression model to estimate residential house asking prices.
6. Evaluate and compare regression models using RMSE and R².
7. Examine how the results relate to housing affordability and SDG 11 – Sustainable Cities and Communities.

## **C. Dataset Information**

| Information                 | Details                                                                                                             |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Dataset Name                | Philippines Real Estate Asking Prices                                                                               |
| Dataset Source              | Hugging Face – covaga                                                                                               |
| Dataset Link                | [View Dataset](https://huggingface.co/datasets/covaga/Philippines-Real-Estate-Asking-Prices?utm_source=chatgpt.com) |
| Total Dataset Observations  | 241,496 property listings                                                                                           |
| Selected Population         | Residential houses listed for sale in the Philippines                                                               |
| Initial House Observations  | 97,133 house listings                                                                                               |
| Number of Selected Features | 3 numerical independent variables                                                                                   |
| Target Variable             | `price_php`                                                                                                         |
| File Format                 | CSV (compressed) / Parquet                                                                                          |
| Observation Period          | February 22 – August 30, 2026                                                                                       |

### **Dataset Description**

The dataset contains residential and commercial property listings from different regions in the Philippines. It includes information about asking prices, floor area, lot area, bedrooms, bathrooms, and property locations.

For this project, the group will focus exclusively on residential houses. From the available variables, three numerical features will be selected to examine their relationship with house asking prices.

The initial population consists of 97,133 house listings. The final sample size will be determined after filtering incomplete records, invalid measurements, and duplicate listings.

The dataset contains asking prices rather than confirmed property transaction prices.&#x20;

## **D. Description of Variables**

| Variable Name | Description                                        | Data Type | Role        |
| ------------- | -------------------------------------------------- | --------- | ----------- |
| `sqm`         | Total floor area of the house in square meters     | Numerical | Independent |
| `bedrooms`    | Number of bedrooms                                 | Numerical | Independent |
| `bathrooms`   | Number of bathrooms                                | Numerical | Independent |
| `price_php`   | Residential house asking price in Philippine pesos | Numerical | Dependent   |

### **Justification of the Selected Variables**

The selected independent variables represent important physical characteristics of residential houses.

Floor area measures the available indoor space, while the number of bedrooms and bathrooms represents the house's capacity and facilities.

These characteristics may influence the asking price of a property. Therefore, they will be used as independent variables to estimate the residential house asking price.

The target variable is `price_php` because the main purpose of the project is to predict the asking price based on the selected property characteristics.

*Note: `lot_area_m2` is available in the dataset but is not included in the initial model because it has missing values in many listings. It can be considered later if sufficient complete records are available.*

## **E. Sample Dataset**

The following are four example house records visible in the dataset preview.

| Observation      | Floor Area (sqm) | Bedrooms | Bathrooms | Asking Price (₱) |
| ---------------- | ---------------- | -------- | --------- | ---------------- |
| 1 – Silang       | 165              | 3        | 3         | 14,892,000       |
| 2 – Marikina     | 413              | 4        | 4         | 33,184,000       |
| 3 – Angeles City | 260              | 3        | 3         | 21,488,000       |
| 4 – Cebu City    | 415              | 3        | 5         | 54,468,000       |

Source: Dataset preview. These are example records, not the final cleaned sample.&#x20;



### **Example of the Proposed Matrix Representation**

Using the four example observations and three independent variables, the feature matrix can be represented as:

**Feature Matrix (X)**

\\[ X = \begin{bmatrix} 165&3&3\\\ 413&4&4\\\ 260&3&3\\\ 415&3&5 \end{bmatrix} \\]

**Target Vector (Y)**

\\[ Y = \begin{bmatrix} 14892000\\\ 33184000\\\ 21488000\\\ 54468000 \end{bmatrix} \\]

The sample feature matrix has four rows and three columns. Each row represents one residential house, while each column represents a selected property characteristic.

The final feature matrix will contain all valid observations remaining after data cleaning.

## **F. Proposed Application of Linear Algebra Concepts**

| Linear Algebra Concept             | Proposed Application                                                                                                                                                                           |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Matrices**                       | Organize floor area, bedrooms, and bathrooms into a feature matrix X. Store house asking prices separately as the target vector Y. Compute the transpose and matrix multiplication \\(X^TX\\). |
| **Vector Spaces**                  | Examine the column space, matrix rank, and linear independence of the selected property characteristics.                                                                                       |
| **Linear Transformations**         | Standardize the numerical features so that variables with different measurement scales can be compared fairly.                                                                                 |
| **Determinants**                   | Calculate the determinant of \\(X^TX\\) using standardized training features to examine matrix invertibility.                                                                                  |
| **Eigenvalues and Eigenvectors**   | Construct the covariance matrix and calculate its eigenvalues and eigenvectors to identify the principal directions of variation in property characteristics.                                  |
| **Diagonalization**                | Apply matrix diagonalization using eigenvalue decomposition and reconstruct the covariance matrix.                                                                                             |
| **Dimensionality Reduction (PCA)** | Reduce the number of features while retaining at least 95% of the variance, if achievable.                                                                                                     |
| **Regression Model**               | Apply Ordinary Least Squares regression to predict house asking prices using the full standardized features and reduced principal components. Evaluate both models using RMSE and R².          |

### **Example of the Proposed Regression Model**

The group will use Multiple Linear Regression to estimate residential house asking prices based on the selected independent variables.

The general equation is:

\\[ Y=\beta_0+\beta_1X_1+\beta_2X_2+\beta_3X_3+\epsilon \\]

Where:

- \\(Y\\) = Predicted house asking price
- \\(X_1\\) = Floor area
- \\(X_2\\) = Number of bedrooms
- \\(X_3\\) = Number of bathrooms
- \\(\beta_0\\) = Intercept
- \\(\beta_1,\beta_2,\beta_3\\) = Regression coefficients
- \\(\epsilon\\) = Error term

The group will develop two regression models:

1. **Full Feature Model** – Uses all three standardized independent variables.
2. **PCA-Reduced Model** – Uses principal components selected based on the 95% cumulative explained variance requirement.

The two models will be evaluated and compared using Root Mean Squared Error (RMSE) and the coefficient of determination (R²).

## **G. References**

1\. covaga. (2026). *Philippines Real Estate Asking Prices* [Dataset]. Hugging Face. [https://huggingface.co/datasets/covaga/Philippines-Real-Estate-Asking-Prices](https://huggingface.co/datasets/covaga/Philippines-Real-Estate-Asking-Prices?utm_source=chatgpt.com)

2\. United Nations. (n.d.). *Goal 11: Sustainable cities and communities*. [https://sdgs.un.org/goals/goal11](https://sdgs.un.org/goals/goal11?utm_source=chatgpt.com)

3\. OpenAI. (n.d.). *Python documentation and libraries used for numerical computing*. [https://numpy.org/doc/](https://numpy.org/doc/?utm_source=chatgpt.com)
