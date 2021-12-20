# Required IAM policy for a member account<a name="member-account-iam-policy"></a>

Before a member account can view and manage invitations, the required IAM policy must be attached to their principal\. The principal can be an existing user or role, or you can create a new user or role to use for Detective\.

Ideally, the administrator account has their IAM administrator attach the required policy\.

The member account IAM policy grants access to member account actions in Amazon Detective\. The email invitation to contribute to a behavior graph includes the text of that IAM policy\.

To use this policy, replace `<behavior graph ARN>` with the graph ARN\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "detective:AcceptInvitation",
        "detective:DisassociateMembership",
        "detective:RejectInvitation"
      ],
      "Resource": "<behavior graph ARN>"
    },
   {
    "Effect":"Allow",
    "Action":[
        "detective:GetFreeTrialEligibility",
        "detective:GetPricingInformation",
        "detective:GetUsageInformation",
        "detective:ListInvitations"
    ],
    "Resource":"*"
   }
 ]
}
```

Note that organization accounts in the organization behavior graph do not receive invitations and cannot disassociate their account from the organization behavior graph\. If they do not belong to other behavior graphs, then they only require the `ListInvitations` permission\. `ListInvitations` allows them to see the administrator account for the behavior graph\. The permissions to manage invitations and disassociate memberships only apply to memberships by invitation\.