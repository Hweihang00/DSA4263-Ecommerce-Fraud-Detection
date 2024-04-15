<!-- omit in toc -->
# DSA4263 Project: Identification of Fraudulent Transactions using Machine Learning

This repository contains the code that are created for the purposes of detecting fraduluent transactions from an E-commerce Fraud Dataset.

## Description

The exponential growth of e-commerce platforms has brought a corresponding rise in fraudulent activities, necessitating the development of robust detection techniques. In this report, we investigate the domain of e-commerce fraud detection, using machine learning frameworks for predictive analysis. We are focusing on a dataset sourced from Kaggle, comprising essential features of distinguishing fraudulent transactions, such as fingerprints and IP addresses. We examined baseline models such as Decision Trees and Logistic Regression for their performances - while Decision Trees had commendable accuracy, it faltered for the precision and recall metrics, necessitating further refinement. Conversely, Logistic Regression struggles to identify fraudulent transactions, showing limitations in the domain. Challenger models - Random Forest and XGBoost - were introduced as well. After hyperparameter tuning and addressing for the class imbalance in the dataset, XGBoost emerged as the better performing model, demonstrating enhanced recall score, which are crucial for identifying fraudulent transactions. Given the direct implications of fraud detection on mitigating financial losses, it is significant to prioritise recall. Despite XGBoost’s superior recall and computational efficiency, the interpretability of Random Forest proves to be a viable alternative, especially in regulatory compliance. In conclusion, the report looks into the role of machine learning in e-commerce fraud detection. By leveraging on advanced algorithms like XGBoost, businesses can safeguard against fraudulent activities, ensuring the integrity of online transactions and fostering a secure marketplace for all.


<!-- omit in toc -->
## Table of Content:

- [Folder Structure](#folder-structure)
- [Software Requirements](#software-requirements)
- [Installation](#installation)
- [Data](#data)
- [Models](#models)
- [Results](#results)
- [Team Members](#team-members)

## Folder Structure

```
.
├── data/
│   ├── raw/
│   │   ├── Fraud_Data.csv
│   │   ├── IpAddress_to_Country.csv
│   ├── processed/
│   │   ├── df.csv
├── descriptions/
│   ├── datadictionary.txt
├── notebooks/
│   ├── ecommerce_fraud.ipynb
│   ├── main.ipynb
├── LICENSE
├── README.md
└── requirements.txt
```

* `data` - Contains the raw and processed data files where `Fraud_Data.csv` and `IpAddress_to_Country.csv` are the raw data files under `raw/` folder and `df.csv` is the processed data file after feature selection and engineering under `processed/` folder. 

* `descriptions` - Contains `datadictionary.txt` which is the txt file that has detailed information about the content and attribute of data within the dataset.

* `main.ipynb` - The .ipynb file that contains data preprocessing, exploratory data analysis, feature engineering as well as all the models and evaluation.

* `requirements.txt` - Contains the Python libraries that needs to be downloaded within the machine for the notebook to work.


## Software Requirements

1. Python version $\geq 3.8$

## Installation
### Cloning Repository

To clone the repository into your device, you can run the following command:

```bash
git clone https://github.com/Hweihang00/DSA4263-Ecommerce-Fraud-Detection.git
```

After it has been successfully cloned, you should see a folder `DSA4263-Ecommerce-Fraud-Detection` created.

### Install Software / Packages

After the repository has been cloned over successfully, run the following commands to install the relevant software or packages.

1. **Installing packages required**

*(If you are running on Windows, change `pip3` to `pip`)*

Ensure that you are within the `DSA4263-Ecommerce-Fraud-Detection` folder before running the following command.

```bash
pip3 install -r requirements.txt
```

## Data
### Description
The dataset, sourced from Kaggle, consists of two CSV files: Fraud_Data.csv and IpAddress_to_Country.csv. Fraud_Data.csv contains 151,112 entries across 11 columns, including a class label indicating fraud (1) or non-fraud (0). Key features, such as sign-up and purchase times, offer insights into fraudulent behavior. Additional features like User ID, Device ID, and IP address aid in detecting suspicious activities. The class distribution shows a significant imbalance, with fraudulent transactions representing only 9% of the dataset.

### Data Dictionary
| Feature Name            | Data Type | Description                                                                                                      |
|-------------------------|-----------|------------------------------------------------------------------------------------------------------------------|
| purchase_value          | Integer   | The value of the item purchased in the transaction                                                                |
| age                     | Integer   | The age of the user who made the transaction                                                                       |
| class                   | Integer   | A binary column that indicates whether the transaction was fraudulent or non-fraudulent                          |
| signup_month            | Integer   | The month that the user who made the transaction signed up to the e-commerce platform                              |
| signup_day              | Integer   | The day that the user who made the transaction signed up to the e-commerce platform                                |
| purchase_day            | Integer   | The day that the user made the transaction                                                                          |
| signup_purchase_time_diff | Integer | The time difference in seconds between the timestamp of when the user signed up to the platform and when they made this transaction |
| num_users_per_device    | Integer   | The count of unique user IDs associated with the same device ID across transactions for the device ID that made the transaction           |
| num_unique_ips_per_device | Integer | The count of unique user IP Addresses associated with the same device ID across transactions for the device ID that made the transaction     |
| high_value_purchase     | Integer   | A flag for transactions where the purchase value exceeds twice the average purchase value associated with the respective device ID for the device ID that made the transaction             |
| frequent_purchase       | Integer   | A flag that indicates whether the purchase value of this transaction falls within the top three most frequently occurring values in the dataset          |
| browser_Chrome          | Integer   | Indicates if the browser used for this transaction is Chrome (1) or otherwise (0)                                 |
| browser_FireFox         | Integer   | Indicates if the browser used for this transaction is Firefox(1) or otherwise (0)                                  |
| browser_Opera           | Integer   | Indicates if the browser used for this transaction is Opera(1) or otherwise (0)                                    |
| browser_Safari          | Integer   | Indicates if the browser used for this transaction is Safari(1) or otherwise (0)                                   |
| sex_F                   | Integer   | Indicates if the gender of the user who made this transaction is Female (1) or otherwise (0)                     |
| source_Ads              | Integer   | Indicates if the source that the user who made the transaction came to the platform is through Ads (1) or otherwise (0)                     |
| source_Direct           | Integer   | Indicates if the source that the user who made the transaction came to the platform Direct (1) or otherwise (0)                     |
| country_encoded         | Float     | Indicates a numerical encoding of the 'country' feature after one-hot encoding. Each country is assigned a unique numerical value               |


- Kaggle dataset: [link](https://www.kaggle.com/datasets/vbinh002/fraud-ecommerce/data)


## Models
The baseline models we attempted were Logistic Regression and Decision Trees. We implemented challenger models such as Random Forest, XGBoost, and Neural Network for comparision.

## Results
We will be predominantly focusing on the model's performance in terms of recall as recall captures the model’s ability to correctly identify fraudulent transactions among all actual fraudulent transactions.

- Baseline Models
  - Logistic Regression: Accuracy of 90.6%, 0.0% for Precision, Recall, F1 Score.
  - Decision Trees: Accuracy of 91.9%, Precision of 56.6%, Recall of 58.8%, F1 Score of 57.7%
- Challenger Models
  - Random Forest: Accuracy of 95%, Precision of 81.7%, Recall of 59.4%, F1 Score of 68.8%
  - XGBoost: Accuracy of 91.5%, Precision of 53.5%, Recall of 71.6%, F1 Score of 61.2%
  - Neural Network: Accuracy of 91%, Precision of 53%, Recall of 71%, F1 Score 61%

## Team Members

1. Chong Wan Fei  (**Handle**: [wanfeijong](https://github.com/wanfeijong))

2. Choo Wei Jie, Darren (**Handle**: [dchoo99](https://github.com/dchoo99))

3. Han Weihang (**Handle**: [Hweihang00](https://github.com/Hweihang00))

4. Janelle Tay Xin Yi (**Handle**: [ddalgiie](https://github.com/ddalgiie))

5. Jeong Won Choi (**Handle**: [JeongwonChoi54](https://github.com/JeongwonChoi54))

6. Ng Zheng Li (**Handle**: [Zhengli00](https://github.com/Zhengli00))
