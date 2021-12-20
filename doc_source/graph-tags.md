# Managing tags for a behavior graph<a name="graph-tags"></a>

You can assign tags to your behavior graph\. You can then use the tag values in IAM policies to manage access to behavior graph functions in Detective\. See [Authorization based on Detective behavior graph tags](security_iam_service-with-iam.md#security_iam_service-with-iam-tags)\.

You also can use tags as a tool for cost reporting\. For example, to track costs associated with security, you could assign the same tag to your Detective behavior graph, AWS Security Hub hub resource, and Amazon GuardDuty detectors\. In AWS Cost Explorer, you could then search for that tag to see a consolidated view of the costs across those resources\.

## Viewing the tags for a behavior graph \(Console\)<a name="graph-tags-list-console"></a>

You manage the tags for your behavior graph from the **General** page\.

**To view the list of tags assigned to the behavior graph**

1. Open the [Detective console](https://console.aws.amazon.com/detective/)\.

1. In the navigation pane, under **Settings**, choose **General**\.

## Listing the tags for a behavior graph \(Detective API, AWS CLI\)<a name="graph-tags-list-api"></a>

You can use the Detective API or the AWS Command Line Interface to get the list of tags for your behavior graph\.

**To get the list of tags for a behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_ListTagsForResource.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_ListTagsForResource.html) operation\. You must provide the ARN of your behavior graph\.
+ **AWS CLI:** At the command line, run the `list-tags-for-resource` command\.

  ```
  aws detective list-tags-for-resource --resource-arn <behavior graph ARN>
  ```

  **Example**

  ```
  aws detective list-tags-for-resource --resource-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234
  ```

## Adding tags to a behavior graph \(Console\)<a name="graph-tags-add-console"></a>

From the tag list on the **General** page, you can add tag values to the behavior graph\.

**To add a tag to your behavior graph**

1. Choose **Add new tag**\.

1. For **Key**, enter the name of the tag\.

1. For **Value**, enter the value of the tag\.

## Adding tags to a behavior graph \(Detective API, AWS CLI\)<a name="graph-tags-add-api"></a>

You can use the Detective API or the AWS CLI to add tag values to your behavior graph\.

**To add tags to a behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_TagResource.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_TagResource.html) operation\. You provide the behavior graph ARN and the tag values to add\.
+ **AWS CLI**: At the command line, run the `tag-resource` command\.

  ```
  aws-detective tag-resource --aws detective tag-resource --resource-arn <behavior graph ARN> --tags '{"TagName":"TagValue"}'
  ```

  **Example**

  ```
  aws detective tag-resource --resource-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234 --tags '{"Department":"Finance"}'
  ```

## Removing tags from a behavior graph \(Console\)<a name="graph-tags-remove-console"></a>

To remove a tag from the list on the **General** page, choose the **Remove** option for that tag\.

## Removing tags from a behavior graph \(Detective API, AWS CLI\)<a name="graph-tags-remove-api"></a>

You can use the Detective API or the AWS CLI to remove tag values from your behavior graph\.

**To remove tags from a behavior graph \(Detective API, AWS CLI\)**
+ **Detective API:** Use the [https://docs.aws.amazon.com/detective/latest/APIReference/API_UntagResource.html](https://docs.aws.amazon.com/detective/latest/APIReference/API_UntagResource.html) operation\. You provide the behavior graph ARN, and the names of the tags to remove\.
+ **AWS CLI**: At the command line, run the `untag-resource` command\.

  ```
  aws detective untag-resource --resource-arn <behavior graph ARN> --tag-keys "TagName"
  ```

  **Example**

  ```
  aws detective untag-resource --resource-arn arn:aws:detective:us-east-1:111122223333:graph:123412341234 --tag-keys "Department"
  ```