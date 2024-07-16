
# IR Tools

## QueryList Analysis

This section explains an XML snippet used in Event Viewer queries to filter for successful logon events of a specific user within the past 7 days:

```
<QueryList>
  <Query Id="0" Path="Security">
    <Select Path="Security">
      *[System[(EventID='4624')]]
      and
      System[TimeCreated[timediff(@SystemTime) <= 604800000]]
      and
      EventData[Data[@Name='TargetUserName']='user']
      and
      EventData[Data[@Name='LogonType']='2']
    </Select>
  </Query>
</QueryList>

```

```<QueryList>```:  Contains all XML queries for Event Viewer. <br/>
```<Query Id="0" Path="Security">```: Defines a specific query (ID: 0) targeting the Security log. <br/>
```<Select Path="Security">```: Selects all data from the Security log path. <br/>
```System[(EventID='4624')]```: Selects all events with EventID '4624' (successful logon). <br/>
```System[TimeCreated[timediff(@SystemTime) <= 604800000]]```: Filters events created within the last 7 days (604800000 ticks, A single tick represents one hundred nanoseconds or one ten-millionth of a second). <br/>
```EventData[Data[@Name='TargetUserName']='user']```: Filters events for a specific username (user). Replace "user" with the desired username or remove for all users . <br/>
```EventData[Data[@Name='LogonType']='2']```: Filters events for interactive logon type ('2'). <br/>

## Logon Types: <br/> <br/>
![Logon Types](https://github.com/shlomo120/IR_Tools/blob/687cc421ca23207c129ee34f7bd4d7d6a4846a64/Logon%20Types.png) <br/> 
Referenes: Microsoft Documentation, [Administrative tools and logon types](https://learn.microsoft.com/en-us/windows-server/identity/securing-privileged-access/reference-tools-logon-types).

<br/>

## Ping Castle <br/> <br/> 
Ping Castle is a valuable tool for post-hack incident response and security posture assessment. <br/> 
By identifying the initial attack vector, it can prioritize patching and configuration changes to address the root cause. <br/> 
Ping Castle can help identify systems that might have been compromised beyond the initial breach. <br/> 
Running Ping Castle after a breach can help demonstrate that you're taking proactive steps to improve security. <br/> 
Analyzing the results of Ping Castle can help to refine your incident response plan for future incidents. <br/> 
![Ping Castle](https://www.pingcastle.com/wp/wp-content/uploads/2018/09/ipad1-e1536782462467.png) <br/> 
Download [Ping Castle](https://www.pingcastle.com/). <br/> 

## Common Event Codes <br/> <br/>
**File System Activity Related Events:** <br/>
* 4660: An object has been deleted. <br/>
* 4661: An object was accessed. <br/>
* 4662: An object was opened. <br/>
* 4663: A new file has been created. <br/>
* 4656: A handle to an object has been requested. This event can indicate file access attempts. <br/> <br/>
**Privilege and Security Policy Changes:** <br/>
* 4624: An account was successfully logged on. <br/>
* 4634: An account was logged off. <br/>
* 4672: A special privilege has been assigned to a new process. This could indicate potential privilege escalation. <br/>
* 4673: A privilege was used (process uses a special privilege). <br/>
* 4674: A special privilege has been revoked from a process. <br/> <br/>
**Process and Network Related Events** <br/>
* 4688: A new process has been created. This event can be used to track process creation and potential malicious activity. <br/>
* 4689: A group membership has been changed. This indicates changes to user or group privileges and can be a sign of potential security policy modifications. <br/>
* 4717: A system security policy was changed. <br/>
* 4719: A user account was enabled. <br/>
* 4720: A user account was disabled. <br/>
* 4728: A directory service object (like user) was created in Active Directory. <br/> 
* 4729: A directory service object (like user) was modified in Active Directory.<br/> 
* 4730: A directory service object (like user) was deleted in in Active Directory <br/>





