# Managing accounts<a name="accounts"></a>

Each behavior graph contains data from one or more accounts\. When an account enables Detective, it becomes the administrator account for the behavior graph, and it chooses the member accounts for the behavior graph\. A behavior graph can have up to 1,200 member accounts\.

If you are integrated with AWS Organizations, then the organization management account designates the Detective administrator account for the organization\. That Detective administrator account then becomes the administrator account for the organization behavior graph\. The Detective administrator account can enable any organization account as a member account in the organization behavior graph\. Organization accounts cannot remove themselves from the organization behavior graph\.

An administrator account also can invite accounts to join a behavior graph\. When the account accepts the invitation, Detective enables the account as a member account\. Member accounts that are added by invitation can remove themselves from the behavior graph\.

When an account is enabled as a member account, Detective begins to ingest and extract the member account's data into that behavior graph\.

Detective charges each account for the data that it contributes to each behavior graph\. For information on tracking the volume of data for each account in a behavior graph, see [Monitoring usage and cost for a behavior graph \(administrator account\)](usage-tracking-admin.md)\.

**Topics**
+ [Account restrictions and recommendations in Detective](accounts-restrictions-recommendations.md)
+ [Making the transition to use Organizations to manage behavior graph accounts](accounts-orgs-transition.md)
+ [Allowed actions for accounts](accounts-allowed-actions.md)
+ [Designating the Detective administrator account for an organization](accounts-designate-admin.md)
+ [Viewing the list of accounts](accounts-view-list.md)
+ [Managing organization accounts as member accounts](accounts-orgs-members.md)
+ [Managing invited member accounts](accounts-invited-members.md)
+ [For member accounts: Managing behavior graph invitations and memberships](member-account-graph-management.md)
+ [Effect of account actions on behavior graphs](accounts-effects.md)