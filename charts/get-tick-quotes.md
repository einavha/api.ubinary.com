
### Get tick quotes

#### Request

GET http://platform.ubinary.com/fe/api/charts/get/tick/quotes

where `JSON_DATA` is like

```C#
{
    string Symbol;                          // symbol (six characters)
    string MinDate;                         // from date
    string MaxDate;                         // to date
}
```

##### A valid request examples

```json    
{
    "Symbol":"EURUSD",
    "MinDate":"03/04/2015 08:00:00",
    "MaxDate":"03/04/2015 23:56:01"
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
    AggregatedQuotesProviderArgs AggregatedQuotesProvider;

    class AggregatedQuotesProviderArgs
    {
        string ErrorCode;                   // always "RC_OK"
        string ErrorMessage;                // always empty
        DataArgs Data;
    }

    class DataArgs
    {
        string Symbol;
        int Pip;                            // number of digits in pip
        int Points;                         // number of returned points
        AggregatedQuote[] AggregatedQuotes;
    }

    class AggregatedQuote
    {
        decimal cRate;
        decimal oRate;
        decimal hRate;
        decimal lRate;
        string date;
    }
}
```


##### Successful response example

```json
{
    "TrackingId": "82.37.38",
    "ErrorCode": "Ok",
    "ErrorMessage": "",
    "AggregatedQuotesProvider": {
        "ErrorCode": "RC_OK",
        "ErrorMessage": "",
        "Data":{
            "Symbol": "EURUSD",
            "Pip": 5.0,
            "Points": 1,
            "AggregatedQuotes": [
                {
                    "cRate": 1.10935,
                    "oRate": 1.10935,
                    "hRate": 1.10935,
                    "lRate": 1.10935,
                    "date": "20150305 13:41:19"
                }
            ]
        }
    }
}
```


##### Unsuccessful response example

```json
{
  "TrackingId": "37.30.05",
  "ErrorCode": "Failed",
  "ErrorMessage": "Oops, something went wrong (37.30.05)"
}
```



#### Expectations

None

#### Access restrictins

None (public)


#### Diagnostics

http://platform.ubinary.com/fe/api/charts/get/statistics

