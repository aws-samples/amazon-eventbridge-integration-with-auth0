

# Build an Amazon QuickSight dashboard with Auth0 events

![QuickSight Dashboard](/images/screenshot.png "QuickSight Dashboard")


# amazon-eventbridge-integration-with-auth0

This project contains source code and supporting files for a serverless application that you can deploy with the SAM CLI. It includes the following files and folders.

## Requirements

* AWS CLI already configured with Administrator permission
* [NodeJS 12.x installed](https://nodejs.org/en/download/)
* An Auth0 Account with Amazon EVentBridge integration configured [Instructions](https://auth0.com/docs/logs/streams/aws-eventbridge#set-up-auth0-for-use-as-the-event-source)
* A front end application Auth0 [Quick Start](https://auth0.com/docs/quickstart/spa) 

## Installation Instructions

1. [Create an AWS account](https://portal.aws.amazon.com/gp/aws/developer/registration/index.html) if you do not already have one and login.

1. Clone the repo onto your local development machine using `git clone`.

1. From the command line, change directory into the root, then run:
```
sam build
sam deploy --guided
```
## How it works

1. Events are emitted from Auth0 when a user interacts with the login service on the front-end application.
1. These events are streamed into a custom SaaS event bus.
1. Event rules match events and send them downstream to a Lambda function target.
1. The receiving Lambda function performs some data housekeeping before writing an object to S3.  
1. These objects are captured by a QuickSight data source manifest file and used as datapoints on a QuickSight dashboard. 

Follow the prompts in the deploy process to set the stack name, AWS Region and other parameters.

## Auth0EventBusName

* Auth0EventBusName: A valid custom Event Bus for Auth0 Events (custom event bus names are genrated by the event source).

## Amazon QuickSight manifest file

* {your-s3-bucket-name}: in manifest.JSON, replace this token with your S3 bucket name

## Building the QuickSight dashboard

Before building your first visual you must:

:white_check_mark: Ensure that QuickSight has permission to access your S3 bucket. [Show me how](https://github.com/aws-samples/amazon-eventbridge-integration-with-auth0/blob/master/guides/Guide_QuickSight_S3_Permissions.md#granting-quicksight-permission-to-access-your-s3-bucket "QuickSight has permission to access your S3 bucket").

:white_check_mark: Create a new Data source. [Show me how](https://github.com/aws-samples/amazon-eventbridge-integration-with-auth0/blob/master/guides/Guide_QuickSight_S3_Permissions.md#creting-a-new-data-source "QuickSight has permission to access your S3 bucket").


## Creating visuals

### Example 1 – Connection channels

This visual enables you to understand your users’ preferred mechanism to log into your application.

![Pie Chart visual with multiple data points](https://raw.githubusercontent.com/aws-samples/amazon-eventbridge-integration-with-auth0/master/images/piechart.png "S3 Permissions Dashboard")
[Show me how to build this](/guides/Guide_QuickSight_Visuals#Example-1 "QuickSight Visuals").

:white_check_mark: Tip: Use calculated fields to build more complex visuals [Show me how](https://github.com/aws-samples/amazon-eventbridge-integration-with-auth0/blob/master/guides/Guide_QuickSight_Visuals#Calculated-Fields "QuickSight Visuals").


### Example 2 - trends
You can use this type of visual to show the trend in unsuccessful sign-ins, which could signify a problem with a recent UX release or user database connect.

![Trends with conditional formatting](https://raw.githubusercontent.com/aws-samples/amazon-eventbridge-integration-with-auth0/master/images/trends.png "Trends with conditional formatting")

[Show me how to build this](/guides/Guide_QuickSight_Visuals#Example-2 "QuickSight Visuals").


### Example 3 – comparisons over time 
This third example shows registrations versus sign-ins over time:
![Time based comparrisons](https://raw.githubusercontent.com/aws-samples/amazon-eventbridge-integration-with-auth0/master/images/timebasedComparisons.png "Time based comparrisons")
 
[Show me how to build this](/guides/Guide_QuickSight_Visuals#Example-3 "QuickSight Visuals").
