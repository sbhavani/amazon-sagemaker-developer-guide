# Troubleshoot Inference Recommender Errors<a name="neo-troubleshooting-compilation"></a>

This section contains information about how to understand and prevent common errors, the error messages they generate, and guidance on how to resolve these errors\. 

**Topics**
+ [How to troubleshoot](#neo-troubleshooting-compilation-how-to-use)
+ [Common errors](#neo-troubleshooting-compilation-infrastructure-errors)
+ [Check CloudWatch](#neo-troubleshooting-compilation-logs)

## How to troubleshoot<a name="neo-troubleshooting-compilation-how-to-use"></a>

Attempt to resolve your error by the going through the following steps:

1.  Check if you've covered all the pre-requisites to use Inference Recommender. See [Inference Recommender Prerequisites](https://docs.aws.amazon.com/sagemaker/latest/dg/inference-recommender-prerequisites.html).

2.  Check that you are able to deploy your Model from Registry to an Endpoint and it can indeed process your payloads without errors. See [Deploy a Model from the Registry](https://docs.aws.amazon.com/sagemaker/latest/dg/model-registry-deploy.html)

3.  When you kick off an Inference Recommender job, you should see Endpoints being created in Console and can review CloudWatch logs. See [Check CloudWatch]().

## Common errors<a name="neo-troubleshooting-compilation-framework-related-errors"></a>

| Error | Solution | 
| --- | --- | 
|   `Specify Domain in the Model Package version 1. Domain is a mandatory parameter for the job`   |  Make sure you provide the ML Domain or 'OTHER' if unknown.  | 
|  `Provided role ARN cannot be assumed and an AWSSecurityTokenServiceException error occurred.`  |  Make sure the execution role provided has the necessary permissions.  | 
|   `Specify Framework in the Model Package version 1. Framework is a mandatory parameter for the job`   |   Make sure you provide the ML Framework or 'OTHER' if unknown.   | 
|   `Users at the end of prev phase is 0 while initial users of current phase is 1`   |   |
|   `Total Traffic duration (across) should not be more than Job duration`   |   The total duration of all your Phases cannot exceed the Job duration.   |
|   `Burstable instance type ml.t2.medium is not allowed`   |   We don't support load testing on t2 instance family because burstable instances do not provide consistent performance.   |

## Check CloudWatch<a name="neo-troubleshooting-compilation-logs"></a>

1. Navigate to Amazon CloudWatch at [https://console\.aws\.amazon\.com/cloudwatch/](https://console.aws.amazon.com/cloudwatch/)\.

1. Select the region you created the compilation job from the **Region** dropdown list in the top right\.

1. In the navigation pane of the Amazon CloudWatch, choose **Logs**\. Select **Log groups**\.

1. Search for the log group called `/aws/sagemaker/CompilationJobs`\. Select the log group\.

1. Search for the logstream named after the compilation job name\. Select the log stream\.
