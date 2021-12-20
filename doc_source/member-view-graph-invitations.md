# Viewing your list of behavior graph invitations<a name="member-view-graph-invitations"></a>

From the Amazon Detective console, Detective API, or AWS Command Line Interface, a member account can see their behavior graph invitations\.

## Viewing behavior graph invitations \(console\)<a name="member-view-invitations-console"></a>

You can view behavior graph invitations from the AWS Management Console\.

**To view behavior graph invitations \(console\)**

1. Sign in to the AWS Management Console\. Then open the Detective console at [https://console\.aws\.amazon\.com/detective/](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, choose **Account management**\.

On the **Account management** page, **My administrator accounts** contains your open and accepted behavior graph invitations in the current Region\. For an organization account, **My administrator accounts** also contains the organization behavior graph\.

If your account is currently in the free trial period, the page also displays the number of days remaining in your free trial\.

The list does not contain invitations that you declined, memberships that you resigned, or memberships that the administrator account removed\.

Each invitation shows the administrator account number, the date that the invitation was accepted, and the current status of the invitation\.
+ For invitations that you have not responded to, the status is **Invited**\.
+ For invitations that you accepted, the status is either **Enabled** or **Not enabled**\.

  If the status is **Enabled**, then your account contributes data to the behavior graph\.

  If the status is **Not enabled**, then your account does not contribute data to the behavior graph\.

  Your account status is set initially to **Not enabled** while Detective checks whether you have GuardDuty enabled, and if so, whether your account would cause the data volume for the behavior graph to exceed the Detective quota\.

  If your account would not cause the behavior graph to exceed the quota, Detective updates your account status to **Enabled**\. Otherwise, the status remains **Not enabled**\.

  When the behavior graph is able to accommodate the data volume for your account, Detective automatically updates it to **Enabled**\. For example, the administrator account might remove other member accounts so that your account can be enabled\. The administrator account can also enable your account manually\.

## Viewing behavior graph invitations \(Detective API, AWS CLI\)<a name="member-view-invitations-api"></a>

You can list behavior graph invitations from the Detective API or the AWS Command Line Interface\.

**To retrieve a list of open and accepted invitations to behavior graphs \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListInvitations.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListInvitations.html) operation\.
+ **AWS CLI:** At the command line, run the [https://docs.aws.amazon.com/cli/latest/reference/detective/list-invitations.html](https://docs.aws.amazon.com/cli/latest/reference/detective/list-invitations.html) command\.

  ```
  aws detective list-invitations
  ```