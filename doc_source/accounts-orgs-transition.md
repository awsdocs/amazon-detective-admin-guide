# Making the transition to use Organizations to manage behavior graph accounts<a name="accounts-orgs-transition"></a>

You might have an existing behavior graph with member accounts that accepted a manual invitation\. If you are enrolled in AWS Organizations, use the following steps to use Organizations to enable and manage member accounts instead of using the manual invitation process:

1. [Designate the Detective administrator account for your organization\.](#accounts-transition-designate-admin) This creates the organization behavior graph\.

   If the Detective administrator account already has a behavior graph, then that behavior graph becomes the organization behavior graph\.

1. [Enable organization accounts as member accounts in the organization behavior graph\.](#accounts-transition-members)

   If the organization behavior graph has existing member accounts that are organization accounts, those accounts are enabled automatically\.

The following diagram shows an overview of a behavior graph structure before the transition, the configuration in Organizations, and the behavior graph account structure after the transition\.

![\[This diagram shows the process of making the transition to use AWS Organizations to manage member accounts in the organization behavior graph.\]](http://docs.aws.amazon.com/detective/latest/adminguide/images/diagram_account_transition.png)

## Designate a Detective administrator account for your organization<a name="accounts-transition-designate-admin"></a>

Your organization management account designates the Detective administrator account from your organization\. See [Designating the Detective administrator account for an organization](accounts-designate-admin.md)\.

To make the transition simpler, Detective recommends that you choose a current administrator account as the Detective administrator account for the organization\.

If there is a delegated administrator account for Detective in Organizations, then you must use either that account or the organization management account as the Detective administrator account\.

Otherwise, the first time you designate a Detective administrator account that is not the organization management account, Detective calls Organizations to make that account the delegated administrator account for Detective\.

## Enable organization accounts as member accounts<a name="accounts-transition-members"></a>

The Detective administrator account is the administrator account for the organization behavior graph\. The Detective administrator account chooses the organization accounts to enable as member accounts in the organization behavior graph\. See [Managing organization accounts as member accounts](accounts-orgs-members.md)\.

On the **Accounts** page, the Detective administrator account sees all of the accounts in the organization\. 

If the Detective administrator account was already the administrator account for a behavior graph, then that behavior graph becomes the organization behavior graph\. Organization accounts that were already member accounts in that behavior graph are enabled as member accounts automatically\. Other organization accounts have a status of **Not a member**\.

Organization accounts have a type of **By organization**, even if they were previously member accounts by invitation\.

Member accounts that do not belong to the organization have a type of **By invitation**\.

The **Account management** page also provides an option, **Automatically enable new organization accounts**, to automatically enable new accounts as they are added to an organization\. See [Enabling new organization accounts as member accounts automatically](accounts-orgs-members-autoenable.md)\. The option is initially turned off\.

When the Detective administrator account first displays the **Account management** page, it displays a message that contains an **Enable all organization accounts** button\. When you choose **Enable all organization accounts**, Detective performs the following actions:
+ Enables all of the current organization accounts as member accounts\.
+ Turns on the option to automatically enable new organization accounts\.

There is also an **Enable all organization accounts** option on the member account list\.