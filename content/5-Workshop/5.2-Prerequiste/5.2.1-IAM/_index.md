---
title: "AWS Account & IAM Setup"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.2.1. </b> "
---

#### Create an IAM user

Do not use the root account for daily development. Create a dedicated IAM user and enable MFA, following the Principle of Least Privilege.

1. Go to **IAM → Users → Create user**.
2. User name: `student-warning-dev`.
3. Enable **Provide user access to the AWS Management Console**.
4. Attach the policies needed for this workshop:
   - `AmazonS3FullAccess`
   - `AmazonDynamoDBFullAccess`
   - `AWSLambda_FullAccess`
   - `AmazonAPIGatewayAdministrator`
   - `CloudWatchFullAccess`
   - `AmazonSNSFullAccess`
   - `AmazonSageMakerFullAccess`

![IAM user creation]( /fcj-workshop-template/images/5-Workshop/5.2-Prerequisite/iam-user.png)

#### Enable MFA

Under **Security credentials → Multi-factor authentication (MFA)**, register an authenticator app (Google Authenticator / Authy). This secures the console login and improves the Security score of the project.

![Enable MFA]( /fcj-workshop-template/images/5-Workshop/5.2-Prerequisite/mfa.png)

#### Create Access Keys for the CLI

Under **Security credentials → Create access key → Command Line Interface (CLI)**, generate an Access Key ID and Secret Access Key.

{{% notice warning %}}
The Secret Access Key is shown **only once**. Save it securely and never commit it to Git or hard-code it into your source code.
{{% /notice %}}

#### The Lambda execution role

Lambda functions must not use hard-coded credentials. They assume an **execution role**. Create the role now:

1. **IAM → Roles → Create role**.
2. Trusted entity type: **AWS service**.
3. Use case: **Lambda**.
4. Attach:
   - `AWSLambdaBasicExecutionRole` (CloudWatch Logs)
   - `AmazonS3ReadOnlyAccess`
   - `AmazonDynamoDBFullAccess`
5. Role name: `StudentWarningLambdaRole`.

{{% notice info %}}
The role **must** trust `lambda.amazonaws.com`. If you create a role for a different service, it will not appear in the Lambda "existing role" dropdown.
{{% /notice %}}

![Lambda role trust relationship]( /fcj-workshop-template/images/5-Workshop/5.2-Prerequisite/lambda-role.png)