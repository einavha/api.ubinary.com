## Funds

Get all fund transactions between specified dates

[Try it online](http://api.ubinary.com/nunit/page/online.html)


#### Request

GET http://api.ubinary.com/online/monitoring/quotes/snapshot?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string SnapshotName;        // unique snpashot name (usually like 'snapshot.TAG-OR-ID'
    string Symbol;              // asset symbol (upcase) of a desired snapshot 
    int UserId;                 
    DateTime From;              
    DateTime To;                
}
```

##### A valid request example

```json
{
    "SnapshotName": "snapshot.testing",
    "Symbol": "EURUSD",
    "UserId": 123456,
    "From": "2014-04-21 00:00:00",
    "To": "2014-04-21 23:00:00"
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE


##### Successful response example

```json
{
    [
      {
        "name": "EURUSD.trading-server.qa-ubinary01",
        "data": [
          {
            "x": 1405935945000.0,
            "y": 1.30731,
            "timestamp": "09:45:45.000",
            "rate": "1.30731",
            "id": "dcf125a2-8790-44ec-94ee-b26173c3d265",
            "rawId": "123"
          },
          ...
        ]
      },
      {
        "name": "EURUSD.front-end.qa-ubinary01",
        "data": [
          {
            "x": 1405935945000.0,
            "y": 1.30731,
            ...
          },
          ...
        ]
      }
    ]
}
```


#### Access restrictions

- White IP list


#### Expectations

None
