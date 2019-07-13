### Firebase plan

The first thing is to get a [Blaze Plan](https://firebase.google.com/pricing) for being able to
send data to outbound networking.

Indeed, the free `Spark Plan` cannot allow you to do so. But the good thing is that the `Blaze Plan` is paid only you go further than the free `Spark Plan` !
(insert gif on where to change that kind of stuff)

### Create a personnal slack

Create a simple free workspace and create a channel in it.

Then add an app to it (`Administration > Manage Apps`), on the page opened, go to `Custom Integration` and then add an `Incoming WebHook`.

Try it w/ something like Insomnia, send a POST request to your webhook and you should see it appearing right in your defined channel.

### Firebase

Follow the [get started](https://firebase.google.com/docs/functions/get-started) guide to get a basic project working, the most important part is `firebase deploy --only functions` to send the function to the cloud.

If you're properly using the Blaze plan, you should have access to your functions on the Google Console and see your apps there.
[Google Cloud Platform apps](https://console.cloud.google.com/functions/list)

Then add some basic functions make sure that a post into slack works properly.

~~Add an ENV key with the [gcloud CLI tool](https://cloud.google.com/sdk/docs).~~

`firebase functions:config:get` then `firebase functions:config:set slack.webhook_url="https://hooks.slack.com/services/cool/hash"`

[Nice documentation](https://api.slack.com/docs/message-attachments) on how to send a fancy slack message

[functions/config-env](https://firebase.google.com/docs/functions/config-env)

Btw, it seems that Firebase env vars are not the same as the Google Cloud platform ones.

If you do have a var sent with `firebase functions:config:set app.dev_tools=false`, it will not appear on the Google Cloud Functions dashboard, but will be available on Firebase (`firebase functions:config:get`).
Another annoying thing

To run the code locally, simply run `firebase emulators:start --only functions` (more details can be found [here](https://firebase.google.com/docs/functions/local-emulator))

[SeLoger API](http://ws.seloger.com/) has moved apparently, so it will be hard to continue furhter... :(


## How to refresh Pole Emploi with Puppeteer

So, to run some variables locally, you can create a `.runtimeconfig.json` in your folder app in `/functions` directory, create something like
```js
{
  "app": {
    "url": "https://www.google.com"
  }
}
```
and then call it inside the code with

```js
const functions = require('firebase-functions')
const local_vars = functions.config()
const myCoolWebsite = local_vars.app.url
```
NB: you can of course interpolate it as usual.

Maybe try to find out how to [debug](https://medium.com/@mwebler/debugging-firebase-functions-with-vs-code-3afab528bb36) properly Firebase into VScode.

To set your entire `functions/.env-production.json` env variables, use this command line `firebase functions:config:set app="$(cat .env-production.json)"` and check if it's ok with `firebase functions:config:get`.

If you failed somehow, you can still unset it with `firebase functions:config:unset app.firebase_chromium_exe_path` for example.

DO NOT forget to reset the env variables if you were sick or were in a training because it will not do it by itself !

To add a Slack webhook, click on your workspace name, then `Administration` > `Manage apps`. In the opened browser window, go to `Apps` marketpage and type `Incoming WebHooks`. Add the configuration by binding it to one of your existing channels.
And you should get your Slack WebHook !
