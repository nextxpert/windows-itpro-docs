---
title: Audit Audit the access of global system objects (Windows 10)
description: Describes the best practices, location, values, and security considerations for the Audit Audit the access of global system objects security policy setting.
ms.assetid: 20d40a79-ce89-45e6-9bb4-148f83958460
ms.pagetype: security
ms.prod: W10
ms.mktglfcycl: deploy
ms.sitesec: library
author: brianlic-msft
---
# Audit: Audit the access of global system objects
**Applies to**
-   Windows 10
Describes the best practices, location, values, and security considerations for the **Audit: Audit the access of global system objects** security policy setting.
## Reference
If you enable this policy setting, a default system access control list (SACL) is applied when the device creates system objects such as mutexes, events, semaphores, and MS-DOS® devices. If you also enable the [Audit object access](basic-audit-object-access.md) audit setting, access to these system objects is audited.
Global system objects, also known as "base system objects" or "base named objects," are temporary kernel objects that have had names assigned to them by the application or system component that created them. These objects are most commonly used to synchronize multiple applications or multiple parts of a complex application. Because they have names, these objects are global in scope and, therefore, visible to all processes on the device. These objects all have a security descriptor; but typically, they do not have a NULL SACL. If you enable this policy setting and it takes effect at startup time, the kernel assigns a SACL to these objects when they are created.
The threat is that a globally visible named object, if incorrectly secured, might be acted on by a malicious program that knows the name of the object. For instance, if a synchronization object such as a mutex has a poorly constructed discretionary access control list (DACL), a malicious program can access that mutex by name and cause the program that created it to malfunction. However, the risk of this occurring is very low.
Enabling this policy setting can generate a large number of security events, especially on busy domain controllers and application servers. This might cause servers to respond slowly and force the security log to record numerous events of little significance. Auditing for access to global system objects is an all-or-nothing affair; there is no way to filter which events get recorded and which do not. Even if an organization has the resources to analyze events generated when this policy setting is enabled, it is unlikely to have the source code or a description of what each named object is used for; therefore, it is unlikely that many organizations could benefit from enabling this policy setting.
### Possible values
-   Enabled
-   Disabled
-   Not defined
### Best practices
-   Use the advanced security audit policy option, [Audit Kernel Object](audit-kernel-object.md) in Advanced Security Audit Policy Settings\\Object Access, to reduce the number of unrelated audit events that you generate.
### Location
Computer Configuration\\Windows Settings\\Security Settings\\Local Policies\\Security Options
### Default values
The following table lists the actual and effective default values for this policy. Default values are also listed on the policy’s property page.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Server type or GPO</th>
<th align="left">Default value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Default Domain Policy</p></td>
<td align="left"><p>Not defined</p></td>
</tr>
<tr class="even">
<td align="left"><p>Default Domain Controller Policy</p></td>
<td align="left"><p>Not defined</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Stand-Alone Server Default Settings</p></td>
<td align="left"><p>Disabled</p></td>
</tr>
<tr class="even">
<td align="left"><p>DC Effective Default Settings</p></td>
<td align="left"><p>Disabled</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Member Server Effective Default Settings</p></td>
<td align="left"><p>Disabled</p></td>
</tr>
<tr class="even">
<td align="left"><p>Client Computer Effective Default Settings</p></td>
<td align="left"><p>Disabled</p></td>
</tr>
</tbody>
</table>
 
## Policy management
This section describes features and tools that are available to help you manage this policy.
### Restart requirement
A restart of the computer is required before this policy will be effective when changes to this policy are saved locally or distributed through Group Policy.
### Group Policy
All auditing capabilities are integrated in Group Policy. You can configure, deploy, and manage these settings in the Group Policy Management Console (GPMC) or Local Security Policy snap-in for a domain, site, or organizational unit (OU).
### Auditing
To audit attempts to access global system objects, you can use one of two security audit policy settings:
-   [Audit Kernel Object](audit-kernel-object.md) in Advanced Security Audit Policy Settings\\Object Access
-   [Audit object access](basic-audit-object-access.md) under Security Settings\\Local Policies\\Audit Policy
If possible, use the Advanced Security Audit Policy option to reduce the number of unrelated audit events that you generate.
If the [Audit Kernel Object](audit-kernel-object.md) setting is configured, the following events are generated:
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Event ID</th>
<th align="left">Event message</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>4659</p></td>
<td align="left"><p>A handle to an object was requested with intent to delete.</p></td>
</tr>
<tr class="even">
<td align="left"><p>4660</p></td>
<td align="left"><p>An object was deleted.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>4661</p></td>
<td align="left"><p>A handle to an object was requested.</p></td>
</tr>
<tr class="even">
<td align="left"><p>4663</p></td>
<td align="left"><p>An attempt was made to access an object.</p></td>
</tr>
</tbody>
</table>
 
If the [Audit Kernel Object](audit-kernel-object.md) setting is configured, the following events are generated.
<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Event ID</th>
<th align="left">Event message</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>560</p></td>
<td align="left"><p>Access was granted to an already existing object.</p></td>
</tr>
<tr class="even">
<td align="left"><p>562</p></td>
<td align="left"><p>A handle to an object was closed.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>563</p></td>
<td align="left"><p>An attempt was made to open an object with the intent to delete it.</p>
<div class="alert">
<strong>Note</strong>  
<p>This is used by file systems when the FILE_DELETE_ON_CLOSE flag is specified in Createfile().</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="even">
<td align="left"><p>564</p></td>
<td align="left"><p>A protected object was deleted.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>565</p></td>
<td align="left"><p>Access was granted to an already existing object type.</p></td>
</tr>
<tr class="even">
<td align="left"><p>567</p></td>
<td align="left"><p>A permission associated with a handle was used.</p>
<div class="alert">
<strong>Note</strong>  
<p>A handle is created with certain granted permissions (Read, Write, and so on). When the handle is used, up to one audit is generated for each of the permissions that was used.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td align="left"><p>569</p></td>
<td align="left"><p>The resource manager in Authorization Manager attempted to create a client context.</p></td>
</tr>
<tr class="even">
<td align="left"><p>570</p></td>
<td align="left"><p>A client attempted to access an object.</p>
<div class="alert">
<strong>Note</strong>  
<p>An event will be generated for every attempted operation on the object.</p>
</div>
<div>
 
</div></td>
</tr>
</tbody>
</table>
 
## Security considerations
This section describes how an attacker might exploit a feature or its configuration, how to implement the countermeasure, and the possible negative consequences of countermeasure implementation.
### Vulnerability
A globally visible named object, if incorrectly secured, could be acted upon by malicious software by using the name of the object. For instance, if a synchronization object such as a mutex had a poorly chosen discretionary access control list (DACL), malicious software could access that mutex by name and cause the program that created it to malfunction. However, the risk of such an occurrence is very low.
### Countermeasure
Enable the **Audit: Audit the access of global system objects** setting.
### Potential impact
If you enable the **Audit: Audit the access of global system objects** setting, a large number of security events could be generated, especially on busy domain controllers and application servers. Such an occurrence could cause servers to respond slowly and force the Security log to record numerous events of little significance. This policy setting can only be enabled or disabled, and there is no way to choose which events are recorded from this setting. Even organizations that have the resources to analyze events that are generated by this policy setting are not likely to have the source code or a description of what each named object is used for. Therefore, it is unlikely that most organizations would benefit by enabling this policy setting.
To reduce the number of audit events generated, use the advanced audit policy.
## Related topics
[Security Options](security-options.md)
 
 