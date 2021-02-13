# Electrolytic

![Electrolytic on NPM](https://img.shields.io/npm/v/electrolytic?color=green&label=Electrolytic%20on%20NPM&logo=Electrolytic%20on%20NPM&style=for-the-badge)

A suite of features to make your desktop apps even more powerful 💪

- 🔎 **Analytics**; how many users, what platforms, where're they from?
- ☁️ **Cloud config**; JSON object that you can change via our dashboard and your app can access via this package, instantly.
- ⚡️ **Push notifications**; send silent (or loud) information from your servers to your app and users.

... and much more for electron apps.

This package is:

- 🚀 **Lightweight** (under 10KB gzipped). Yes, we're aware of and fully relate to the memes about the size of `node_modules` 😂
- 👌 is **not dependent** on any other package, only core code. We wrote every bit of it ourselves. No threat of package compromise!
- 🏎 **Performant**. It uses the bare-minimum resources to keep your app running faster. Not a memory hog.
- 🔐 **Privacy-respecting**. It only collects and sends the data to our servers when you tell it to. Respecting your app's and its users' privacy.

### Install it (please 🙏)

Sign up (also please) on [electrolytic.app](https://electrolytic.app) and get your `App key` and `Secret`. It's free to get started! ⭐️

Then do the thing, you know, ***the thing***:

```shell
npm install --save electrolytic
```

### Use it in your app!

```javascript
const Electrolytic = require('electrolytic')

const electrolytic = Electrolytic({
  appKey: '<Your-App-Key>',
})

// when app starts
electrolytic.on('token', (token) => {
  // send this token to your server, you'll need it to send a push
  console.log('user token', token);
})

// when you use that <token> to send push via server POST
electrolytic.on('push', (payload) => {
  console.log('got push notification', payload) // hola, here's a push!
})

// when you update the config on our dashboard. It's pushed to all the apps in realtime 🙀
electrolytic.on('config', (updatedConfig) => {
  console.log('look ma, updated config!', updatedConfig)
})
```

### Sending a push (and ❤️) from your server

Simply send a `POST` request to `https://api.electrolytic.app/push/send`

with JSON body having following schema:

```javascript
{
  "appKey": "<You-App-Key>",
  "appSecret": "<Your-App-Secret>",
  "target": ["<token>"], // should be an array. multiple tokens can be used to send the same push to all of them.
  "payload": "hola, here's a push!" // can also be a JSON object
}
```

❤️ is optional... well, I mean its not required.. Don't send it, seriously.

#### For more informations (and emojis), visit [electrolytic.app](https://electrolytic.app)
### License

SOME RIGHTS RESERVED

See [License](https://github.com/electrolytic/electrolytic/blob/master/LICENSE.md)
