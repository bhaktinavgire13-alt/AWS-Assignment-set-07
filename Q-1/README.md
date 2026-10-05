Question 1 - Serverless Image Upload using S3 and Lambda
Design and implement a serverless image-upload workflow using Amazon S3 and AWS Lambda.
Upload an image to S3, automatically invoke Lambda through an S3 event, extract the uploaded
object's details, and record the execution information in CloudWatch Logs.

Objective:-
The main objective of this task is to create an image upload workflow using Amazon S3 and AWS Lambda. When an image is uploaded to the S3 bucket, the Lambda function should be triggered automatically.

AWS Services Used:-
- Amazon S3
- AWS Lambda
- AWS IAM
- Amazon CloudWatch

Architecture:-(added in screenshot folder)
User
↓
S3 Bucket
↓
S3 Event
↓
Lambda Function
↓
CloudWatch Logs

Steps Performed:-
1. I created an S3 bucket in the AWS Management Console.
2. I configured the bucket for uploading image files.
3. I created a Lambda function.
4. I created the required IAM permissions for the Lambda function.
5. I connected the S3 bucket with the Lambda function using an event notification.
6. I uploaded an image to the S3 bucket.
7. I checked whether the Lambda function was triggered after the upload.
8. I checked the Lambda execution details in CloudWatch Logs.

Testing:-
To test the setup, I uploaded an image file to the S3 bucket. After uploading the image, the S3 event triggered the Lambda function. I then checked the execution logs in CloudWatch.

Result:-
The S3 bucket and Lambda function were successfully connected, and the Lambda function was triggered when an image was uploaded.

Screenshots:-Saved in the `screenshots` folder.


Conclusion:-
I learned how S3 can be connected with Lambda to create a simple serverless workflow. The setup was tested by uploading an image and checking the Lambda execution.

code:-
import json
import urllib.parse
import boto3

s3 = boto3.client("s3")


def lambda_handler(event, context):

    print("===== S3 IMAGE UPLOAD EVENT =====")

    # Print the complete S3 event
    print(json.dumps(event, indent=2))

    # Get information from the S3 event
    record = event["Records"][0]

    bucket_name = record["s3"]["bucket"]["name"]

    object_key = urllib.parse.unquote_plus(
        record["s3"]["object"]["key"]
    )

    object_size = record["s3"]["object"]["size"]

    event_name = record["eventName"]

    event_time = record["eventTime"]

    print("Bucket Name:", bucket_name)
    print("Object Name:", object_key)
    print("Object Size:", object_size, "bytes")
    print("Event Name:", event_name)
    print("Event Time:", event_time)

    # Get additional information about the uploaded object
    response = s3.head_object(
        Bucket=bucket_name,
        Key=object_key
    )

    content_type = response.get("ContentType")

    print("Content Type:", content_type)

    print("===== PROCESSING COMPLETED =====")

    return {
        "statusCode": 200,
        "body": json.dumps({
            "bucket": bucket_name,
            "object": object_key,
            "size": object_size,
            "content_type": content_type
        })
    }