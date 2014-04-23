## Open position

#### Request

GET http://api.ubinary.com/online/trading/bot/position/open?data=JSON_DATA

where `JSON_DATA` is like

```json
{
  "BotId": "MyBotName",                                 // The same as in Login
  "SessionKey": "47d8fd5711b84a39a696e5c3b79241f9",     // Provided by successful login 
  "UserId": "john@ub.com",                              // User emaile or user id
  "UserPassword": "111111",                             // User password
  "Symbol": "EURUSD",                                   // Symbol of an asset to open position on
  "AboveBelow": "Above",                                // Direction should be 'Above' or 'Below'
  "Duration": "0:0:30",                                 // Position duration
  "Stake": 20                                           // Position volume USD
}
```

#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```json
{
  "TrackingId": "String",                 Tracking id for troubleshooting
  "PositionId": "Int",                    "Id of an successfully opened position",
  "ExpirationAt": "Date",                 "Comment": "Position expiration point"
  "Error": "String"                       // null if request succeeds, error description if request fails
}
```

```C#
{
  string TrackingId;        // Tracking id for troubleshooting
  int PositionId;           // Id of an successfully opened position
  DateTime ExpirationAt;    // Comment": "Position expiration point
  string Error;             // null if request succeeds, error description if request fails
}
```

```Pascal
TrackingId : String;      { Tracking id for troubleshooting }
PositionId : Integer;     { Id of an successfully opened position }
ExpirationAt : Date;      // Comment": "Position expiration point
Error : String;           // null if request succeeds, error description if request fails
```


#### Successful response example

```json
{
  "TrackingId": "d24d7427bd6b431e8ee46aa84dd56ddd",
  "PositionId": 674191,
  "ExpirationAt": "22-Apr-2014 16:07:36",
  "Error": null
}
```


#### Unsuccessful response example

```json
{
  "TrackingId": "a8654255cf1745b899f517b7b3ebdc3d",
  "PositionId": 0,
  "ExpirationAt": "01-Jan-0001 00:00:00",
  "Error": "User 299216 (bot@ub.com): login failed; password is wrong"
}
```


#### Expectations

- Bot is loged in
- Bot session key is not expired