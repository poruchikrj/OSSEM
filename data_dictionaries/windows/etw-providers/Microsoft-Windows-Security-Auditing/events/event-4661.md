# Event ID 4661: A handle to an object was requested

## Description
This event indicates that a handle was requested for either an Active Directory object or a Security Account Manager (SAM) object. If access was declined, then Failure event is generated. This event generates only if Success auditing is enabled for the Audit Handle Manipulation subcategory.

## Data Dictionary
|Standard Name|Field Name|Type|Description|Sample Value|
|---|---|---|---|---|
|user_sid|SubjectUserSid|SID|SID of account that requested a handle to an object.|`S-1-5-21-3457937927-2839227994-823803824-1104`|
|user_name|SubjectUserName|UnicodeString|the name of the account that requested a handle to an object.|`dadmin`|
|user_domain|SubjectDomainName|UnicodeString|subject's domain or computer name.|`CONTOSO`|
|user_logon_id|SubjectLogonId|HexInt64|hexadecimal value that can help you correlate this event with recent events that might contain the same Logon ID, for example, "4624: An account was successfully logged on."|`0x4280e`|
|object_server|ObjectServer|UnicodeString|has "Security Account Manager" value for this event.|`Security Account Manager`|
|object_type|ObjectType|UnicodeString|the type or class of the object that was accessed.|`SAM_DOMAIN`|
|object_name|ObjectName|UnicodeString|the name of an object for which access was requested.|`DC=contoso,DC=local`|
|object_handle_id|HandleId|Pointer|hexadecimal value of a handle to Object Name. This field can help you correlate this event with other events that might contain the same Handle ID, for example, "4662: An operation was performed on an object." This parameter might not be captured in the event, and in that case appears as "0x0".|`0xdd64d36870`|
|transaction_guid|TransactionId|GUID|unique GUID of the transaction. This field can help you correlate this event with other events that might contain the same the Transaction ID, such as "4660(S): An object was deleted."|`{00000000-0000-0000-0000-000000000000}`|
|object_access_list|AccessList|UnicodeString|the list of access rights which were requested by Subject\Security ID. These access rights depend on Object Type.|`%%5400`|
|object_access_mask|AccessMask|HexInt32|hexadecimal mask for the operation that was requested or performed.|`0x2d`|
|object_privilege_list|PrivilegeList|UnicodeString|the list of user privileges which were used during the operation, for example, SeBackupPrivilege. This parameter might not be captured in the event, and in that case appears as "-".|`-`|
|object_properties|Properties|UnicodeString|depends on Object Type. This field can be empty or contain the list of the object properties that were accessed. See more detailed information in "4661: A handle to an object was requested" from Audit SAM subcategory.|`-`|
|object_restricted_sid_count|RestrictedSidCount|UInt32|Number of restricted SIDs in the token. Applicable to only specific Object Types.|`-`|
|process_id|ProcessId|Pointer|hexadecimal Process ID of the process that requested the handle. Process ID (PID) is a number used by the operating system to uniquely identify an active process.|`0x9000a000d002d`|
|process_path|ProcessName|UnicodeString|full path and the name of the executable for the process.|`{bf967a90-0de6-11d0-a285-00aa003049e2} %%5400 {ccc2dc7d-a6ad-4a7a-8846-c04e3cc53501}`|

## References
* [MS Source](https://github.com/MicrosoftDocs/windows-itpro-docs/blob/master/windows/security/threat-protection/auditing/event-4661.md)
* [MS Security Auditing Category - DS Access](https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-audit-policy-settings#ds-access)
* [MS Security Auditing Category - Object Access](https://docs.microsoft.com/en-us/windows/security/threat-protection/auditing/advanced-security-audit-policy-settings#object-access)
* [MS Security Auditing Sub-category - Audit Directory Service Access](https://github.com/MicrosoftDocs/windows-itpro-docs/tree/master/windows/security/threat-protection/auditing/audit-directory-service-access.md)
* [MS Security Auditing Sub-category - Audit SAM](https://github.com/MicrosoftDocs/windows-itpro-docs/tree/master/windows/security/threat-protection/auditing/audit-sam.md)

## Tags
* etw_level_Informational
* etw_task_task_0
* DS Access
* Object Access
* Audit Directory Service Access
* Audit SAM