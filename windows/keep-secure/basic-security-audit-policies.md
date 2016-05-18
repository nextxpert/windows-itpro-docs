---
title: Basic security audit policies (Windows 10)
description: Before you implement auditing, you must decide on an auditing policy.
ms.assetid: 3B678568-7AD7-4734-9BB4-53CF5E04E1D3
ms.pagetype: security
ms.prod: W10
ms.mktglfcycl: deploy
ms.sitesec: library
author: brianlic-msft
---
# Basic security audit policies
**Applies to**
-   Windows 10
Before you implement auditing, you must decide on an auditing policy. A basic audit policy specifies categories of security-related events that you want to audit. When this version of Windows is first installed, all auditing categories are disabled. By enabling various auditing event categories, you can implement an auditing policy that suits the security needs of your organization.
The event categories that you can choose to audit are:
-   Audit account logon events
-   Audit account management
-   Audit directory service access
-   Audit logon events
-   Audit object access
-   Audit policy change
-   Audit privilege use
-   Audit process tracking
-   Audit system events
If you choose to audit access to objects as part of your audit policy, you must enable either the audit directory service access category (for auditing objects on a domain controller), or the audit object access category (for auditing objects on a member server or workstation). Once you have enabled the object access category, you can specify the types of access you want to audit for each group or user.
## In this section
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Topic</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[Create a basic audit policy for an event category](create-a-basic-audit-policy-settings-for-an-event-category.md)</p></td>
<td align="left"><p>By defining auditing settings for specific event categories, you can create an auditing policy that suits the security needs of your organization. On devices that are joined to a domain, auditing settings for the event categories are undefined by default. On domain controllers, auditing is turned on by default.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Apply a basic audit policy on a file or folder](apply-a-basic-audit-policy-on-a-file-or-folder.md)</p></td>
<td align="left"><p>You can apply audit policies to individual files and folders on your computer by setting the permission type to record successful access attempts or failed access attempts in the security log.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[View the security event log](view-the-security-event-log.md)</p></td>
<td align="left"><p>The security log records each event as defined by the audit policies you set on each object.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Basic security audit policy settings](basic-security-audit-policy-settings.md)</p></td>
<td align="left"><p>Basic security audit policy settings are found under Computer Configuration\Windows Settings\Security Settings\Local Policies\Audit Policy.</p></td>
</tr>
</tbody>
</table>
 
 
 