﻿## Buy me out

#### Request

GET http://api.ubinary.com/online/trading/bot/buy-me-out?data=JSON_DATA

where `JSON_DATA` is like

```json
{
}
```

#### Response

Status | Meaning           | Response body
-------|-------------------|-------------
200    | successful        | JSON_RESPONSE
400    | bad request (missing fields or wrong format) | has error description
500    | Server side error | has error description

where `JSON_RESPONSE` is like

```json
{
}
```

#### Expectations