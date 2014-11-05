## Open position

[Try it online](http://api.ubinary.com/nunit/page/bots.html)


#### Request

GET http://api.ubinary.com/trading/user/get/balance?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string BotId;               // Bot id (provided by Ubinary)
    string SessionKey;          // Returned by a successful login   
    string UserEmail;           // User email
}
```

##### A valid request example

```json
{
    "BotId": "MyBotName",
    "SessionKey": "47d8fd5711b84a39a696e5c3b79241f9",
    "UserEmail": "john@ub.com",
}
```

#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    string TrackingId;            // Tracking id for troubleshooting
    string ErrorCode;             // null if request succeeds, short error code if request fails
    string ErrorMessage;          // error description if request fails
    decimal Balance;              // user's balance
    decimal FreeBalance;          // user's free balance (balance minus open positions)
    decimal Stakes;               // sum of user's open positions
}
```

##### Successful response example

```json
{
    "TrackingId": "d24d7427bd6b431e8ee46aa84dd56ddd",
    "ErrorCode": null,
    "ErrorMessage": null,
    "Balance": 5661.95,
    "Stakes": 100,
    "FreeBalance": 5561.95
}
```


##### Unsuccessful response example

```json
{
  "TrackingId": "37.30.05",
  "ErrorCode": "Failed",
  "ErrorMessage": "User 'john@ub.com' is not registered"
}
```


#### Expectations

- Bot is loged in
- Bot session key is not expired
