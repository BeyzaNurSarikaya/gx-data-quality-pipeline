# Amazon Sales Data Quality Monitoring with Great Expectations

<img width="739" height="254" alt="Screenshot 2026-02-12 153754" src="https://github.com/user-attachments/assets/e32996f2-8525-47c0-b596-b4ff59e87f6c" />

This project demonstrates a data quality monitoring pipeline using **Great Expectations (GX) v1.0+** and **Python**. It performs automated validation checks on Amazon Sales reports and triggers real-time alerts via **Slack Webhooks** when data quality issues are detected.

## 🚀 Features

* **Automated Validation:** Checks for null values, uniqueness, and value ranges using Great Expectations.
* **Modern GX Workflow:** Implements the latest Fluent Data Sources and Batch Definitions (GX 1.0+).
* **Slack Integration:** Sends instant alerts with failure summaries to a dedicated Slack channel.
* **Data Cleansing:** Basic preprocessing to ensure column consistency.

## 🛠️ Tech Stack

* **Language:** Python 3.12 (via Google Colab)
* **Libraries:** `great_expectations`, `pandas`, `requests`
* **Monitoring:** Slack Incoming Webhooks

## 📊 Dataset
The dataset used in this analysis contains over 128,000 rows of Amazon India sales data. 

- **Source:** You can download the dataset from Kaggle: [Amazon Sales Report Dataset](https://www.kaggle.com/datasets/mdsazzatsardar/amazonsalesreport)
- **Size:** ~128k rows and 24 columns.
- **Note:** Due to GitHub's file size limits, the raw CSV file is not included in this repository. To run the notebook, please download the CSV from the link above and upload it in the `/Colab Data` directory in Google Drive.


## 📋 Data Expectations

The pipeline validates the following rules:

* `order_id`: Must not be null and must be unique.
* `qty`: Must be a positive value (between 0 and max).
* `amount`: Must be a non-negative value.
* `status`: Must be within the predefined set of allowed Amazon shipping statuses.

## ⚙️ How to Run

1. Upload `Amazon Sale Report.csv` to your environment.
2. Install dependencies:
```bash
pip install great_expectations pandas requests

```


3. Configure your **Slack Webhook URL** in the script:
```python
MY_WEBHOOK_URL = "https://hooks.slack.com/services/YOUR/WEBHOOK/HERE"

```


4. Run the Jupyter Notebook cells to execute the validation.

## 🚨 Alert Example

When a validation fails, a notification like this is sent to Slack:

> 🚨 **GX Validation Failed!**
> ✅ Successful: 3
> ❌ Unsuccessful: 2
> 🛠 Errors: ExpectColumnValuesToBeUnique, ExpectColumnValuesToBeBetween



