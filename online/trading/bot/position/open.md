## Open position

#### Request

GET http://api.ubinary.com/online/trading/bot/open?data=JSON_DATA

where `JSON_DATA` is like

```json
{
  "BotId": "TestBot",
  "SessionKey": "47d8fd5711b84a39a696e5c3b79241f9",
  "UserId": "john@ub.com",
  "UserPassword": "111111",
  "Symbol": "EURUSD",
  "AboveBelow": "Above",
  "Duration": "0:0:30",
  "Stake": 20
}
```

#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```json
{
  "TrackingId": "This request tracking id",
  "PositionId": 123456,
  "ExpirationAt": "Position expiration time",
  "Error": "Error descrition if request fails"
}
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