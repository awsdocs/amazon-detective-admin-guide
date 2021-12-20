# Allowed actions for accounts<a name="accounts-allowed-actions"></a>

Administrator and member accounts have access to the following Detective actions\. In the table, the values have the following meanings:
+ **Any** – The account can perform the action for all of the accounts under the same Detective administrator account\.
+ **Self** – The account can only perform the action on their own account\.
+ Dash \(–\) – The account cannot perform the action\.

This table reflects the default permissions for administrator and member accounts\. You can use custom IAM policies to further restrict access to Detective features and functions\.


|  Action  |  Administrator account \(Organization\)  |  Administrator account \(Invitation\)  |  Member \(Organization\)  |  Member \(Invitation\)  | 
| --- | --- | --- | --- | --- | 
|  View accounts  |  Any  |  Any  |  Self \(View administrator accounts\)  |  Self \(View administrator accounts\)  | 
|  Remove member account  |  Any Invited accounts are removed Organization accounts are disassociated  |  Any  |  –  |  Self  | 
|  Disable Detective  |  –  |  Self  |  –  |  –  | 
|  View behavior graph data  |  Any  |  Any  |  –  |  –  | 