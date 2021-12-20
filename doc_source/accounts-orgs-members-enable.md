# Enabling organization accounts as member accounts<a name="accounts-orgs-members-enable"></a>

If you do not automatically enable new organization accounts, then you can enable those accounts manually\. You must also manually enable accounts that you disassociated\.

## Determining whether an account can be enabled<a name="accounts-orgs-members-enable-eligibility"></a>

You cannot enable an organization account as a member account if the organization behavior graph already has the maximum 1,200 enabled accounts\. In this case, the organization account status remains **Not a member**\.

When you enable an organization account, Detective checks whether the account has been an Amazon GuardDuty customer for at least 48 hours\. If it has, then Detective checks whether the account data would cause the data rate for the behavior graph to exceed the quota\. This check can take 24 to 48 hours\.

While Detective verifies the data rate, the member account status is **Not enabled**\.

If the member account passes both of those checks, then the member account status is updated to **Enabled**\. Detective begins to ingest data from the member account into the behavior graph\.

If the account fails either of those checks, then the member account status remains **Not enabled**\. The account does not contribute data to the behavior graph\.

As soon as the member account can be enabled, Detective automatically changes the member account status to **Enabled**\.

## Enabling organization accounts as member accounts \(console\)<a name="accounts-orgs-members-enable-console"></a>

From the **Account management** page, you can enable organization accounts as member accounts\.

**To enable organization accounts as member accounts**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

1. To view the list of accounts that are not currently enabled, choose **Not enabled**\.

1. You can either select specific organization accounts, or enable all organization accounts\.

   To enable selected organization accounts:

   1. Select each organization account that you want to enable\.

   1. Choose **Enable accounts**\.

   To enable all organization accounts, choose **Enable all organization accounts**\.

## Enabling organization accounts as member accounts \(Detective API, AWS CLI\)<a name="accounts-orgs-members-enable-api"></a>

You can use the Detective API or the AWS Command Line Interface to enable organization accounts as member accounts in the organization behavior graph\. To get the ARN of your behavior graph to use in the request, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html) operation\.

**To enable organization accounts as member accounts \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateMembers.html) operation\. You must provide the graph ARN\.

  For each account, specify the account identifier\. Organization accounts in the organization behavior graph do not receive an invitation\. You do not need to provide an email address or other invitation information\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/create-members.html](https://docs.aws.amazon.com/cli/latest/reference/detective/create-members.html) command\.

  ```
  aws detective create-members --accounts AccountId=<AWS account ID> --graph-arn <behavior graph ARN>
  ```

  **Example**

  ```
  aws detective create-members --accounts AccountId=444455556666 AccountId=123456789012 --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234
  ```