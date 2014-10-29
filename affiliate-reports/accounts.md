## accounts


#### Request

GET http://reports/affiliate/AFF_ID/accounts.xml?from=FROM_DATE&to=TO_DATE&PagingIndex=PAGING_INDEX

where AFF_ID is affiliate id number

Parameter       | Format                  | Description
----------------|-------------------------|-------------
AFF_ID          | integer                 | Your affiliate ID number
FROM_DATE       | 'yyyy-MM-dd HH:mm:ss'   | Start from this date
FROM_TO         | 'yyyy-MM-dd HH:mm:ss'   | Until this date
PAGING_INDEX    | integer                 | 1 for first request, PagingIndex from previous request if it has more data


##### A valid first request example

http://reports/affiliate/5647/accounts.xml?from=2014-06-22 00:00:00&to=2014-06-22 23:59:59&PagingIndex=1



#### Response

Status | Response body
-------|--------------
200    | XML_RESPONSE

where `XML_RESPONSE` is like

```C#
{
    int PagingIndex;            // should be used in a consequent request
    int HasMoreData;            //     if there is more data
    UserInfo[] Users;           // an array of retrieved users
}

class UserInfo
{
    DateTime TransactionDate;   // Lead creation date
    string cTag;                // the ad_server parameter sent with registration API
    int AccountID;              // Unique account ID
    string Type;                // 'lead' or 'user' (a user is a lead with one successful login)
    string FirstName;
    string LastName;
}
```

##### Successful response example

```json
{
    "SessionKey": "77732467768c44bc8316ad21db46ef11",
    "Error": null
}
```


##### Unsuccessful response example

```json
{
  "SessionKey": null,
  "Error": "BotId 'MyBot' is not registered"
}
```


#### Expectations

None
