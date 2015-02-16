
### Get additional user details

#### Request

GET http://api.ubinary.com/users/get/user/details?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    int UserId;                             // user id (or email)
}
```

##### A valid request examples

```json    
{
    "UserId": 111222
}
```

#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    string TrackingId;                      // Tracking id for troubleshooting
    string ErrorCode;                       // "Ok" if request succeeds, short error code if request fails
    string ErrorMessage;                    // error description if request fails
    bool HasKycDocuments;                   // user uploaded at leaset one of KYC documents
    bool BlockedKyc;                        // user is blocked by KYC policy
    KycArgs Kyc;                            // KYC details (see below)

    class KycArgs
    {
        bool IsEnabled;                     // KYC logic is enabled / disabled
        bool UserIsBlocked;                 // user is already blocked by KYC policy
        bool UserHasAnyDocument;            // user has any document complient with 
        int UserWillBeBlockedInSeconds;     // seconds remain until user is blocked by KYC policy 
    }
}
```

##### Successful response example

```json
{
  "TrackingId": "82.37.38",
  "ErrorCode": "Ok",
  "ErrorMessage": "",
  "Kyc": {
    "IsEnabled": true,
    "UserIsBlocked": false,
    "UserHasAnyDocument": false,
    "UserWillBeBlockedInSeconds": 129457
  }
}
```


##### Unsuccessful response example

```json
{
  "TrackingId": "37.30.05",
  "ErrorCode": "Failed",
  "ErrorMessage": "User 111222 is not the logged in user"
}
```



#### Expectations

- UserId exists
- User is logged in


#### Access restrictins

None (public)
