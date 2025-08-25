# Lambda Alert Processor

Create a simple Lambda function that takes a message as input and publishes it to SNS Topic.

Go To Lambda Service and create a Function.

## Lambda Function Creation
Author From Scratch 

Function name = alert_processor_lambda

Runtime= Python

<b> Set The Execution Role </b>

Select The role, here we will grant IAM role to Lambda that what action it can perform on our end.

Provide the role to Lambda Function 

Make a Role=" disaster-alert-lambda-role"

## Code For Lambda Function

Once the Function is created, will see the code editor in the console.

This code uses the AWS SDK to publish a message to the SNS topic.
``` sh

import json
import boto3

# Initialize the SNS client
sns_client = boto3.client('sns')

# Replace with your SNS topic ARN from Week 1
# Example: 'arn:aws:sns:us-east-1:123456789012:disaster-alert-test'
SNS_TOPIC_ARN = 'arn:aws:sns:YOUR_REGION:YOUR_ACCOUNT_ID:disaster-alert-test'

def lambda_handler(event, context):
    """
    Receives an event payload and publishes its message to an SNS topic.
    """
    try:
        # Parse the incoming message from the event
        body = json.loads(event['body'])
        message_text = body.get('message', 'No message provided.')

        # Publish the message to the SNS topic
        response = sns_client.publish(
            TopicArn=SNS_TOPIC_ARN,
            Message=message_text,
            Subject='Disaster Alert Notification'
        )

        return {
            'statusCode': 200,
            'body': json.dumps('Message published successfully!')
        }

    except Exception as e:
        print(f"Error publishing message: {e}")
        return {
            'statusCode': 500,
            'body': json.dumps(f'Error: {str(e)}')
        }
```