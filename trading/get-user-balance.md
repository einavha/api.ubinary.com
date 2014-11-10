## Get user balance

[Try it online](http://api.ubinary.com/nunit/page/bots.html)


#### Request

GET http://api.ubinary.com/trading/user/get/balance?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string BotId;               // Bot id (provided by Ubinary)
    string UserEmail;           // User email
}
```

##### A valid request example

```json
{
    "BotId": "MyBotName",
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
    string UserName;              // user name (email)
    string FirstName;
    string LastName;
    decimal Balance;              // user's balance
    decimal FreeBalance;          // user's free balance (balance minus open positions)
    decimal Stakes;               // sum of user's open positions
    decimal Pnl;                  // accumulated PNL of a user
}
```

##### Successful response example

```json
{
    "TrackingId": "12.34.56",
    "ErrorCode": null,
    "ErrorMessage": null,
    "UserName": "john@company.com",
    "FirstName": "John",
    "LastName": "Smith",
    "Balance": 5661.95,
    "FreeBalance": 5561.95,
    "Stakes": 100,
    "FreeBalance": 5561.95,
    "Pnl": -2345.78
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

- bot is active
- white IP list
