
### Set additional user details

#### Request

GET http://api.ubinary.com/registration/v2/set/user/details?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    int UserId;                             // user id (mandatory)
    string FirstName;                       // optional (can be null)
    string LastName;                        // optional (can be null)
    string CountryCode;                     // optional (can be null) two letters ISO country code
    string PhoneNumber;                     // optional (can be null)
    DateTime? DateOfBirth;                  // optional (can be null)
    int? EmployementStatus;                 // optional (can be null) see table below
    decimal? AnnualIncome;                  // optional (can be null) see table below
    decimal? NetWorth;                      // optional (can be null) see table below
    decimal? BinaryExpirience;              // optional (can be null) see table below
}
```

##### A valid request examples

```json    
{
    "UserId": 291935,
    "FirstName": "John",
    "LastName": "Smith",
    "CountryCode": "GB",
    "PhoneNumber": "44-12345678",
    "DateOfBirth": "27-Mar-1977",
    "EmployementStatus": 1,
    "AnnualIncome": 2,
    "NetWorth": 3,
    "BinaryExpirience": 1
}
```

```json    
{
    "UserId": 111222,
    "FirstName": "John",
    "CountryCode": "GB",
    "PhoneNumber": "44-12345678",
    "DateOfBirth": null,
    "NetWorth": 3,
    "BinaryExpirience": null
}
```

Note: fields `EmploymentStatus`, `AnnualIncome`, `NetWorth` and `BinaryExpirience` are mapped as the following


EmploymentStatus        | Mapped to
------------------------|--------
Not selected            | 0
Employed                | 1
Unemployed              | 2
Self employed           | 3
Pension	                | 4
Other                   | 5


AnnualIncome            | Mapped to
------------------------|--------
Not selected            | 0
Less than $25,000       | 1
$25,001-$50,000         | 2
$50,001-$75,000         | 3
$75,000-$100,000        | 4
$100,001-$250,000       | 5
$250,001-$500,000       | 6
More than $500,000      | 7


NetWorth                | Mapped to
------------------------|--------
Not selected            | 0
Less than $25,000       | 1
$25,001-$100,000        | 2
$100,001-$200,000       | 3
$200,001-$300,000       | 4
$300,001-$500,000       | 5
$500,001-$750,000       | 6
$750,001-$1,000,000     | 7
More than $1,000,000    | 8


BinaryExpirience        | Mapped to
------------------------|--------
Not selected            | 0
Less than 1 year        | 1
1-3 years               | 2
3-5 years               | 3
5+ years                | 4



#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#

enum EligibilityStatus { Eligible, NotEligible }

{
    string TrackingId;            // Tracking id for troubleshooting
    string ErrorCode;             // "Ok" if request succeeds, short error code if request fails
    string ErrorMessage;          // error description if request fails
}
```

##### Successful response example

```json
{
    "TrackingId": "12.34.56",
    "ErrorCode": "Ok",
    "ErrorMessage": null,
}
```


##### Unsuccessful response example

```json
{
  "TrackingId": "37.30.05",
  "ErrorCode": "Failed",
  "ErrorMessage": "Unknown country code 'UK'"
}
```



#### Expectations

- UserId exists
- User is logged in

