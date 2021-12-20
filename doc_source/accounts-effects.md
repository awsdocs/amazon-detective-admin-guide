# Effect of account actions on behavior graphs<a name="accounts-effects"></a>

These actions have the following effects on Amazon Detective data and access\.

## Detective disabled<a name="accounts-effects-detective-disabled"></a>

When an administrator account disables Detective, the following occurs:
+ The behavior graph is removed\.
+ Detective stops ingesting data from the administrator account and the member accounts for that behavior graph\.

## Member account removed from the behavior graph<a name="accounts-effects-member-removed"></a>

When a member account is removed from a behavior graph, Detective stops ingesting data from that account\.

Existing data in the behavior graph is not affected\.

For invited accounts, the account is removed from the **My member accounts** list\.

For organization accounts in the organization behavior graph, the account status changes to **Not a member**\.

## Member account leaves the organization<a name="accounts-effects-member-leaves-org"></a>

When a member account leaves an organization, the following occurs:
+ The account is removed from the **My member accounts** list for the organization behavior graph\.
+ Detective stops ingesting data from that account\.

Existing data in the behavior graph is not affected\.

## AWS account suspended<a name="accounts-effects-account-suspended"></a>

When an administrator account is suspended in AWS, the account loses permission to view the behavior graph in Detective\. Detective stops ingesting data into the behavior graph\.

When a member account is suspended in AWS, Detective stops ingesting data for that account\.

After 90 days, the account is either terminated or reactivated\. When an administrator account is reactivated, its Detective permissions are restored\. Detective resumes the ingest of data from the account\. When a member account is reactivated, Detective resumes the ingest of data from the account\.

## AWS account closed<a name="accounts-effects-account-closed"></a>

When an AWS account is closed, Detective responds to the closure as follows\.
+ For an administrator account, Detective deletes the behavior graph\.
+ For a member account, Detective removes the account from the behavior graph\.

 AWS retains the policy data for the account for 90 days from the effective date of the administrator account closure\. At the end of the 90 day period, AWS permanently deletes all policy data for the account\. 
+  To retain findings for more than 90 days, you can archive the policies\. You can also use a custom action with an EventBridge rule to store the findings in an S3 bucket\. 
+  As long as AWS retains the policy data, when you reopen the closed account, AWS reassigns the account as the service administrator and recovers the service policy data for the account\. 
+  For more information, see [Closing an account](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/close-account.html)\. 

**Important**  
 For customers in the AWS GovCloud \(US\) Regions:   
 Before closing your account, back up and then delete your policy data and other account resources\. You will no longer have access to them after you close the account\. 