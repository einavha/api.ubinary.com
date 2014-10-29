## User login

[Try it online](http://api.ubinary.com/nunit/page/bots.html)


#### Request

GET http://api.ubinary.com/trading/user/login?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string UserEmail;               // Bot id (provided by Ubinary)
    string UserPassword;            // Login key (provided by Ubinary)
}
```

##### A valid request example

```json
{
  "UserEmail": "john@company.com",
  "LoginKey": "111111"
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    string TrackingId;          // tracking id of this request for a later troubleshooting
    string ErrorCode;           // short error code; 'Ok' - for successful request
    string ErrorMessage;        // error description (if there is an error)
}
```

##### Successful response example

```json
{
    "TrackingId": "12.34.56",
    "ErrorCode": "Ok",
    "Error": ""
}
```


##### Unsuccessful response example

```json
{
    "TrackingId": "12.34.56",
    "ErrorCode": "RC_PASSWORD_IS_WRONG",
    "Error": "Login failed"
}
```


#### Expectations

None
