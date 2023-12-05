# AWS-Cloud-Resume-Challenge-CloudFormation
This repo has 2 yaml files that can be used to create basic versions of the resources necessary to complete the Cloud Resume Challenge in AWS using the AWS CLI and CloudFormation for automation rather than manually working through the console. You will need to add some attributes to the code in order for it to be specific to your project and include more advanced settings necessary for the challenge. 

1. Buy your custom domain name through Route 53 (or whatever service you prefer).
2. Request a public certificate to be stored in ACM that will be applied to your CloudFront distribution so that your website will utilize HTTPS.
   - You can do this manually or through the CLI
   - CLI:
     https://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request-public.html#request-public-cli
3. Utilize the CloudFormation template in this repo to:
   - Create a CloudFront distribution (you will need to enter the certificate information into the template)
   - Make sure the CloudFront distribution utilizes the custom URL 
   - Create an S3 bucket set to host a static website and whose URL points to the CloudFront distribution
   - Create a DynamoDB table
   - Create a Lambda function with a policy that allows it to get item and update item in the DynamoDB table
   - Create a Lambda function URL so that we can call the function in our JavaScript file
4. Upload your website files to the S3 bucket
   - make sure you update your JavaScript file to include the Lambda function URL

Instead of downloading the CLI to my computer I used CloudShell in the console which doesn't require authentication. 

CloudShell CLI command: aws cloudformation deploy --template-file FILENAME.yml --stack-name CREATE_A_NAME_FOR_YOUR_STACK --capabilities CAPABILITY_NAMED_IAM
