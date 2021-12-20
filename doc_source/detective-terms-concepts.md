# Amazon Detective terms and concepts<a name="detective-terms-concepts"></a>

The following terms and concepts are important for understanding Amazon Detective and how it works:

****Administrator account****  
The AWS account that owns a behavior graph and that uses the behavior graph for investigation\.  
The administrator account invites member accounts to contribute their data to the behavior graph\. see [Inviting member accounts to a behavior graph](accounts-invited-members-add.md)\.  
For the organization behavior graph, the administrator account is the Detective administrator account that the organization management account designates\. See [Designating the Detective administrator account for an organization](accounts-designate-admin.md)\. The Detective administrator account can enable any organization account as a member account in the organization behavior graph\. See [Managing organization accounts as member accounts](accounts-orgs-members.md)\.  
Administrator accounts can also view data usage for the behavior graph, and remove member accounts from the behavior graph\.

****Behavior graph****  
A linked set of data generated from incoming source data that is associated with one or more AWS accounts\.  
Each behavior graph uses the same structure of findings, entities, and relationships\.

**Delegated administrator account \(AWS Organizations\)**  
In Organizations, the delegated administrator account for a service is able to manage the use of a service for the organization\.  
In Detective, the Detective administrator account is also the delegated administrator account, unless the Detective administrator account is the organization management account\. The organization management account cannot be a delegated administrator account\.

**Detective administrator account**  
The account designated by the organization management account to be the administrator account for the organization behavior graph in a Region\. See [Designating the Detective administrator account for an organization](accounts-designate-admin.md)\.  
Detective recommends that the organization management account choose an account other than their account\.  
If the account is not the organization management account, then the Detective administrator account is also the delegated administrator account for Detective in Organizations\.

****Detective source data****  
Processed, structured versions of information from the following types of feeds:  
+ Logs from AWS services, such as AWS CloudTrail logs and Amazon VPC Flow logs
+ GuardDuty findings
Detective uses the Detective source data to populate the behavior graph\. Detective also stores copies of the Detective source data to support its analytics\.

**Entity**  
An item extracted from the incoming data\.  
Each entity has a type, which identifies the type of object it represents\. Examples of entity types include IP addresses, Amazon EC2 instances, and AWS users\.  
Entities can be AWS resources that you manage, or external IP addresses that have interacted with your resources\.  
For each entity, the source data is also used to populate entity properties\. Property values can be extracted directly from source records or aggregated across multiple records\.

****Finding****  
A security issue detected by Amazon GuardDuty\.

**Finding overview**  
A single page that provides a summary of information about a finding\.  
A finding overview contains the list of involved entities for the findings\. From the list, you can pivot to the profile for an entity\.  
A finding overview also contains a details panel that contains the finding attributes\.

**High\-volume entity**  
An entity that has connections to or from a very large number of other entities during a time interval\. For example, an EC2 instance might have connections from millions of IP addresses\. The number of connections exceeds the threshold that Detective can accommodate\.  
When the current scope time contains a high\-volume time interval, Detective notifies the user\.  
See [Viewing details for high\-volume entities](https://docs.aws.amazon.com/detective/latest/userguide/high-degree-entities.html) in the *Amazon Detective User Guide*\.

****Investigation****  
The process of performing triage on suspicious or interesting activity, determining the scope, getting to its underlying source or cause, and then determining how to proceed\.

****Member account****  
An AWS account that an administrator account invited to contribute data to a behavior graph\. In the organization behavior graph, a member account can be an organization account that the Detective administrator account enabled as a member account\.  
Member accounts that are invited can respond to the behavior graph invitation and remove their account from the behavior graph\. See [For member accounts: Managing behavior graph invitations and memberships](member-account-graph-management.md)\.  
Organization accounts cannot change their membership in the organization behavior graph\.  
All member accounts can also view usage information for their account across the behavior graphs that they contribute data to\.  
They have no other access to the behavior graph\.

**Organization behavior graph**  
The behavior graph that is owned by the Detective administrator account\. The organization management account designates the Detective administrator account\. See [Designating the Detective administrator account for an organization](accounts-designate-admin.md)\.  
In the organization behavior graph, the Detective administrator account controls whether an organization account is a member account\. An organization account cannot remove itself from the organization behavior graph\.  
The Detective administrator account can also invite other accounts to the organization behavior graph\.

****Profile****  
A single page that provides a collection of data visualizations related to activity for an entity\.  
For findings, profiles help analysts to determine whether the finding is of genuine concern or a false positive\.  
Profiles provide information to support an investigation into a finding or for a general hunt for suspicious activity\.

****Profile panel****  
A single visualization on a profile\. Each profile panel is intended to help answer a specific question or questions to assist an analyst in an investigation\.  
Profile panels can contain simple key\-value pairs, tables, timelines, bar charts, or geolocation charts\.

****Relationship****  
Activity that occurs between individual entities\. Relationships are also extracted from the incoming source data\.  
Similar to an entity, a relationship has a type, which identifies the types of entities involved and the direction of the connection\. An example of a relationship type is an IP address connecting to an Amazon EC2 instance\.

****Scope time****  
The time window that is used to scope the data displayed on profiles\.  
The default scope time for a finding reflects the first and last times when the suspicious activity was observed\.  
The default scope time for an entity profile is the previous 24 hours\.