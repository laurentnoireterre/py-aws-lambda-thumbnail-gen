# Description

Simple python program to create a thumbail from a S3 image. The function is triggered by a SNS message.

# Packaging

Clone the repository and zip its content
```
cd py-aws-lambda-thumbnail-gen
pip install -r requirements.txt -b ./
zip -r ../py-aws-lambda-thumbnail-gen.zip .
```

# Installation & Usage 

Connect to AWS console and create a Lambda having this properties:
   - Runtime: `Python 3.6`
   - Trigger: `SNS`
   - Role:
```
Allow: logs:CreateLogGroup
Allow: logs:CreateLogStream
Allow: logs:PutLogEvents
Allow: s3:*
Allow: sns:*

Resource: *
```
   - Environment variables: 
     - Add 2 environment variables named `imgSrcBucket` and `thumbDestBucket`, containing the S3 image source bucket name and S3 thumbnail destination bucket name

Deploy the function code by uploading the zip package.

You can use the `test-sample.json`file to test the function.