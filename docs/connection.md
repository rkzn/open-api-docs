For connection we will use a TCP client socket and a SSL stream over socket stream.

The API has separate endpoints for live and demo trading accounts, if you want to work on your program with both types of accounts you must have a connection with each endpoint.

You can get the API endpoints from [here](../protocol-buffers/#endpoints).

You can't use a live endpoint connection to interact with demo trading accounts or vice versa, if you try you will receive a routing error from API.

You must use the SSL stream for all your read/write operations, not the actual client stream.

If you are building a trading platfrom or integrating cTrader on your platform you can follow these guide lines:

 1. Create only two connections for live and demo endpoints
 2. Use the live connection for live trading accounts and demo connection for demo trading accounts, you can handle large number of accounts with just one connection, there is no need to create more connections
 3. After you got connected, authorize your API application for each connection by sending a [ProtoOAApplicationAuthReq](../messages/#protooaapplicationauthreq) message
 4. The API will send you back a [ProtoOAApplicationAuthRes](../messages/#protooaapplicationauthres) message, it means your API application is authorized and you are ready to go
 5. Don't try to send any message before authorzing your application, otherwise you will receive an error
 6. To keepalive your connections keep sending a [ProtoHeartbeatEvent](../common-messages/#protoheartbeatevent) in 10 seconds interval
 7. Use a message queue for reading/writing to connection streams for avoiding concurrent read/write, or anyother solution that is available for you based on your environment
 8. Please check the endpoints [limitations](../protocol-buffers/#limitations) to avoid connection issues