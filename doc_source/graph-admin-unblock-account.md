# Enabling a member account that is Not enabled<a name="graph-admin-unblock-account"></a>

After a member account accepts an invitation, Amazon Detective checks whether it can enable the member account\. If Detective cannot enable the member account, then it sets the member account status to **Not enabled**\. This can happen for one of the following reasons\.
+ The member account has not been an Amazon GuardDuty customer for at least 48 hours\.
+ Detective is verifying the data volume for the member account\.
+ The member account data would cause the behavior graph data rate to exceed the quota\.

Member accounts that are **Not enabled** do not contribute data to the behavior graph\.

Detective automatically enables accounts as the behavior graph can accommodate them\.

You can also try to enable member accounts manually that are **Not enabled** member accounts\. For example, you might remove existing member accounts to reduce the data volume\. Instead of waiting for the automatic process to enable accounts, you can try to enable **Not enabled** member accounts\.

## Enabling a member account that is Not enabled \(Console\)<a name="unblock-account-console"></a>

The member account list includes an option to enable selected member accounts that are **Not enabled\.**

**To enable a member account that is Not enabled**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

1. Under **My member accounts**, select the check box for each member account to enable\.

   You can only enable member accounts that have a status of **Not enabled**\.

1. Choose **Enable accounts**\.

Detective determines whether the member account can be enabled\. If the member account can be enabled, the status changes to **Enabled**\.

## Enabling a member account that is Not enabled \(Detective API, AWS CLI\)<a name="unblock-account-api"></a>

You can use an API call or the AWS Command Line Interface to enable a single member account that is **Not enabled**\. To get the ARN of your behavior graph to use in the request, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html) operation\.

**To enable a member account that is Not enabled**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_StartMonitoringMember.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_StartMonitoringMember.html) API operation\. You must provide the behavior graph ARN\. To identify the member account, use the AWS account identifier\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/start-monitoring-member.html](https://docs.aws.amazon.com/cli/latest/reference/detective/start-monitoring-member.html) command:

  ```
  start-monitoring-member --graph-arn <behavior graph ARN> --account-id <AWS account ID>
  ```

  For example:

  ```
  start-monitoring-member --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234 --account-id 444455556666
  ```