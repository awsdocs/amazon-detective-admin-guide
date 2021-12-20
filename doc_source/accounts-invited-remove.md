# Removing invited member accounts from a behavior graph<a name="accounts-invited-remove"></a>

The administrator account can remove member accounts from a behavior graph at any time\.

Detective automatically removes member accounts that are terminated in AWS, except in the AWS GovCloud \(US\-East\) and AWS GovCloud \(US\-West\) Regions\.

When an invited member account is removed from a behavior graph, the following occurs\.
+ The member account is removed from **My member accounts**\.
+ Amazon Detective stops ingesting data from the removed account\.

Detective does not remove any existing data from the behavior graph, which aggregates data across member accounts\.

## Removing invited member accounts from a behavior graph \(console\)<a name="accounts-invited-remove-console"></a>

You can use the AWS Management Console to remove invited member accounts from your behavior graph\.

**To remove member accounts \(console\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

1. In the account list, select the check box for each member account to remove\.

   You cannot remove your own account from the list\.

1. Choose **Actions**\. Then choose **Disable accounts**\.

## Removing invited member accounts from a behavior graph \(Detective API, AWS CLI\)<a name="accounts-invited-remove-api"></a>

You can use the Detective API or the AWS Command Line Interface to remove invited member accounts from your behavior graph\. To get the ARN of your behavior graph to use in the request, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html) operation\.

**To remove invited member accounts from your behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_DeleteMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_DeleteMembers.html) operation\. Specify the graph ARN and the list of account identifiers for the member accounts to remove\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/delete-members.html](https://docs.aws.amazon.com/cli/latest/reference/detective/delete-members.html) command\.

  ```
  aws detective delete-members --account-ids <account ID list> --graph-arn <behavior graph ARN>
  ```

  Example:

  ```
  aws detective delete-members --account-ids 444455556666 123456789012 --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234
  ```

## Removing a list of invited member accounts across Regions \(Python script on GitHub\)<a name="accounts-invited-remove-script"></a>

Detective provides an open\-source script in GitHub\. You can use this script to remove a specified list of member accounts from an administrator account's behavior graphs across a specified list of Regions\.

For information on how to configure and use the GitHub scripts, see [Using the Amazon Detective Python scripts](detective-github-scripts.md)\.