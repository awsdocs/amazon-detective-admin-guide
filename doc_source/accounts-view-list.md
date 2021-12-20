# Viewing the list of accounts<a name="accounts-view-list"></a>

The administrator account can use the Detective console or API to view a list of accounts\. The list can include:
+ Accounts that the administrator account invited to join the behavior graph\. These accounts have a type of **By invitation**\.
+ For the organization behavior graph, all of the accounts in the organization\. These accounts have a type of **By organization**\.

The results do not include invited member accounts that declined an invitation or that the administrator account removed from the behavior graph\. It only includes accounts with the following statuses\.

**Verification in progress**  
For invited accounts, Detective is verifying the account email address before it sends the invitation\.  
For organization accounts, Detective is verifying that the account belongs to the organization\. Detective also verifies that it was the Detective administrator account that enabled the account\.

**Verification failed**  
The verification failed\. The invitation was not sent, or the organization account was not enabled as a member\.

**Invited**  
For invited accounts\. The invitation was sent, but the member account has not yet responded\.

**Not a member**  
For organization accounts in the organization behavior graph\. The organization account is not currently a member account\. It does not contribute data to the organization behavior graph\.

**Enabled**  
For invited accounts, the member account accepted the invitation and contributes data to the behavior graph\.  
For organization accounts in the organization behavior graph, the Detective administrator account enabled the account as a member account\. The account contributes data to the organization behavior graph\.

**Not enabled**  
For invited accounts, the member account accepted the invitation, but cannot be enabled\.  
For organization accounts in the organization behavior graph, the Detective administrator account tried to enable the account, but the account cannot be enabled\.  
This status occurs for one of the following reasons\.  
+ The member account has not been an Amazon GuardDuty customer for at least 48 hours\.
+ The member account data would cause the behavior graph data volume to exceed the Detective quota\.

## Listing accounts \(Console\)<a name="accounts-view-list-console"></a>

You can use the AWS Management Console to see and filter your list of accounts\.

**To display the list of accounts \(console\)**

1. Sign in to the AWS Management Console\. Then open the Detective console at [https://console\.aws\.amazon\.com/detective/](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

   The member account list contains the following accounts:
   + Your account
   + Accounts that you invited to contribute data to the behavior graph
   + In the organization behavior graph, all of the organization accounts

   For each account, the list displays the following information:
   + The AWS account identifier\.
   + For organization accounts, the account name\.
   + The account type \(**By invitation** or **By organization**\)\.
   + For invited accounts, the account root user email address\.
   + The account status\.
   + The daily data volume for the account\. Detective cannot retrieve the data volume for accounts that are not enabled as member accounts\.
   + The date when the account status was last updated\.

You can use the tabs at the top of the table to filter the list based on the member account status\. Each tab shows the number of matching member accounts\.
+ Choose **All** to view all of the member accounts\.
+ Choose **Enabled** to view accounts that have a status of **Enabled**\.
+ Choose **Not enabled** to view accounts that have a status other than **Enabled**\.

You also can add other filters to the member account list\.

**To add a filter to the list of accounts in the behavior graph \(console\)**

1. Choose the filter box\.

1. Choose the column that you want to use to filter the list\.

1. For the specified column, choose the value to use for the filter\.

1. To remove a filter, choose the **x** icon at the top right\.

1. To update the list with the most recent status information, choose the refresh icon at the top right\.

## Listing your member accounts \(Detective API, AWS CLI\)<a name="accounts-view-list-api"></a>

You can use an API call or the AWS Command Line Interface to view a list of member accounts in your behavior graph\.

To get the ARN of your behavior graph to use in the request, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html) operation\.

**To retrieve a list of member accounts \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListMembers.html) operation\. To identify the intended behavior graph, specify the behavior graph ARN\.

  Note that for the organization behavior graph, [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListMembers.html) does not return organization accounts that you did not enable as member accounts or that you disassociated from the behavior graph\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/list-members.html](https://docs.aws.amazon.com/cli/latest/reference/detective/list-members.html) command\.

  ```
  aws detective list-members --graph-arn <behavior graph ARN>
  ```

  Example:

  ```
  aws detective list-members --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234
  ```

**To retrieve details about specific member accounts in your behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_GetMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_GetMembers.html) operation\. Specify the behavior graph ARN and the list of account identifiers for the member accounts\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/get-members.html](https://docs.aws.amazon.com/cli/latest/reference/detective/get-members.html) command\.

  ```
  aws detective get-members --account-ids <member account IDs> --graph-arn <behavior graph ARN>
  ```

  Example:

  ```
  aws detective get-members --account-ids 444455556666 123456789012 --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234
  ```