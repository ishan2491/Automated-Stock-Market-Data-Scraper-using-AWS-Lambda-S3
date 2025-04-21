# 📈 Automated Stock Data Scraper using AWS Lambda & S3

This project is a simple yet powerful serverless web scraper that collects stock market data from [Groww](https://groww.in), such as:
- ✅ Company Name
- ✅ Open Price
- ✅ Previous Close Price
- ✅ Market Capitalization

The data is formatted into a JSON file and automatically stored in an AWS S3 bucket.

---

## 🔧 Tech Stack
- **Python 3**
- **AWS Lambda**
- **Amazon S3**
- **Amazon EventBridge**
- **Amazon CloudWatch**
- **BeautifulSoup** and **Requests**

---

## 🚀 Features
- Web scraper runs inside a Lambda function.
- Scheduled scraping every 12 hours via EventBridge.
- JSON-formatted output saved directly to S3.
- CloudWatch logs for easy monitoring and debugging.
- Error handling built-in for missing or unexpected data.

---

## 🧪 Example Output

Sample JSON (`stock_data.json`):
```json
[
  {
    "URL": "https://groww.in/us-stocks/nke",
    "Company Name": "Nike Inc",
    "Open Price": "$82.10",
    "Prev. Close": "$81.72",
    "Market Cap": "$120.87B"
  },
  ...
]
```

## 🛠 Setup Guide

1. **Prepare Lambda Function**
   * Create a folder and install dependencies:
   ```bash
   mkdir lambda_package && cd lambda_package
   pip install -r requirements.txt -t .
   ```
   * Add your `lambda_function.py` and zip everything:
   ```bash
   zip -r lambda_package.zip .
   ```
   * Upload to AWS Lambda.

2. **Increase Lambda Timeout**
   * Navigate to your Lambda function → Configuration → General Settings.
   * Set timeout to **30 seconds**.

3. **Configure EventBridge**
   * Create a rule to trigger Lambda every 12 hours.

4. **Store Data in S3**
   * Add your S3 bucket name in the script under `S3_BUCKET`.
