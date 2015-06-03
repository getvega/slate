# Authentication

> Try this with your `applicationId` and `applicationSecret`

```shell
curl https://api.cubyn.com/v1 \
    -u my-app:e336bfdbe671af94c4b9dfcb
```

All endpoints except `GET /version` require a proper authentication. If you do not have your application credentials yet, please write your request at [api@cubyn.com](mailto:api@cubyn.com).
Your API credentials will consist of an `applicationId` and an `applicationSecret`. Beware that these credentials carry many privileges - so keep them secret!

Authentication is done through [HTTP's Basic Auth](http://en.wikipedia.org/wiki/Basic_access_authentication) with you application credentials.