# Electrolytic

Push notifications for electron apps.

First sign up on https://electrolytic.app and get your `App key` and `Secret`.

## Installation

```shell
npm install --save electrolytic
```

## Usage in app

```javascript
const Electrolytic = require('electrolytic')

const electrolytic = Electrolytic({
  appKey: '<Your-App-Key>',
})

electrolytic.on('token', (token) => {
  // send this token to your server, you'll need it to send push
  console.log('user token', token);
})

electrolytic.on('push', (payload) => {
  console.log('got push notification', payload)
})
```

## Send push from your server

Send a `POST` request to `https://api.electrolytic.app/push/send`

with JSON body with following schema:

```javascript
{
  "appKey": "<You-App-Key>",
  "appSecret": "<Your-App-Secret>",
  "target": ["<token>"], // should always be an array. multiple tokens can be used to send same payload to all of them.
  "payload": "hola, here's a push!" // can also be a JSON object
}
```

### License

SOME RIGHTS RESERVED

See [License](https://github.com/Electrolytic/electrolytic/blob/master/LICENSE.md)
