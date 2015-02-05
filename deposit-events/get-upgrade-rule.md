## Get deposit upgrade rule

GET http://api.ubinary.com/deposit/get/upgrade/rule?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string UserId;              // user id or email
    decimal Amount;             // amount user is going to deposit
    string PaymentMethod;       // payment method
}
```

For localication see the coresponding section below


##### A valid request example

http://api.ubinary.com/deposit/get/upgrade/rule?data=%7B%22UserId%22:%22john@ub.com%22,%22Amount%22:200,%22PaymentMethod%22:%22Neteler%22%7D

```json
{
    "UserId": "john@ub.com",
    "Amount": 200,
    "PaymentMethod": "Neteler"
}
```

http://api.ubinary.com/deposit/get/upgrade/rule?data=%7B%22UserId%22:%22123456%22,%22Amount%22:200,%22PaymentMethod%22:%22Neteler%22%7D

```json
{
    "UserId": 123456,
    "Amount": 200,
    "PaymentMethod": "Neteler"
}
```

##### Localization

Default language is english

**English**:  http://api.ubinary.com/en/deposit/get/upgrade/rule?data=JSON_DATA   
**Arabic**:  http://api.ubinary.com/ar/deposit/get/upgrade/rule?data=JSON_DATA   
**Russian**:  http://api.ubinary.com/ru/deposit/get/upgrade/rule?data=JSON_DATA   



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
    decimal UpgradeTo;            // upgrade to this amount
    string UpgrageMsg;            // upgrade message (localized)
}
```

#### Successful response example

```json
{
  "TrackingId": "99.89.96",
  "ErrorCode": "Ok",
  "ErrorMessage": "",
  "UpgradeTo": 750.0,
  "UpgrageMsg":"When depiting with Netteller"
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

- UserId exists
- User is logged in


#### Access restrictions

