---
id: xtra-err-msgs
title: Orbis Error Codes and Messages
sidebar_label: Error Messages
---

The following table lists platform error conditions along with their corresponding HTTP codes. 

|Orbis Error  |HTTP Code  |Error Description
|--           |---        |---
|1000   |401    	|Authentication token missing
|1001   |401    	|Authentication token invalid
|1002   |401    	|Authentication token expired
|1003   |403		|Not authorized to read requested resource
|1004   |403		|Not authorized to write to requested resource
|1005   |403		|Not authorized to reset password
|1006   |401    	|Invalid APIKey
|1040   |404    	|Resource not found
|1041   |404    	|Account not found
|1042   |400    	|Password mismatch
|1043   |409    	|Resource already exists
|1044   |400    	|Account not logged in
|1045   |400    	|Email cannot be verified
|1046   |400        |Email not verified; cannot send reset password link to account
|1047   |422        |Account ID must be a valid email address
|1048   |422        |New password failed validation
|1050   |400        |Bad data
|1051   |404        |Device not found
|1060   |400		|Incomplete data
|1070   |413		|Request too large
|1100   |500		|Internal server error
|1101   |500		|Database misconfiguration error
|1102   |500		|Error deleting asset
|1103   |400		|Format of request invalid
|1104   |400		|Unsupported category
|1105   |400		|Unsupported category key
|1201   |400		|Receipt validation check failed
|1202   |400		|The receipt shows the purchase/subscription as cancelled
|1401   |400		|Tenant not found
|1402   |400		|Token type not recognized
|1403   |400		|Token type not supported by tenant
|1404   |403		|Account not entitled to play requested stream  
|1405   |403		|Account cannot exceed streaming policy limits set by tenant
|1406   |403        |Account cannot update an item to a version that has been superseded
|1407   |403		|Account not currently in whitelisted areas for the requested content
|1408   |403		|Account cannot exceed concurrent device limits set by tenant policy
|1409   |403		|Requested content is blacked out for the account's current location

[Back to top of Error Messages](xtra-err-msgs)

<!--
See the 
[Orbis Error Codes](https://istreamplanet.atlassian.net/wiki/spaces/OD/pages/2215015/Orbis+Error+Codes), 
based on the errornums.go file.
-->