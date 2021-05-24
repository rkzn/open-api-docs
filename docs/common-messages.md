# Common Messages
<a name="top"></a>

<a name="OpenApiCommonMessages"></a>
<p align="right"><a href="#top">Top</a></p>

<a name=".ProtoErrorRes"></a>

### ProtoErrorRes



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoPayloadType](../models/#protooapayloadtype) | optional |  Default: ERROR_RES |
| errorCode | [string](#string) | required | Contains name of ProtoErrorCode or other custom ErrorCodes (e.g. ProtoCHErrorCode) |
| description | [string](#string) | optional | Error description |
| maintenanceEndTimestamp | [uint64](#uint64) | optional | CS-10489 Epoch timestamp in second |






<a name=".ProtoHeartbeatEvent"></a>

### ProtoHeartbeatEvent
Event that is sent from Open API proxy and can be used as criteria that connection is healthy when no other messages are sent by cTrader platform. Open API client can send this message when he needs to keep the connection open for a period without other messages longer than 30 seconds


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoPayloadType](../models/#protooapayloadtype) | optional |  Default: HEARTBEAT_EVENT |






<a name=".ProtoMessage"></a>

### ProtoMessage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [uint32](#uint32) | required | Contains id of ProtoPayloadType or other custom PayloadTypes (e.g. ProtoOAPayloadType) |
| payload | [bytes](#bytes) | optional | Serialized protobuf message that corresponds to payloadType |
| clientMsgId | [string](#string) | optional | Request message id, assigned by the client that will be returned in the response |

