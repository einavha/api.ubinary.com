## Get user balance


#### Request

GET http://api.ubinary.com/trading/user/get/balance?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string BotId;               // Bot id (provided by Ubinary)
    string UserEmail;           // User email or user id
}
```

##### A valid request example

```json
{
    "BotId": "MyBotName",
    "UserEmail": "john@ub.com",
}
```

```json
{
    "BotId": "MyBotName",
    "UserEmail": 123456,
}
```

#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#

enum EligibilityStatus { Eligible, NotEligible }

{
    string TrackingId;            // Tracking id for troubleshooting
    string ErrorCode;             // "Ok" if request succeeds, short error code if request fails
    string ErrorMessage;          // error description if request fails
    int UserId;                   // user id
    string UserName;              // user name (email)
    string FirstName;
    string LastName;
    decimal Balance;              // user's balance
    decimal FreeBalance;          // user's free balance (balance minus open positions)
    decimal Stakes;               // sum of user's open positions
    decimal Pnl;                  // accumulated PNL of a 
    string Eligibility;           // values: Eligible, NotEligible
    bool HasDeposits;             // 'true' if first time deposit is done, 'false' otherwise
    string Country,               // currently is not availible (use CountryCode)
    string CountryCode,           // two letters country code
    string Phone,                 // user's phone number
    Date RegistrationDate,        // user's registration (creation) date and time (YYYY-MM-DD hh:mm:ss)
    Date FirstDepositDate         // user's first deposit date and time (YYYY-MM-DD hh:mm:ss)
}
```

##### Successful response example

```json
{
    "TrackingId": "12.34.56",
    "ErrorCode": "Ok",
    "ErrorMessage": null,
    "UserId": 123456,
    "UserName": "john@company.com",
    "FirstName": "John",
    "LastName": "Smith",
    "Balance": 5661.95,
    "FreeBalance": 5561.95,
    "Stakes": 100,
    "FreeBalance": 5561.95,
    "Pnl": -2345.78,
    "Eligibility": "Eligible",
    "HasDeposits": true,
    "Country": null,
    "CountryCode": "GB",
    "Phone": "+972-54-123456",
    "RegistrationDate": "2014-02-10 07:29:54",
    "FirstDepositDate": "2014-02-10 09:49:59"
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
