## Login

#### Request

GET http://api.ubinary.com/online/trading/bot/login?data=JSON_DATA

where `JSON_DATA` is like

```json
{
  "BotId": "<BOT_ID>",
  "LoginKey": "<LOGIN_KEY>"
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```json
{
  "SessionKey": "A key bot should provide in order to open position",
  "Error": "null if request succeeds, error description if request fails"}
```


#### Successful response example

```json
{
  "SessionKey": "77732467768c44bc8316ad21db46ef11",
  "Error": null
}
```


#### Unsuccessful response example

```json
{
  "SessionKey": null,
  "Error": "BotId 'MyBot' is not registered"
}
```


#### Expectations

None
