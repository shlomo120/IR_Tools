
# IR_Tools

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
```  <Query Id="0" Path="Security">```: Defines a specific query (ID: 0) targeting the Security log. <br/>
```    <Select Path="Security">```: Selects all data from the Security log path. <br/>
```      [System[(EventID='4624')]]```: Selects all events with EventID '4624' (successful logon). <br/>
```      and System[TimeCreated[timediff(@SystemTime) <= 604800000]]```: Filters events created within the last 7 days (604800000 ticks). <br/>
```      and EventData[Data[@Name='TargetUserName']='user']```: Filters events for a specific username (user). Replace "user" with the desired username. <br/>
```      and EventData[Data[@Name='LogonType']='2']```: Filters events for interactive logon type ('2'). <br/>
