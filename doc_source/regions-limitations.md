# Amazon Detective Regions and quotas<a name="regions-limitations"></a>

When using Amazon Detective, be aware of these quotas\.

## Detective Regions and endpoints<a name="regions-endpoints"></a>

To see the list of Regions where Detective is available, see [Detective service endpoints](https://docs.aws.amazon.com/general/latest/gr/detective.html)\. 

## Detective quotas<a name="quotas"></a>

Detective has the following quotas, which cannot be configured\.


|  Resource  |  Quota  |  Comments  | 
| --- | --- | --- | 
|  Number of member accounts  |  1,200  |  The number of member accounts that an administrator account can add to a behavior graph\.  | 
|  Behavior graph data volume – volume warning  |  3\.24 TB per day  |  If the behavior graph data volume is larger than 3\.24 TB per day, then Detective displays a warning that the behavior graph is nearing the maximum allowed volume\.  | 
|  Behavior graph data volume – no new accounts  |  3\.6 TB per day  |  If the behavior graph data volume is larger than 3\.6 TB per day, then you cannot add new member accounts to the behavior graph\.  | 
|  Behavior graph data volume – stop data ingest into the behavior graph  |  4\.5 TB per day  |  If the behavior graph data volume is larger than 4\.5 TB per day, then Detective stops ingesting data into the behavior graph\. The 4\.5 TB per day reflects both normal data volume and spikes in the data volume\. To re\-enable the data ingest, you must contact AWS Support\.  | 

## Internet Explorer 11 not supported<a name="browser-limitation"></a>

You cannot use Detective with Internet Explorer 11\.