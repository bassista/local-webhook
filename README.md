# local-webhook

Zero-configuration localhost webhooks. Do not use in production.

<p>  
  <img src="https://i.imgur.com/ySm2Noc.png" alt="banner" draggable="false">
</p>

## Installation

```bash
# npm
npm install --save-dev local-webhook express ngrok
```

Note: `express` and `ngrok` are required peer dependencies.

## Usage

Setup and generate webhook as a Promise:
```js
import LocalWebhook from 'local-webhook';

await LocalWebhook.startServer(); // optional: { region: "eu" }

const webhook = LocalWebhook.getPromise();

// This URL can be shared with third-party services.
webhook.getWebhookUrl(); 

// Handle third-party service's webhook request once.
webhook.then(({ req, res }) => {
    res.send("Hello from promise");
});

// Awaitable if necessary.
await webhook;
```

Generate webhook as an Observable:
```js
const webhook = LocalWebhook.getObservable();

// This URL can be shared with third-party services.
webhook.getWebhookUrl(); 

// Handle third-party service's webhook requests each time.
webhook.subscribe(({ req, res }) => {
  res.send("Hello from observable");
});
```

To inspect and replay requests, open ngrok's web interface at [localhost:4040](http://localhost:4040).

## Peer dependencies

- [expressjs/express](https://github.com/expressjs/express) - http server
- [bubenshchykov/ngrok](https://github.com/bubenshchykov/ngrok) - a [ngrok](https://ngrok.com/) wrapper

## Community

Let's start one together! After you ★ this project, follow me [@rygu](https://twitter.com/rygu) on Twitter.

## Thanks

- [Vernon de Goede](https://github.com/vernondegoede)
- [Giel Cobben](https://github.com/gielcobben)
- [René Feiner](https://github.com/rfeiner)
- [Mathieu Kooiman](https://github.com/mathieuk)

## License

BSD 3-Clause license. Copyright © 2018, Rick Wong. All rights reserved.
