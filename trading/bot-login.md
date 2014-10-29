## Bot login

[Try it online](http://api.ubinary.com/nunit/page/bots.html)


#### Request

GET http://api.ubinary.com/trading/bot/login?data=JSON_DATA

where `JSON_DATA` is like

```C#
{
    string BotId;               // Bot id (provided by Ubinary)
    string LoginKey;            // Login key (provided by Ubinary)
}
```

##### A valid request example

```json
{
  "BotId": "MyBot",
  "LoginKey": "MyLoginKey"
}
```


#### Response

Status | Response body
-------|--------------
200    | JSON_RESPONSE

where `JSON_RESPONSE` is like

```C#
{
    string SessionKey;          // Session key to use in API calls
    string Error;               // null if request succeeds, error description if request fails
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
