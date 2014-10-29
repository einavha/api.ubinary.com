## Bot integration

#### Bot registration
- Ubinary provides you with `BotId` and `LoginKey`
- A white IPs list is required from your side

#### Bot trading
- Each bot has to login in order to open positions - [Login API](login.md)
- Each login starts a session (the session has an expiration timeout)
- During the session bot is allowed to open positions - [Open position API](position/open.md)

#### Bot testing
- Ubinary provides you with a test user
- Please use this [Bot trading test page](http://api.ubinary.com/nunit/page/bots.html)
