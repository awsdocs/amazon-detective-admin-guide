# AWS managed policies for Amazon Detective<a name="security-iam-awsmanpol"></a>

To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ViewOnlyAccess** AWS managed policy provides read\-only access to many AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.







## AWS managed policy: AmazonDetectiveFullAccess<a name="security-iam-awsmanpol-amazondetectivefullaccess"></a>

You can attach the `AmazonDetectiveFullAccess` policy to your IAM identities\.

This policy grants administrative permissions that allow a principal full access to all Detective actions\. This policy can be attached to a principal before they enable Detective for their account\. It must also be attached to the role that is used to run the Detective Python scripts to create and manage a behavior graph\.

Principals with these permissions can manage member accounts, add tags to their behavior graph, and use Detective for investigation\. They can archive GuardDuty findings\. The policy also provides permissions that the Detective console needs to display account names for accounts that are in AWS Organizations\.

**Permissions details**

This policy includes the following permissions\.
+ `detective` – Allows principals full access to all Detective actions\.
+ `organizations` – Allows principals to retrieve from AWS Organizations information about the accounts in an organization\. If an account belongs to an organization, then these permissions allow the Detective console to display account names in addition to account numbers\.
+ `guardduty` – Allows principals to archive GuardDuty findings from within Detective\.



```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "detective:*",
                "organizations:DescribeOrganization",
                "organizations:ListAccounts"
            ],
            "Resource": "*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "guardduty:ArchiveFindings"
            ],
            "Resource": "arn:aws:guardduty:*:*:detector/*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "guardduty:ListDetectors"
            ],
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: AmazonDetectiveServiceLinkedRolePolicy<a name="security-iam-awsmanpol-amazondetectiveservicelinkedrolepolicy"></a>

You can't attach `AmazonDetectiveServiceLinkedRolePolicy` to your IAM entities\. This policy is attached to a service\-linked role that allows Detective to perform actions on your behalf\. For more information, see [Using service\-linked roles for Detective](using-service-linked-roles.md)\.



This policy grants administrative permissions that allow the service\-linked role to retrieve account information for an organization\.

**Permissions details**

This policy includes the following permissions\.


+ `organizations` – Retrieves account information for an organization\.



```
{
  "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
              "organizations:ListAccounts"
            ],
            "Resource": "*"
        }
    ]
}
```

## Detective updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>

View details about updates to AWS managed policies for Detective since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the [Document history page](doc-history.md)\.








| Change | Description | Date | 
| --- | --- | --- | 
|  [AmazonDetectiveServiceLinkedRolePolicy](#security-iam-awsmanpol-amazondetectiveservicelinkedrolepolicy) – New policy  |  Detective added a new policy for its service\-linked role\. The policy allows the service\-linked role to retrieve information about the accounts in an organization\.  | December 9, 2021 | 
|  Detective started to track changes  |  Detective started to track changes for its AWS managed policies\.  | May 10, 2021 | 