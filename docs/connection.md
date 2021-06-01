In this tutorial we will explain how to connect to Open API using a TCP client socket and a SSL stream over socket stream.

cTrader Open API has separate endpoints for live and demo trading accounts.

If your application needs to work with both types of accounts, you need to maintain a separate connection with each endpoint.

You can get the API endpoints from [here](../protocol-buffers/#endpoints).

You can't use a live endpoint connection to interact with demo trading accounts or vice versa, if you try you will receive a routing error from API.

All read/write operations require an SSL stream.

If you are building a trading platform or integrating cTrader on your platform you can follow these guidelines:

 1. Create only two connections, one for the live and on for the demo endpoint.
 2. Use the live connection for live trading accounts and demo connection for demo trading accounts. You can handle many accounts with just one connection, there is no need to create more connections.
 3. After your application connects to the endpoint, you can authorize your API application for each connection by sending a [ProtoOAApplicationAuthReq](../messages/#protooaapplicationauthreq) message.
 4. The API will send you back a [ProtoOAApplicationAuthRes](../messages/#protooaapplicationauthres) message. This means that your API application is authorized and you are ready to go.
 5. Your application needs to be authorized before you send any other message to the API end point. If you send any message before authorizing your application, you will receive an error.
 6. To keep your connections alive, keep sending a [ProtoHeartbeatEvent](../common-messages/#protoheartbeatevent) in 10 seconds interval.
 7. Use a message queue for reading/writing to connection streams for avoiding concurrent read/write, or any other solution that is available for you based on your environment.
 8. Please check the endpoints [limitations](../protocol-buffers/#limitations) to avoid connection issues.