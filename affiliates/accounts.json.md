## Users (leads) report


#### Request

GET http://reports/affiliate/AFF_ID/accounts.json?from=FROM_DATE&to=TO_DATE&PagingIndex=PAGING_INDEX

where AFF_ID is affiliate id number

Parameter       | Format                  | Description
----------------|-------------------------|-------------
AFF_ID          | integer                 | Your affiliate ID number
FROM_DATE       | 'yyyy-MM-dd HH:mm:ss'   | Start from this date
FROM_TO         | 'yyyy-MM-dd HH:mm:ss'   | Until this date
PAGING_INDEX    | integer                 | 1 for first request, PagingIndex from a response if its HasMoreData is true


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

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

##### Paging index sample

**CAUTION:** PagingIndex is not the index of a desired page

**First request** - PagingIndex should be 1
http://api.ubinary.com/reports/affiliate/12345/accounts.json?from=2014-10-01 00:00:00&to=2014-11-25 00:00:00&PagingIndex=1

**Response**
'''
{
  "HasMoreData": 1,
  "PagingIndex": 101,
  "Accounts": [
  ...
'''

Response indicates that there is more data - HasMoreData is 1

**Next request** Use PagingIndex from the response
http://api.ubinary.com/reports/affiliate/12345/accounts.json?from=2014-10-01 00:00:00&to=2014-11-25 00:00:00&PagingIndex=101

**Response**
'''
{
  "HasMoreData": 0,
  "PagingIndex": 154,
  "Accounts": [
  ...
'''

No more data


#### Expectations
None

#### Access restrictions
- White IP list
