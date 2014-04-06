## Open position

#### Request

GET http://.../online/trading/bot/open?data=JSON_DATA

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
