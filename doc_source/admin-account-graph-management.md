# For administrator accounts: Managing the accounts in your behavior graph<a name="admin-account-graph-management"></a>

An administrator account can invite 1,200 other accounts to be member accounts in the behavior graph\. See [Inviting member accounts to a behavior graph](graph-admin-add-member-accounts.md)\. When a member account accepts the invitation and is enabled, Amazon Detective begins to ingest and extract the member account's data into that behavior graph\.

The administrator account can also remove member accounts from their behavior graph\. See [Removing member accounts from a behavior graph](graph-admin-remove-member-accounts.md)\.

An account can be a member account of multiple behavior graphs in the same Region\. An account can only be the administrator account of one behavior graph per Region\. An account can be an administrator account in different Regions\.

Detective charges each account for the data that it contributes to each behavior graph\. For information on tracking the volume of data for each account in the behavior graph, see [Monitoring usage and cost for a behavior graph \(administrator account\)](usage-tracking-admin.md)\.

**Topics**
+ [Viewing the list of accounts in a behavior graph](graph-admin-view-accounts.md)
+ [Inviting member accounts to a behavior graph](graph-admin-add-member-accounts.md)
+ [Enabling a member account that is Accepted \(Not enabled\)](graph-admin-unblock-account.md)
+ [Removing member accounts from a behavior graph](graph-admin-remove-member-accounts.md)