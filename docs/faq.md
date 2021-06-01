# Frequently Asked Questions

In this page you will find frequently asked questions by API users

## Why do I get 429 error response?

The 429 error response means that the user has sent too many requests in a given amount of time.

API endpoints or subjects to some limitation, you can find them [here](../protocol-buffers/#limitations)

## Why does my application get disconnected frequently?

Applications are disconnected by the server after some time of inactivity. In order to avoid getting disconnected from the server, make sure that you send a heartbeat to the server at least once every 10 seconds.

## Why I can't connect to API during weekends?

Sometimes we do maintenance and upgrades during weekends, and the API will be down during the maintenance time.

## Why do I get invalid route error?

Most probably you are using invalid endpoint, be sure to use the live endpoint for live trading accounts and demo endpoint for demo trading account, for more about endpoints check [here](../protocol-buffers/#endpoints).

## Why do I get errors in messages serialization/deserialization with Google Protocol Buffers?

Please read the [reading/writing](../reading-writing/) tutorial.

## Can I refresh my access token before its expiry?

Yes, you can refresh an access before or after its expiry.

## For how long the refresh token is valid?

Forever, there is no time limit for a refresh token, it will be invalidated if you use it to refresh an access token or if you re-authorize your cTrader ID and trading accounts.

## What's the difference between a trading account's login number and ID?

The login number is used for UI purpose, it has no use case on the API.

You can use a trading account's login number on your application accounts list, for user.

The trading account ID is the one that you will use for sending/receiving API messages.