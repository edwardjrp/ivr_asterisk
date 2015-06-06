# IVR App based on Adhearsion Cool Opensource VoIP Framework

Creates an IVR based on Asterisk and Adhearsion gem, you'll need to configure your VoIP platform as simple as:


```
answer
say 'Hello, and thank you for your call. We will put you through to the front desk now...'
dial 'tel:+18005550199'
hangup
```

The code included is a simple IVR playing game where the Asterisk VoIP will ask you to guess a number which is input from the phone and if you guess the random from 1 to 10 it wil congratulate you for the guessing.

## It can be used with Asterisk, FreeSwitch or Voxeo Prism.


Edit `extensions.conf` to include the following:

```
[your_context_name]
exten => _.,1,AGI(agi:async)
```

and setup a user in `manager.conf` with read/write access to `all`, `dialplan` and `agi`.

## Voxeo PRISM

Install the [rayo-server](https://github.com/rayo/rayo-server) app into PRISM 11 and follow the [configuration guide](https://github.com/rayo/rayo-server/wiki/Single-node-and-cluster-configuration-reference).

## Configure your app

In `config/adhearsion.rb` you'll need to set the VoIP platform you're using, along with the correct credentials. You'll find example config there, so follow the comments.

## Ready, set, go!

Start your new app with "ahn start". You'll get a lovely console and should be presented with the SimonGame when you call in.

### Running your app on heroku

In order to run an adhearsion application on Heroku, you must create the application on the 'cedar' stack (`heroku apps:create --stack cedar`) and re-scale your processes like so:

```
heroku ps:scale web=0
heroku ps:scale ahn=1
```

Check out [the Adhearsion website](http://adhearsion.com) for more details of where to go from here.
More detail is available in the [deployment documentation](http://adhearsion.com/docs/best-practices/deployment).
