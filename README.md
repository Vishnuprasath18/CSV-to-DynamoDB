# CSV-to-DynamoDB

# S3 to DynamoDB Automation with AWS Lambda

This project automates the process of uploading CSV data from an S3 bucket to a DynamoDB table using an AWS Lambda function.

## How it works
1. A CSV file is uploaded to an S3 bucket.
2. This triggers a Lambda function.
3. The Lambda function reads the CSV file and inserts its data into a DynamoDB table row by row.

## AWS Services Used
- S3 (Simple Storage Service)
- Lambda
- DynamoDB
- IAM (Identity and Access Management)
- CloudWatch (For logging)

## Setup and Deployment
1. Create an S3 bucket and a DynamoDB table.
2. Create an IAM role with S3 read access and DynamoDB write access.
3. Deploy the `lambda_function.py` to AWS Lambda.
4. Add an S3 trigger for the bucket to call the Lambda function on file upload.
5. Upload a CSV file and see the data appear in DynamoDB.

## Sample CSV Format
```csv
name,email
Alice,alice@example.com
Bob,bob@example.com
Charlie,charlie@example.com
