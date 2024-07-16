
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

_<QueryList>:_  Contains all XML queries for Event Viewer.
_<Query Id="0" Path="Security">:_ Defines a specific query (ID: 0) targeting the Security log.
_<Select Path="Security">:_ Selects all data from the Security log path.
_[System[(EventID='4624')]]:_ Selects all events with EventID '4624' (successful logon).
_and System[TimeCreated[timediff(@SystemTime) <= 604800000]]:_ Filters events created within the last 7 days (604800000 ticks).
_and EventData[Data[@Name='TargetUserName']='user']:_ Filters events for a specific username (user). Replace "user" with the desired username.
_and EventData[Data[@Name='LogonType']='2']:_ Filters events for interactive logon type ('2').
