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

Follow the [get started](https://firebase.google.com/docs/functions/get-started) guide to get a basic project working.

Then add some basic functions make sure that a post into slack works properly.

~~Add an ENV key with the [gcloud CLI tool](https://cloud.google.com/sdk/docs).~~

`firebase functions:config:get` then `firebase functions:config:set slack.webhook_url="https://hooks.slack.com/services/cool/hash"`

[functions/config-env](https://firebase.google.com/docs/functions/config-env)

To run the code locally, simply run `firebase emulators:start --only functions` (more details can be found [here](https://firebase.google.com/docs/functions/local-emulator))


[SeLoger API](http://ws.seloger.com/) has moved apparently, so it will be hard to continue furhter... :(
