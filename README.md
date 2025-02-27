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
🛠 Step 1: Create the S3 bucket

Go to the S3 Console.
Click "Create bucket" → Name it (e.g., csv-upload-bucket).
Keep everything else default and click "Create bucket".
🛠 Step 2: Create the DynamoDB table

Go to the DynamoDB Console.
Click "Create table".
Table name: CSVDataTable.
Partition key: id → Type: String (We’ll generate unique IDs for each row).
Click "Create table".
🛠 Step 3: Create an IAM role for the Lambda function

Go to the IAM Console.
Click "Roles" → "Create role".
Select "Lambda" as the trusted entity.
Attach these policies:
AmazonS3ReadOnlyAccess (to read the CSV from S3).
AmazonDynamoDBFullAccess (to write to DynamoDB).
Click "Next" → "Create role".
Name it LambdaS3DynamoDBRole.
🛠 Step 4: Create the Lambda function

Go to the Lambda Console.
Click "Create function" → "Author from scratch".
Function name: S3ToDynamoDBFunction.
Runtime: Python 3.12 (or latest).
Execution role: Use existing role → Select LambdaS3DynamoDBRole.
Click "Create function".
📝 Step 5: Write the Lambda function 
which is lambdaFunc.py

🛠 Step 6: Add an S3 trigger to the Lambda function

Go to your S3ToDynamoDBFunction in the Lambda Console.
Click "Add trigger" → Select S3.
Bucket: csv-upload-bucket.
Event type: "PUT" (when a file is uploaded).
Click "Add".
🛠 Step 7: Upload a CSV file to S3

Open your csv-upload-bucket in the S3 console.
Click "Upload" → Select a CSV file like this:
csv
Copy
Edit
name,email
Alice,alice@example.com
Bob,bob@example.com
Charlie,charlie@example.com
Click "Upload".
🛠 Step 8: Check DynamoDB

Go back to the CSVDataTable in the DynamoDB Console.
Click "Explore table items".
You should see each row from the CSV file inserted as an item.
🛠 Step 9: (Optional) Clean up resources

Delete the S3 bucket.
Delete the DynamoDB table.
Delete the Lambda function.
Remove the IAM role if not needed elsewhere.
