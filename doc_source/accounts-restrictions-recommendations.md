# Account restrictions and recommendations in Detective<a name="accounts-restrictions-recommendations"></a>

When managing accounts in Amazon Detective, be aware of the following restrictions and recommendations\.

## Maximum number of member accounts<a name="accounts-maximum-members"></a>

Detective allows up to 1,200 member accounts in each behavior graph\.

## Accounts and Regions<a name="accounts-regions"></a>

If you use AWS Organizations to manage accounts, the organization management account designates a Detective administrator account for the organization\. The Detective administrator account becomes the administrator account for the organization behavior graph\. 

The Detective administrator account must be the same in all Regions\. The organization management account designates the Detective administrator account separately in each Region\. The Detective administrator account also manages the organization behavior graphs and member accounts separately in each Region\.

For member accounts created by invitation, the administrator\-member association is created only in the Region that the invitation is sent from\. The administrator account must enable Detective in each Region, and has a separate behavior graph in each Region\. The administrator account then invites each account to associate as a member account in that Region\.

An account can be a member account of multiple behavior graphs in the same Region\. An account can only be the administrator account of one behavior graph per Region\. An account can be an administrator account in different Regions\.

## Alignment of administrator accounts with Security Hub and GuardDuty<a name="accounts-alignment"></a>

To ensure that the integrations with AWS Security Hub and Amazon GuardDuty work smoothly, we recommend that the same account is the administrator account in all of these services\.

See [Recommended alignment with GuardDuty and AWS Security Hub](detective-prerequisites.md#recommended-service-alignment)\.

## Granting the required permissions for administrator accounts<a name="accounts-admin-permissions"></a>

To ensure that an administrator account has the required permissions to manage its behavior graph, attach the [`AmazonDetectiveFullAccess` managed policy](security-iam-awsmanpol.md#security-iam-awsmanpol-amazondetectivefullaccess) to the IAM principal\.

## Reflecting organization updates in Detective<a name="accounts-orgs-update-notification"></a>

Changes to an organization are not immediately reflected in Detective\.

For most changes, such as new and removed organization accounts, it can take up to an hour for Detective to be notified\.

A change to the designated Detective administrator account in Organizations takes less time to propagate\.