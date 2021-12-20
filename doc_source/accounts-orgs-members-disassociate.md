# Disassociating organization accounts as member accounts<a name="accounts-orgs-members-disassociate"></a>

To stop ingesting data from an organization account in the organization behavior graph, you can disassociate the account\. Existing data for that account remains in the behavior graph\.

When you disassociate an organization account, the status changes to **Not a member**\. Detective stops ingesting data from that account, but the account remains in the list\.

## Disassociating organization accounts \(console\)<a name="accounts-orgs-members-disassociate-console"></a>

From the **Account management** page, you can disassociate organization accounts as member accounts\.To disassociate organization accounts as member accounts \(console\)

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

1. To display the list of enabled accounts, choose **Enabled**\.

1. Select the check box for each account to disassociate\.

1. Choose **Actions**\. Then choose **Disable accounts**\.

   The account status for the disassociated accounts changes to **Not a member**\.

## Disassociating organization accounts \(Detective API, AWS CLI\)<a name="accounts-orgs-members-disassociate-api"></a>

You can use the Detective API or the AWS Command Line Interface to disassociate organization accounts as member accounts in your behavior graph\.

To get the ARN of your behavior graph to use in the request, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html) operation\.

**To disassociate organization accounts from the organization behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_DeleteMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_DeleteMembers.html) operation\. Specify the graph ARN and the list of account identifiers for the member accounts to disassociate\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/delete-members.html](https://docs.aws.amazon.com/cli/latest/reference/detective/delete-members.html) command\.

  ```
  aws detective delete-members --account-ids <account ID list> --graph-arn <behavior graph ARN>
  ```

  **Example**

  ```
  aws detective delete-members --account-ids 444455556666 123456789012 --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234
  ```