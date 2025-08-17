## Week 1
* Project Setup: AWS account setup, IAM user/role creation.

* SNS Topic Creation: Define and create initial SNS topics(e.g: disaster-alert-test).

* Basic SNS Testing: Manually publish messages to SNS topics and subscribe an email/phone number to test deliver.

### 1. AWS account setup, IAM user/role creation
* <b> AWS Account Setup</b>: Create AWS Account.
* <b> IAM User/Role Creation: </b>
    
    Create IAM user for project, instead of using the root account, creating IAM user is a best practise for security.

### 2. SNS Topic Creation

This is the core of your notification system.

* <b>Define and create initial SNS topics</b>: In the AWS SNS console, you'll create one or more topics. A topic is a communication channel that messages are sent to. In this project we'll start with general topic like disaster-alert-test. We can later create more specific topics like disaster-alert-flood and disaster-alert-fire to allow for more granular subscriptions.

### 3. Baisc SNS Testing 
This steps is to confirm that communication channel is working as excepted.

* <b> Manually publish message to SNS topics:</b> Once we have a topic, we will go into the SNS console and manually publish a test message. This stimulates an alert being triggered.

* <b> Subscribe an email/phone number:</b>  Before publsihing the message, we'll subscribe our own email address and a phone number to the topic. This will show excatly how the system delivers notifications. we'll receive a confirmation link in our email and a text message on our phone.

* <b> Verifiy Delivery:</b> After publsihing the test message, we should receive it on our subscribed email inbox and phone number. This will confirm that SNS setup is working correctly and is ready for the next phase.