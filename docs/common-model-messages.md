# Common Model Messages
<a name="top"></a>

<a name="OpenApiCommonModelMessages"></a>
<p align="right"><a href="#top">Top</a></p>

<a name=".ProtoErrorCode"></a>

### ProtoErrorCode
The error explanations.

| Name | Number | Description |
| ---- | ------ | ----------- |
| UNKNOWN_ERROR | 1 | Generic error. |
| UNSUPPORTED_MESSAGE | 2 | Message is not supported. Wrong message. |
| INVALID_REQUEST | 3 | Generic error. Usually used when input value is not correct. |
| TIMEOUT_ERROR | 5 | Deal execution is reached timeout and rejected. |
| ENTITY_NOT_FOUND | 6 | Generic error for requests by id. |
| CANT_ROUTE_REQUEST | 7 | Connection to Server is lost or not supported. |
| FRAME_TOO_LONG | 8 | Message is too large. |
| MARKET_CLOSED | 9 | Market is closed. |
| CONCURRENT_MODIFICATION | 10 | Order is blocked (e.g. under execution) and change cannot be applied. |
| BLOCKED_PAYLOAD_TYPE | 11 | Message is blocked by server. |



<a name=".ProtoPayloadType"></a>

### ProtoPayloadType
The unique identifier of the request, response, or event command.

| Name | Number | Description |
| ---- | ------ | ----------- |
| PROTO_MESSAGE | 5 | common intensive |
| ERROR_RES | 50 | common commands |
| HEARTBEAT_EVENT | 51 |  |