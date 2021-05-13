# Inviting member accounts to a behavior graph<a name="graph-admin-add-member-accounts"></a>

The administrator account can invite up to 1,200 member accounts to contribute to a behavior graph\.

At a high level, the process for inviting members to contribute to a behavior graph is as follows\.

1. For each member account to add, the administrator account provides the AWS account identifier and the root user email address\.

1. Detective validates that the email address is the root user email address for the account\.

   Detective does not perform this validation in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-West\) Regions\.

1. If the account information is valid, Detective sends the invitation to the member account\.

   Detective never sends email invitations to member accounts in the AWS GovCloud \(US\-East\) or AWS GovCloud \(US\-West\) Regions\.

   For other Regions, the Detective API includes an option to not send invitations to the member accounts\.

   This option is useful for accounts that are managed centrally\.

1. The member account accepts or declines the invitation\.

   Note that even if the administrator account does not send invitation emails, the member account must still respond to the invitation\. 

1. If the member account accepts the invitation, then Detective checks whether the member account has been an Amazon GuardDuty customer for at least 48 hours\.

   If it has, then Detective checks whether the member account data would cause the data rate for the behavior graph to exceed the quota\.

   This check can take between 24 to 48 hours\.

   While Detective verifies the data rate, the member account status is **Accepted \(Not enabled\)**\.

1. If the member account passes both of those checks, then the member account status is updated automatically to **Accepted \(Enabled\)**\. Detective begins to ingest data from the member account into the behavior graph\.

   If it fails either of those checks, then the member account status remains **Accepted \(Not enabled\)**\. The member account does not contribute data to the behavior graph\.

1. As soon as the member account is eligible to be enabled, Detective automatically changes the member account status to **Accepted \(Enabled\)**\.

   For example, a member account enables GuardDuty, and Detective verifies that their data volume is not too large\. Or the administrator account removes other member accounts to make space for an account\.

   If more than one account is **Accepted \(Not enabled\)**, then Detective enables the accounts in the order in which they were invited\. The process to check whether to enable any **Accepted \(Not enabled\)** accounts runs every hour\.

   The administrator account can also enable accounts manually, instead of waiting for the automatic process\. For example, the administrator account might want to select the accounts to enable\. See [Enabling a member account that is Accepted \(Not enabled\)](graph-admin-unblock-account.md)\.

   Note that Detective began to automatically enable accounts that are **Accepted \(Not enabled\)** on May 12, 2021\. Accounts that were **Accepted \(Not enabled\)** before then are not enabled automatically\. The administrator account must enable them manually\.

## Inviting individual accounts to a behavior graph \(Console\)<a name="graph-admin-select-accounts-individual"></a>

You can manually specify which member accounts to invite to contribute their data to a behavior graph\.

**To manually select the member accounts to invite \(console\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

1. Choose **Actions**\. Then choose **Invite accounts**\.

1. Under **Add accounts**, choose **Add individual accounts**\.

1. To add a member account to the invitation list, perform the following steps\.

   1. Choose **Add account**\.

   1. For **AWS Account ID**, enter the AWS account ID\.

   1. For **Email address**, enter the root user email address for the account\.

1. To remove an account from the list, choose **Remove** for that account\.

1. Under **Personalize invitation email**, add customized content to include in the invitation email\.

   For example, you can use this area to provide contact information\. Or use it to remind the member account that they need to attach the required IAM policy to their user or role before they can accept the invitation\.

1. **Member account IAM policy** contains the text of the required IAM policy for member accounts\. The email invitation includes this policy text\. To copy the policy text, choose **Copy**\.

1. Choose **Invite**\.

## Inviting a list of member accounts to a behavior graph \(Console\)<a name="graph-admin-select-accounts-csv"></a>

From the Detective console, you can provide a `.csv` file containing a list of member accounts to invite to your behavior graph\.

The first line in the file is the header row\. Each account is then listed on a separate line\. Each member account entry contains the AWS account ID and the account's root user email address\.

Example:

```
Account ID,Email address
111122223333,srodriguez@example.com
444455556666,rroe@example.com
```

When Detective processes the file, it ignores accounts that were already invited, unless the account status is **Verification failed**\. That status indicates that the email address provided for the account did not match the account's root user email address\. In that case, Detective deletes the original invitation and tries again to verify the email address and send the invitation\.

This option also provides a template that you can use to create the list of accounts\.

**To invite member accounts from a \.csv list \(console\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

1. Choose **Actions**\. Then choose **Invite accounts**\.

1. Under **Add accounts**, choose **Add from \.csv**\.

1. To download a template file to work from, choose **Download \.csv template**\.

1. To select the file containing the list of accounts, choose **Choose \.csv file**\.

1. Under **Review member accounts**, verify the list of member accounts that Detective found in the file\.

1. Under **Personalize invitation email**, add customized content to include in the invitation email\.

   For example, you can provide contact information, or remind the member account about the required IAM policy\.

1. **Member account IAM policy** contains the text of the required IAM policy for member accounts\. The email invitation includes this policy text\. To copy the policy text, choose **Copy**\.

1. Choose **Invite**\.

## Inviting member accounts to a behavior graph \(Detective API, AWS CLI\)<a name="graph-admin-add-account-api"></a>

You can use the Detective API or the AWS Command Line Interface to invite member accounts to contribute their data to a behavior graph\. To get the ARN of your behavior graph to use in the request, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListGraphs.html) operation\.

**To invite member accounts to a behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateMembers.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateMembers.html) operation\. You must provide the graph ARN\. For each account, specify the account identifier and the root user email address\.

  To not send invitation emails to the member accounts, set `DisableEmailNotification` to true\. By default, `DisableEmailNotification` is false \.

  If you do send invitation emails, you can optionally provide custom text to add to the invitation email\.
+ **AWS CLI:** At the command line, run the `create-members` command\.

  ```
  aws detective create-members --accounts AccountId=<AWS account ID>,EmailAddress=<root user email address> --graph-arn <behavior graph ARN> --message "<Custom message text>"
  ```

  **Example**

  ```
  aws detective create-members --accounts AccountId=444455556666,EmailAddress=mmajor@example.com AccountId=123456789012,EmailAddress=jstiles@example.com --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234 --message "This is Paul Santos. I need to add your account to the data we use for security investigation in Amazon Detective. If you have any questions, contact me at psantos@example.com."
  ```

  To indicate to not send invitation emails to the member accounts, include `--disable-email-notification`\.

  ```
  aws detective create-members --accounts AccountId=<AWS account ID>,EmailAddress=<root user email address> --graph-arn <behavior graph ARN> --disable-email-notification
  ```

  **Example**

  ```
  aws detective create-members --accounts AccountId=444455556666,EmailAddress=mmajor@example.com AccountId=123456789012,EmailAddress=jstiles@example.com --graph-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234 --disable-email-notification
  ```

## Adding a list of member accounts across Regions \(Python script on GitHub\)<a name="graph-admin-add-accounts-github-scripts"></a>

Detective provides an open\-source script in GitHub that allows you to do the following:
+ Add a specified list of member accounts to an administrator account's behavior graphs across a specified list of Regions\.
+ If the administrator account does not have a behavior graph in a Region, then the script also enables Detective and creates the behavior graph in that Region\.
+ Sends invitation emails to the member accounts\.
+ Automatically accept the invitations for the member accounts\.

For information on how to configure and use the GitHub scripts, see [Using the Amazon Detective Python scripts](detective-github-scripts.md)\.