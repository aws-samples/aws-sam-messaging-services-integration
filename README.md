# Messaging services in serverless applications

The examples in this repo are used in related messaging blog posts. You can read the blog posts at:
- https://aws.amazon.com/blogs/compute/choosing-between-messaging-services-for-serverless-applications/
- https://aws.amazon.com/blogs/compute/building-resilient-no-code-serverless-patterns-by-combining-messaging-services/

Important: these applications use various AWS services and there are costs associated with these services after the Free Tier usage. Please see the [AWS Pricing page](https://aws.amazon.com/pricing/) for details. You are responsible for any AWS costs incurred. No warranty is implied in these examples.

```bash
.
├── README.MD          <-- This instructions file
├── 1-sqs              <-- Integrates an SQS queue with a Lambda function
└── 2-sns              <-- Integrates an SNS topic with a Lambda function
└── 3-eventbridge      <-- Creates an EventBridge rule with a Lambda function as a target
└── 4-sns-sqs          <-- Subscribes an SQS queue to an SNS topic
└── 5-eventbridge-sns  <-- Creates an EventBridge rule with an SNS topic as a target
└── 6-eventbridge-sqs  <-- Creates an EventBridge rule with an SQS queue as a target
```

## Requirements

* AWS CLI already configured with Administrator permission
* [NodeJS 12.x installed](https://nodejs.org/en/download/)

## Installation Instructions

1. [Create an AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) if you do not already have one and login.

1. Clone the repo onto your local development machine using `git clone`.

1. In each example's directory, from the command line, run:
```
sam deploy --guided
```
Follow the prompts in the deploy process to set the stack name and AWS Region.

## Testing

The SAM deployment provides key resource names in the output.

Invoke a Lambda function from the CLI using:
```
aws lambda invoke --function-name << your-function-name >> response.json
```
Tail the function's CloudWatch logs using:
```
sam logs -n sqs-example-QueueConsumerFunction-M1GVFCEH030D --tail
```
With a test event in a local `event.json` file, send the event to the Amazon EventBridge using:
```
aws events put-events --entries file://event.json
```

## Questions?

Please raise an issue on this repo.

==============================================

Copyright 2020 Amazon.com, Inc. or its affiliates. All Rights Reserved.

SPDX-License-Identifier: MIT-0
