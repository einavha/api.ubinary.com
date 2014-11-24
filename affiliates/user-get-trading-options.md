## Get trading options

GET http://api.ubinary.com/trading/affiliate/12345/user/get/trading/options?data=JSON_DATA

where `12345` - is your affiliate id and `JSON_DATA` is like

```C#
{
    string UserId;              // not supported yet
}
```

##### A valid request example

http://api.ubinary.com/trading/affiliate/12345/user/get/open/positions?data={"UserId":""} 

```json
{
    "UserId": ""
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
    Option[] Options;             // array of asset options
}

class Option
{
    string Symbol;
    Deal[] Deals;
}

class Deal
{
    public int DealId;
    public DateTime StartAt;
    public DateTime EndAt;
    public decimal PayMatch;
    public decimal PayNoMatch;
    public decimal MinStake;
    public decimal MaxStake;
}

```

#### Successful response example

```json
{
  "TrackingId": "87.35.06",
  "ErrorCode": "Ok",
  "ErrorMessage": "",
  "Options": [
    {
      "Symbol": "EURUSD",
      "Deals": [
        {
          "DealId": 948504,
          "StartAt": "24-Nov-2014 09:35:00",
          "EndAt": "24-Nov-2014 11:00:00",
          "PayMatch": 75,
          "PayNoMatch": 0,
          "MinStake": 20,
          "MaxStake": 100000
        }
      ]
    }
  ]
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
None

#### Access restrictions
- White IP list
