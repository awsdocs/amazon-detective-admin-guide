# Amazon Detective Administration Guide

-----
*****Copyright &copy; Amazon Web Services, Inc. and/or its affiliates. All rights reserved.*****

-----
Amazon's trademarks and trade dress may not be used in 
     connection with any product or service that is not Amazon's, 
     in any manner that is likely to cause confusion among customers, 
     or in any manner that disparages or discredits Amazon. All other 
     trademarks not owned by Amazon are the property of their respective
     owners, who may or may not be affiliated with, connected to, or 
     sponsored by Amazon.

-----
## Contents
+ [What is Amazon Detective?](what-is-detective.md)
+ [Amazon Detective terms and concepts](detective-terms-concepts.md)
+ [Amazon Detective Regions and quotas](regions-limitations.md)
+ [Setting up Amazon Detective](detective-setup.md)
   + [Amazon Detective prerequisites and recommendations](detective-prerequisites.md)
   + [Enabling Amazon Detective](detective-enabling.md)
+ [About the free trial for behavior graphs](free-trial-overview.md)
+ [Source data used in a behavior graph](detective-source-data-about.md)
+ [Managing accounts](accounts.md)
   + [Account restrictions and recommendations in Detective](accounts-restrictions-recommendations.md)
   + [Making the transition to use Organizations to manage behavior graph accounts](accounts-orgs-transition.md)
   + [Allowed actions for accounts](accounts-allowed-actions.md)
   + [Designating the Detective administrator account for an organization](accounts-designate-admin.md)
   + [Viewing the list of accounts](accounts-view-list.md)
   + [Managing organization accounts as member accounts](accounts-orgs-members.md)
      + [Enabling new organization accounts as member accounts automatically](accounts-orgs-members-autoenable.md)
      + [Enabling organization accounts as member accounts](accounts-orgs-members-enable.md)
      + [Disassociating organization accounts as member accounts](accounts-orgs-members-disassociate.md)
   + [Managing invited member accounts](accounts-invited-members.md)
      + [Inviting member accounts to a behavior graph](accounts-invited-members-add.md)
      + [Enabling a member account that is Not enabled](graph-admin-unblock-account.md)
      + [Removing invited member accounts from a behavior graph](accounts-invited-remove.md)
   + [For member accounts: Managing behavior graph invitations and memberships](member-account-graph-management.md)
      + [Required IAM policy for a member account](member-account-iam-policy.md)
      + [Viewing your list of behavior graph invitations](member-view-graph-invitations.md)
      + [Responding to a behavior graph invitation](member-invitation-response.md)
      + [Removing your account from a behavior graph](member-remove-self-from-graph.md)
   + [Effect of account actions on behavior graphs](accounts-effects.md)
+ [Tracking actions and usage in Amazon Detective](tracking-usage-logging.md)
   + [Monitoring usage and cost for a behavior graph (administrator account)](usage-tracking-admin.md)
   + [Monitoring usage and cost across behavior graphs (member account)](member-usage-tracking.md)
   + [How Amazon Detective calculates projected cost](usage-projected-cost-calculation.md)
   + [Logging Amazon Detective API calls with AWS CloudTrail](logging-using-cloudtrail.md)
+ [Managing tags for a behavior graph](graph-tags.md)
+ [Security in Amazon Detective](security.md)
   + [Data protection in Amazon Detective](data-protection.md)
      + [Key management for Amazon Detective](key-management.md)
   + [Identity and access management for Amazon Detective](security-iam.md)
      + [How Amazon Detective works with IAM](security_iam_service-with-iam.md)
      + [Amazon Detective identity-based policy examples](security_iam_id-based-policy-examples.md)
      + [Troubleshooting Amazon Detective identity and access](security_iam_troubleshoot.md)
   + [Using service-linked roles for Detective](using-service-linked-roles.md)
   + [AWS managed policies for Amazon Detective](security-iam-awsmanpol.md)
   + [Logging and monitoring in Amazon Detective](detective-monitoring-logging.md)
   + [Compliance validation for Amazon Detective](detective-compliance.md)
   + [Resilience in Amazon Detective](disaster-recovery-resiliency.md)
   + [Infrastructure security in Amazon Detective](infrastructure-security.md)
   + [Security best practices for Amazon Detective](security-best-practices.md)
+ [Disabling Amazon Detective](detective-disabling.md)
+ [Using the Amazon Detective Python scripts](detective-github-scripts.md)
+ [Document history for Detective Administration Guide](doc-history.md)