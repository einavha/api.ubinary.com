
### Set additional user details

#### Request

GET http://api.ubinary.com/registration/set/user/details?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    int UserId;                     // should not be empty if UserGuid is empty
    Guid UserGuid;                  // should not be empty if UserId is empty
    DateTime DateOfBirth;
    int EmployementStatus;
    decimal AnnualIncome;
    decimal NetWorth;
    decimal BinaryExpirience;
}
```

##### A valid request examples

```json    
{
    "UserId": 291935,
    "DateOfBirth": "27-April-1977",
    "EmployementStatus": 1,
    "AnnualIncome": 2,
    "NetWorth": 3,
    "BinaryExpirience": 1
}
```

```json    
{
    "UserGuid": "F2092A4CBDA07907E040CA0A011430D9",
    "DateOfBirth": "27-April-1977",
    "EmployementStatus": 1,
    "AnnualIncome": 2,
    "NetWorth": 3,
    "BinaryExpirience": 1
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

Status | Meaning           | Response body
-------|-------------------|-------------
200    | successful        | is empty
400    | bad request (missing fields or wrong format) | has error description
500    | Server side error | has error description


#### Expectations

User with a specified id has already been created.

