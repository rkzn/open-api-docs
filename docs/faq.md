# Frequently Asked Questions

In this page you will find frequently asked questions by API users

## Why do I get 429 error response?

The 429 error response means that the user has sent too many requests in a given amount of time. The request limit on our servers are the following:

Historical Data (ProtoOAGetTrendbarsReq, ProtoOAGetTickDataReq, ProtoOADealListReq): 5 requests/second

All other requests: 50 requests/second

Please restrict your implementation within these limits. If your application's traffic unavoidably exceeds these limits, please contact us.

## Why does my application get disconnected frequently?

Applications are disconnected by the server after some time of inactivity. In order to avoid getting disconnected from the server, make sure that you send a heartbeat to the server at least once every 10 seconds.