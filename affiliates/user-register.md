## Register user

GET http://api.ubinary.com/trading/affiliate/12345/user/register?data=JSON_DATA

where `12345` - is your affiliate id and `JSON_DATA` is like

```C#
{
    string FirstName;           // First name
    string LastName;            // Last name
    string PhoneNumber;         // Phone number
    string Email;               // Email
    string Password;            // Password
    string Tlid;                // optional - tracking link id
    string FromIp;              // optional - explicit client IP, if not specified IP is taken from request
    string CountryCode;         // optional - explicit country code, if not specified country is based on IP
    string Ctag;                // optional - a free parameter; it comes back in report API
}
```

##### A valid request example

http://api.ubinary.com/trading/affiliate/12345/user/register?data=%7B%22FirstName%22:%22TestJohn%22,%22LastName%22:%22TestSmith%22,%22PhoneNumber%22:%22044-1234567%22,%22Email%22:%22test-12317@ub.com%22,%22Tlid%22:%22abcd-efgh-ighk%22,%22Password%22:%22111111%22,%22CountryCode%22:%22%22,%22FromIp%22:%22%22,%22Ctag%22:%22%22%7D

```json
{
  "FirstName": "TestJohn",
  "LastName": "TestSmith",
  "PhoneNumber": "044-1234567",
  "Email": "test-12317@ub.com",
  "Tlid": "abcd-efgh-ighk",
  "Password": "111111",
  "CountryCode": "GB",
  "FromIp": "211.148.218.20",
  "Ctag": "user.JKFDSIE3243-4V432"
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
    string ErrorCode;             // "Ok" if request succeeds, short error code if request fails
    string ErrorMessage;          // error description if request fails
    int UserId;                   // The id of a newly created user
}
```

##### Successful response example

```json
{
  "TrackingId": "74.77.97",
  "ErrorCode": "Ok",
  "ErrorMessage": "",
  "UserId": 299493
}
```


##### Unsuccessful response example

```json
{
  "TrackingId": "50.97.61",
  "ErrorCode": "RC_USER_ALREADY_EXISTS",
  "ErrorMessage": "Oops, something went wrong (50.97.61)",
  "UserId": 0
}
```

```json
{
  "TrackingId": "50.01.14",
  "ErrorCode": "Failed",
  "ErrorMessage": "Unknown country code 'UK'"
}
```


#### Expectations
- None

#### Access restrictions
- None (public)
