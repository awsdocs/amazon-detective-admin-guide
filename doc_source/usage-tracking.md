# Monitoring Amazon Detective usage and cost<a name="usage-tracking"></a>

Amazon Detective bills each account for the data used in each behavior graph that they belong to\. Detective charges a tiered flat rate per GB for all data regardless of the source\.

For master accounts, the **Usage** page of the Detective console shows the volume of data ingested into their behavior graph over the previous 30 days\. Master accounts can also see a projected cost for a typical 30\-day period\.

During the free trial, the **Usage** page displays a notification that includes the number of days remaining\.

**To view Detective usage information**

1. Sign in to the AWS Management Console, then open the Detective console at [https://console\.aws\.amazon\.com/detective/](https://console.aws.amazon.com/detective/)\.

1. In the Detective navigation pane, under **Settings**, choose **Usage**\.

## Volume of data ingested<a name="usage-data-volume"></a>

**Ingested volume by account** lists the active accounts in the behavior graph\. It does not list member accounts that were removed\.

For each account, the ingested volume list provides the following information\.
+ The AWS account identifier and root user email address\.
+ The date when the account began to contribute data to the behavior graph\.

  For the master account, this is the date when they enabled Detective\.

  For member accounts, this is the date when they accepted the behavior graph invitation\.
+ The volume of ingested data from the account over the previous 30 days\. The total includes all source types\.

## Projected 30\-day cost<a name="usage-projected-cost"></a>

**Projected 30\-day cost** shows a projected cost for 30 days of data across the current accounts\. The projected cost is based on the daily average volume for each account\.

**Important**  
This amount is a projected cost only\. It projects the total cost of the behavior graph data for a typical 30\-day time period\. It is based on the usage from the previous 30 days\. The projected cost does not include member accounts that were removed from the behavior graph\.

To calculate the projected cost, Detective does the following\.

1. For each account, Detective calculates the average volume per day\. It adds the data volume across all of the active days and then divides by the number of days that the account has been active\.

   If the account joined the behavior graph more than 30 days ago, then the number of days is 30\. If the account joined the graph fewer than 30 days ago, then it is the number of days since the account joined\.

   For example, if an account accepted the invitation 12 days ago, then Detective adds the volume ingested for those 12 days and then divides it by 12\.

1. For each account, Detective multiplies its daily average by 30\. This is the projected 30\-day usage for that account\.

1. For each account, Detective uses its pricing model to calculate the projected 30\-day cost for the projected 30\-day usage\.

1. Detective combines the projected 30\-day cost from all of the accounts\.