## Users

Get all **changed** users between specified dates

[Try it online](http://api.ubinary.com/nunit/page/spi_online.html)


#### Request

GET http://api.ubinary.com/online/integration/spi/users?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    DateTime From;              // starting from this date
    DateTime To;                // until this date
    int PagingIndex;            // user index to start with in case there are more results
    string Token;               // a validation token
}
```

##### A valid request example

```json
{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 0,
  "Token": ""
}```



#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    UserInfo[] Users;           // an array of retrieved users
    int PagingIndex;            // should be used in a consequent request
    int HasMoreData;            //     if there is more data
}

class UserInfo
{
    int UserId;
    string Email;
    int UserGroupId;
    int BusinessUnitId;
    string UserGroupName;
    UserStatus Status;
    string CreatedAt;
    string UpdatedAt;
    int AffProgramId;
    string UserName;
    string UserPhone;
    int AffiliateId;
}
```

##### Successful response example

```json
{
  "Users": [
    {
      "UserId": 271250,
      "Email": "vicentecolombini@gmail.com",
      "UserGroupId": 10914,
      "BusinessUnitId": 10293,
      "UserGroupName": "micro (Ubinary)",
      "Status": "Active",
      "CreatedAt": "2014-01-05 13:20:15",
      "UpdatedAt": "2014-04-21 21:52:49",
      "AffProgramId": 1,
      "UserName": "Vicente M Colombini",
      "UserPhone": "+31-65-1700812",
      "AffiliateId": 4866
    }
  ],
  "PagingIndex": 1,
  "HasMoreData": 0
}
```

##### Successful response example with consequent request fore remaining data

{
  "Users": [
    {
      "UserId": 271250,
      "Email": "vicentecolombini@gmail.com",
      "UserGroupId": 10914,
      "BusinessUnitId": 10293,
      "UserGroupName": "micro (Ubinary)",
      "Status": "Active",
      "CreatedAt": "2014-01-05 13:20:15",
      "UpdatedAt": "2014-04-21 21:52:49",
      "AffProgramId": 1,
      "UserName": "Vicente M Colombini",
      "UserPhone": "+31-65-1700812",
      "AffiliateId": 4866
    },
    {
      "UserId": 271250,
      ...
    },
    ...
  ],
  "PagingIndex": 101,
  "HasMoreData": 1
}


```json
{
  "From": "2014-04-21 00:00:00",
  "To": "2014-04-21 23:00:00",
  "PagingIndex": 101,
  "Token": ""
}
```


#### Access restrictions

- Each request may retrieve up to one hundred items
- White IP list
- Token validation


#### Expectations

None
