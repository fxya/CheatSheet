# AWS Cheat Sheet for Backend Java Developers

### 1. AWS SDK Configuration
To interact with AWS services from your Java application, you need to configure the AWS SDK. Here's an example of configuring the AWS SDK using the `DefaultAWSCredentialsProviderChain`:

```java
import software.amazon.awssdk.auth.credentials.DefaultAWSCredentialsProviderChain;
import software.amazon.awssdk.regions.Region;
import software.amazon.awssdk.services.s3.S3Client;

// Configure AWS SDK
S3Client s3Client = S3Client.builder()
        .region(Region.US_EAST_1)
        .credentialsProvider(DefaultAWSCredentialsProviderChain.getInstance())
        .build();
```

### 2. Amazon S3 - Object Storage
Amazon S3 (Simple Storage Service) is a scalable object storage service. Here's an example of uploading an object to S3:

```java
import software.amazon.awssdk.core.sync.RequestBody;
import software.amazon.awssdk.services.s3.model.PutObjectRequest;

// Upload object to S3
PutObjectRequest putObjectRequest = PutObjectRequest.builder()
        .bucket("my-bucket")
        .key("my-object-key")
        .build();
s3Client.putObject(putObjectRequest, RequestBody.fromFile(new File("path/to/file")));
```

### 3. AWS Lambda - Serverless Functions
AWS Lambda lets you run your code without provisioning or managing servers. Here's an example of creating a Lambda function:

```java
import software.amazon.awssdk.services.lambda.LambdaClient;
import software.amazon.awssdk.services.lambda.model.CreateFunctionRequest;

// Create a Lambda function
CreateFunctionRequest createFunctionRequest = CreateFunctionRequest.builder()
        .functionName("my-function")
        .runtime("java11")
        .handler("com.example.MyHandler::handleRequest")
        .role("arn:aws:iam::123456789012:role/my-lambda-role")
        .code(new S3Location("my-bucket", "my-object-key"))
        .build();
LambdaClient lambdaClient = LambdaClient.builder().region(Region.US_EAST_1).build();
lambdaClient.createFunction(createFunctionRequest);
```

### 4. Amazon DynamoDB - NoSQL Database
Amazon DynamoDB is a fast and flexible NoSQL database service. Here's an example of querying data from DynamoDB:

```java
import software.amazon.awssdk.services.dynamodb.DynamoDbClient;
import software.amazon.awssdk.services.dynamodb.model.AttributeValue;
import software.amazon.awssdk.services.dynamodb.model.GetItemRequest;
import software.amazon.awssdk.services.dynamodb.model.GetItemResponse;

// Query data from DynamoDB
GetItemRequest getItemRequest = GetItemRequest.builder()
        .tableName("my-table")
        .key(Map.of("id", AttributeValue.builder().s("my-item-id").build()))
        .build();
DynamoDbClient dynamoDbClient = DynamoDbClient.builder().region(Region.US_EAST_1).build();
GetItemResponse getItemResponse = dynamoDbClient.getItem(getItemRequest);
```

### 5. Amazon SQS - Message Queue Service
Amazon SQS (Simple Queue Service) is a fully managed message queuing service. Here's an example of sending a message to an SQS queue:

```java
import software.amazon.awssdk.services.sqs.SqsClient;
import software.amazon.awssdk.services.sqs.model.SendMessageRequest;

// Send message to SQS queue
SendMessageRequest sendMessageRequest = SendMessageRequest.builder()
        .queueUrl("my-queue-url")
        .messageBody("Hello, SQS!")
        .build
SqsClient sqsClient = SqsClient.builder().region(Region.US_EAST_1).build();
sqsClient.sendMessage(sendMessageRequest);
```

### 6. Amazon SNS - Pub/Sub Messaging Service
Amazon SNS (Simple Notification Service) is a fully managed pub/sub messaging service. Here's an example of publishing a message to an SNS topic:

```java
import software.amazon.awssdk.services.sns.SnsClient;
import software.amazon.awssdk.services.sns.model.PublishRequest;

// Publish message to SNS topic
PublishRequest publishRequest = PublishRequest.builder()
        .topicArn("my-topic-arn")
        .message("Hello, SNS!")
        .build();
SnsClient snsClient = SnsClient.builder().region(Region.US_EAST_1).build();
snsClient.publish(publishRequest);
```

### 7. Amazon SES - Email Service
Amazon SES (Simple Email Service) is an email service. Here's an example of sending an email using Amazon SES:

```java
import software.amazon.awssdk.services.ses.SesClient;
import software.amazon.awssdk.services.ses.model.SendEmailRequest;

// Send email using Amazon SES
SendEmailRequest sendEmailRequest = SendEmailRequest.builder()
        .source("my-email-address")
        .destination(Destination.builder().toAddresses("a@b.com").build())
        .message(Message.builder()
                .subject(Content.builder().data("Hello, SES!").build())
                .body(Body.builder().text(Content.builder().data("Hello, SES!").build()).build())
                .build())
        .build();
SesClient sesClient = SesClient.builder().region(Region.US_EAST_1).build();
sesClient.sendEmail(sendEmailRequest);
```

### 8. Amazon API Gateway - API Management Service
Amazon API Gateway is a fully managed service for creating, publishing, maintaining, monitoring, and securing APIs. Here's an example of creating an API Gateway REST API:

```java
import software.amazon.awssdk.services.apigateway.ApiGatewayClient;
import software.amazon.awssdk.services.apigateway.model.CreateRestApiRequest;

// Create API Gateway REST API
CreateRestApiRequest createRestApiRequest = CreateRestApiRequest.builder()
        .name("my-api")
        .build();
ApiGatewayClient apiGatewayClient = ApiGatewayClient.builder().region(Region.US_EAST_1).build();
apiGatewayClient.createRestApi(createRestApiRequest);
```

### 9. Amazon CloudWatch - Monitoring Service
Amazon CloudWatch is a monitoring service for AWS cloud resources and the applications you run on AWS. Here's an example of creating a CloudWatch alarm:

```java
import software.amazon.awssdk.services.cloudwatch.CloudWatchClient;
import software.amazon.awssdk.services.cloudwatch.model.PutMetricAlarmRequest;

// Create CloudWatch alarm
PutMetricAlarmRequest putMetricAlarmRequest = PutMetricAlarmRequest.builder()
        .alarmName("my-alarm")
        .comparisonOperator(ComparisonOperator.GREATER_THAN_THRESHOLD)
        .evaluationPeriods(1)
        .metricName("my-metric")
        .namespace("my-namespace")
        .period(60)
        .statistic(Statistic.AVERAGE)
        .threshold(1.0)
        .actionsEnabled(false)
        .build();
CloudWatchClient cloudWatchClient = CloudWatchClient.builder().region(Region.US_EAST_1).build();
cloudWatchClient.putMetricAlarm(putMetricAlarmRequest);
```

### 10. Amazon CloudFront - Content Delivery Network
Amazon CloudFront is a content delivery network (CDN) service. Here's an example of creating a CloudFront distribution:

```java
import software.amazon.awssdk.services.cloudfront.CloudFrontClient;
import software.amazon.awssdk.services.cloudfront.model.CreateDistributionRequest;

// Create CloudFront distribution
CreateDistributionRequest createDistributionRequest = CreateDistributionRequest.builder()
        .distributionConfig(DistributionConfig.builder()
                .callerReference("my-caller-reference")
                .defaultCacheBehavior(DefaultCacheBehavior.builder()
                        .forwardedValues(ForwardedValues.builder()
                                .queryString(false)
                                .cookies(CookiePreference.builder().forward(CookieForwardPolicy.none).build())
                                .build())
                        .targetOriginId("my-target-origin")
                        .viewerProtocolPolicy(ViewerProtocolPolicy.REDIRECT_TO_HTTPS)
                        .build())
                .enabled(true)
                .origins(Origins.builder()
                        .items(Origin.builder()
                                .domainName("my-origin")
                                .id("my-target-origin")
                                .build())
                        .quantity(1)
                        .build())
                .build())
        .build();
CloudFrontClient cloudFrontClient = CloudFrontClient.builder().region(Region.US_EAST_1).build();
cloudFrontClient.createDistribution(createDistributionRequest);
```

### 11. Amazon CloudFormation - Infrastructure as Code
Amazon CloudFormation is a service that helps you model and set up your AWS resources so that you can spend less time managing those resources and more time focusing on your applications that run in AWS. Here's an example of creating a CloudFormation stack:

```java
import software.amazon.awssdk.services.cloudformation.CloudFormationClient;
import software.amazon.awssdk.services.cloudformation.model.CreateStackRequest;

// Create CloudFormation stack
CreateStackRequest createStackRequest = CreateStackRequest.builder()
        .stackName("my-stack")
        .templateBody("my-template-body")
        .build();
CloudFormationClient cloudFormationClient = CloudFormationClient.builder().region(Region.US_EAST_1).build();
cloudFormationClient.createStack(createStackRequest);
```

### 12. Amazon CloudTrail - Logging Service
Amazon CloudTrail is a logging service that records the API calls and events made in your AWS account. Here's an example of creating a CloudTrail trail:

```java
import software.amazon.awssdk.services.cloudtrail.CloudTrailClient;
import software.amazon.awssdk.services.cloudtrail.model.CreateTrailRequest;

// Create CloudTrail trail
CreateTrailRequest createTrailRequest = CreateTrailRequest.builder()
        .name("my-trail")
        .s3BucketName("my-bucket")
        .build();
CloudTrailClient cloudTrailClient = CloudTrailClient.builder().region(Region.US_EAST_1).build();
cloudTrailClient.createTrail(createTrailRequest);
```