# Enabling Amazon Detective<a name="detective-enabling"></a>

You can enable Detective from the Detective console, the Detective API, or the AWS Command Line Interface\.

You can only enable Detective once in each Region\. If you already are the administrator account for a behavior graph in the Region, then you cannot enable Detective again in that Region\.

Before you try to enable Detective, make sure that your account has been enrolled in Amazon GuardDuty for at least 48 hours\. If you do not meet this requirement, you cannot enable Detective\.

If you do meet the GuardDuty requirement, then when you make the request to enable Detective, Detective checks whether your data volume is within the Detective quota\. If your data volume exceeds the quota, then you cannot enable Detective\.

**Topics**
+ [Enabling Detective \(Console\)](#enable-from-console)
+ [Enabling Detective \(Detective API, AWS CLI\)](#enable-from-api)
+ [Enabling Detective across Regions \(Python script on GitHub\)](#enable-from-github-scripts)
+ [Checking that data is being extracted](#enable-check-data)

## Enabling Detective \(Console\)<a name="enable-from-console"></a>

You can enable Amazon Detective from the AWS Management Console\.

**To enable Detective \(console\)**

1. Sign in to the AWS Management Console\. Then open the Detective console at [https://console\.aws\.amazon\.com/detective/](https://console.aws.amazon.com/detective/)\.

1. Choose **Get started**\.

1. On the **Enable Amazon Detective** page, **Align administrator accounts \(recommended\)** explains the recommendation to align the administrator accounts between Detective and Amazon GuardDuty and AWS Security Hub\. See [Recommended alignment with GuardDuty and AWS Security Hub](detective-prerequisites.md#recommended-service-alignment)\.

1. **Attach IAM policy \(required\)** contains the IAM policy that is required to enable Detective and manage a behavior graph\. The policy should already be attached to your principal\.

   If it is not yet attached, choose **Copy IAM policy** to copy the policy so that you can attach it\.

   Confirm that the required IAM policy is in place\.

1. The **Add tags** section allows you to add tags to the behavior graph\.

   To add a tag, do the following:

   1. Choose **Add new tag**\.

   1. For **Key**, enter the name of the tag\.

   1. For **Value**, enter the value of the tag\.

   To remove a tag, choose the **Remove** option for that tag\.

1. Choose **Enable Amazon Detective**\.

1. After you enable Detective, you can invite member accounts to your behavior graph\.

   To navigate to the **Account management** page, choose **Add members now**\. For information on inviting member accounts, see [Inviting member accounts to a behavior graph](graph-admin-add-member-accounts.md)\.

## Enabling Detective \(Detective API, AWS CLI\)<a name="enable-from-api"></a>

You can enable Amazon Detective from the Detective API or the AWS Command Line Interface\.

**To enable Detective \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateGraph.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_CreateGraph.html) operation\.
+ **AWS CLI:** At the command line, run the `create-graph` command\.

  ```
  aws detective create-graph --tags '{"tagName": "tagValue"}'
  ```

  The following command enables Detective and sets the value of the `Department` tag to `Security`\.

  ```
  aws detective create-graph --tags '{"Department": "Security"}'
  ```

## Enabling Detective across Regions \(Python script on GitHub\)<a name="enable-from-github-scripts"></a>

Detective provides an open\-source script in GitHub that does the following:
+ Enables Detective for an administrator account in a specified list of Regions
+ Adds a provided list of member accounts to each of the resulting behavior graphs
+ Sends invitation emails to the member accounts
+ Automatically accepts the invitations for the member accounts

For information on how to configure and use the GitHub scripts, see [Using the Amazon Detective Python scripts](detective-github-scripts.md)\.

## Checking that data is being extracted<a name="enable-check-data"></a>

After you enable Detective, it begins to ingest and extract data from your AWS account into your behavior graph\.

For the initial extraction, data usually becomes available in the behavior graph within 24 hours\.

One way to check that Detective is extracting data is to look for example values on the Detective **Search** page\.

**To check for example values on the Search page**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the navigation pane, choose **Search**\.

1. From the **Select type** menu, choose a type of item\.

   **Examples from your data** contains a sample set of identifiers of the selected type that are in your behavior graph data\.

   If you can see example values, then you know that data is being ingested and extracted into your behavior graph\.