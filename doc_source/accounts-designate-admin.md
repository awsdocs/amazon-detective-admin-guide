# Designating the Detective administrator account for an organization<a name="accounts-designate-admin"></a>

In the organization behavior graph, the Detective administrator account manages the behavior graph membership for all organization accounts\.

## How the Detective administrator account is managed<a name="accounts-designate-admin-overview"></a>

The organization management account designates the Detective administrator account for the organization in each Region\.

### Setting the Detective administrator account as the delegated administrator account<a name="accounts-detective-admin-delegated-admin"></a>

The Detective administrator account also becomes the delegated administrator account for Detective in Organizations\. The exception is if the organization management account designates itself as the Detective administrator account\. The organization management account cannot be a delegated administrator in Organizations\.

Once the delegated administrator account is set in Organizations, the organization management account can only choose either the delegated administrator account or their own account as the Detective administrator account\. We recommend that you choose the delegated administrator account in all Regions\.

### Creating and managing the organization behavior graph<a name="accounts-organization-behavior-graph"></a>

When the organization management account chooses a Detective administrator account, Detective creates a new behavior graph for that account\. That behavior graph is the organization behavior graph\.

If the Detective administrator account is an administrator account for an existing behavior graph, then that behavior graph becomes the organization behavior graph\.

The Detective administrator account chooses organization accounts to enable as member accounts in the organization behavior graph\.

![\[This diagram shows how the organization management account chooses the Detective administrator account. The Detective administrator account is the administrator account for the organization behavior graph and the delegated administrator account in Organizations. The Detective administrator account has access to all of the organization accounts.\]](http://docs.aws.amazon.com/detective/latest/adminguide/images/diagram_account_delegation.png)

The Detective administrator account can also send invitations to accounts that do not belong to the organization\. See [Managing organization accounts as member accounts](accounts-orgs-members.md) and [Managing invited member accounts](accounts-invited-members.md)\.

### Removing the Detective administrator account<a name="accounts-remove-admin-overview"></a>

The organization management account can remove the current Detective administrator account in a Region\. When you remove the Detective administrator account, Detective only removes it from the current Region\. It does not change the delegated administrator account in Organizations\.

When the organization management account removes the Detective administrator account in a Region, Detective deletes the organization behavior graph\. Detective is disabled for the removed Detective administrator account\.

To remove the current delegated administrator account for Detective, you use the Organizations API\. When you remove the delegated administrator account for Detective in Organizations, Detective deletes all of the organization behavior graphs where the delegated administrator account is the Detective administrator account\. Organization behavior graphs that have the organization management account as the Detective administrator account are not affected\.

## Required permissions to configure the Detective administrator account<a name="accounts-designate-admin-permissions"></a>

To ensure that the organization management account is able to configure the Detective administrator account, grant the following permissions to the IAM principal:
+ Attach the [`AmazonDetectiveFullAccess` managed policy](security-iam-awsmanpol.md#security-iam-awsmanpol-amazondetectivefullaccess)\.
+ Grant the following Organizations permissions:

  ```
  {
      "Effect": "Allow",
      "Action": "organizations:EnableAWSServiceAccess",
      "Resource": "*"
  },
  {
      "Effect": "Allow",
      "Action": [
          "organizations:RegisterDelegatedAdministrator".
          "organizations:DescribeAccount"
      ],
      "Resource": "arn:aws:organizations::*:account/o-*/*"
  }
  ```

  The Organizations [https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeregisterDelegatedAdministrator.html](https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeregisterDelegatedAdministrator.html) operation is used to remove the Detective administrator account from all Regions at the same time\. To be able to run [https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeregisterDelegatedAdministrator.html](https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeregisterDelegatedAdministrator.html), the IAM principal also must be granted` organizations:DeregisterDelegatedAdministrator`\.
+ Grant the following IAM permission on the ARN for the service\-linked role:

  ```
  {
      "Effect": "Allow",
      "Action": "iam:CreateServiceLinkedRole",
      "Resource": "<service-linked role ARN>",
  }
  ```

**To view an IAM policy that contains the required permissions for the organization management account**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the navigation pane, under **Settings**, choose **General**\.

1. Under **Required IAM policies**, choose **View organization management IAM policy**\.

## Designating a Detective administrator account \(console\)<a name="accounts-designate-admin-console"></a>

The organization management account can use the Detective console to designate the Detective administrator account\.

You do not need to enable Detective in order to manage the Detective administrator account\. You can manage the Detective administrator account from the **Enable Detective** page\.

**To designate a Detective administrator account \(**Enable Detective** page\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. Choose **Get started**\.

1. Under **Delegated administrator**, choose the Detective administrator account\.

   The available options depend on whether you have a delegated administrator account for Detective in Organizations\.
   + If you do not have a delegated administrator account for Detective in Organizations, then enter the account identifier of the account to designate it as the Detective administrator account\.

     You might have an existing administrator account and behavior graph from the manual invitation process\. If so, then Detective recommends that you designate that account as the Detective administrator account\.

     If you have a delegated administrator account in Organizations for Amazon GuardDuty, AWS Security Hub, or Amazon Macie, then Detective prompts you to select one of those accounts\. You can also enter a different account\.
   + If you do have a delegated administrator account for Detective in Organizations, then you are prompted to choose either that account or your account\. Detective recommends that you choose the delegated administrator account in all Regions\.

1. Choose **Delegate**\.

If you have Detective enabled, or are a member account in an existing behavior graph, then you can designate the Detective administrator account from the **General** page\.

**To designate a Detective administrator account \(**General** page\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, under **Settings**, choose **General**\.

1. Under **Delegated administrator**, choose **Edit**\.

1. Under **Delegated administrator**, choose the Detective administrator account\.

   The available options depend on whether you have a delegated administrator account for Detective in Organizations\.
   + If you do not have a delegated administrator account for Detective in Organizations, then enter the account identifier of the account to designate it as the Detective administrator account\.

     You might have an existing administrator account and behavior graph from the manual invitation process\. If so, then Detective recommends that you designate that account as the Detective administrator account\.

     If you have a delegated administrator account in Organizations for Amazon GuardDuty, AWS Security Hub, or Amazon Macie, then Detective prompts you to select one of those accounts\. You can also enter a different account\.
   + If you do have a delegated administrator account for Detective in Organizations, then you are prompted to choose either that account or your account\. We recommend that you choose the delegated administrator account in all Regions\.

1. Choose **Delegate**\.

## Designating a Detective administrator account \(Detective API, AWS CLI\)<a name="accounts-designate-admin-api"></a>

To designate the Detective administrator account, you can use an API call or the AWS Command Line Interface\. You must use the organization management account credentials\.

If you already have a delegated administrator account for Detective in organizations, then you must choose either that account or your account\. Detective recommends that you choose the delegated administrator account\.

**To designate the Detective administrator account \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_EnableOrganizationAdminAccount.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_EnableOrganizationAdminAccount.html) operation\. You must provide the AWS account identifier of the Detective administrator account\. To obtain the account identifier, use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListOrganizationAdminAccounts.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListOrganizationAdminAccounts.html) operation\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/enable-organization-admin-account.html](https://docs.aws.amazon.com/cli/latest/reference/detective/enable-organization-admin-account.html) command\.

  ```
  aws detective enable-organization-admin-account --account-id <admin account ID>
  ```

  **Example**

  ```
  aws detective enable-organization-admin-account --account-id 777788889999
  ```

## Removing a Detective administrator account \(console\)<a name="accounts-admin-remove-console"></a>

From the Detective console, you can remove the Detective administrator account\.

When you remove the Detective administrator account, Detective is disabled for the account, and the organization behavior graph is deleted\.

The Detective administrator account is only removed in the current Region\.

Removing a Detective administrator account does not affect the delegated administrator account in Organizations\.

**To remove the Detective administrator account \(**Enable Detective** page\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. Choose **Get started**\.

1. Under **Delegated Administrator**, choose **Remove account**\.

1. On the confirmation dialog, enter **disable**, then choose **Disable Amazon Detective**\.

**To remove a Detective administrator account \(**General** page\)**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, under **Settings**, choose **General**\.

1. Under **Delegated Administrator**, choose **Remove account**\.

1. On the confirmation dialog, enter **disable**, then choose **Disable Amazon Detective**\.

## Removing the Detective administrator account \(Detective API, AWS CLI\)<a name="accounts-remove-admin-det-api"></a>

To remove the Detective administrator account, you can use an API call or the AWS CLI\. You must use the organization management account credentials\.

When you remove the Detective administrator account, Detective is disabled for the account, and the organization behavior graph is deleted\.

When you use the Detective API to remove the Detective administrator account, it is only removed in the Region where the API call or command was issued\. Removing the Detective administrator account does not affect the delegated administrator account in Organizations\.

**To remove the Detective administrator account \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_DisableOrganizationAdminAccount.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_DisableOrganizationAdminAccount.html) operation\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/disable-organization-admin-account.html](https://docs.aws.amazon.com/cli/latest/reference/detective/disable-organization-admin-account.html) command\.

  ```
  aws detective disable-organization-admin-account
  ```

## Removing the delegated administrator account \(Organizations API, AWS CLI\)<a name="accounts-remove-admin-orgs-api"></a>

When you remove the Detective administrator account, it is only removed in that Region\. Removing the Detective administrator account does not affect the delegated administrator account in Organizations\.

The Organizations API allows you to remove the delegated administrator account for Detective\. This also deletes all organization behavior graphs where the delegated administrator account is the Detective administrator account, and disables Detective for the account in those Regions\.

**To remove the delegated administrator account \(Organizations API, AWS CLI\)**
+ **Organizations API:** Use the [https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeregisterDelegatedAdministrator.html](https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeregisterDelegatedAdministrator.html) operation\. You must provide the account identifier of the Detective administrator account, and the service principal for Detective, which is `detective.amazonaws.com`\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/organizations/deregister-delegated-administrator.html](https://docs.aws.amazon.com/cli/latest/reference/organizations/deregister-delegated-administrator.html) command\.

  ```
  aws organizations deregister-delegated-administrator --account-id <Detective administrator account ID> --service-principal <Detective service principal>
  ```

  **Example**

  ```
  aws organizations deregister-delegated-administrator --account-id 777788889999 --service-principal detective.amazonaws.com
  ```