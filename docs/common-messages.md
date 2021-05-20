# Common Messages
<a name="top"></a>

<a name="OpenApiCommonMessages"></a>
<p align="right"><a href="#top">Top</a></p>

<a name=".ProtoErrorRes"></a>

### ProtoErrorRes



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoPayloadType](/./models/#protooapayloadtype) | optional |  Default: ERROR_RES |
| errorCode | [string](#string) | required | Contains name of ProtoErrorCode or other custom ErrorCodes (e.g. ProtoCHErrorCode) |
| description | [string](#string) | optional | Error description |
| maintenanceEndTimestamp | [uint64](#uint64) | optional | CS-10489 Epoch timestamp in second |






<a name=".ProtoHeartbeatEvent"></a>

### ProtoHeartbeatEvent
Event that is sent from Open API proxy and can be used as criteria that connection is healthy when no other messages are sent by cTrader platform. Open API client can send this message when he needs to keep the connection open for a period without other messages longer than 30 seconds


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoPayloadType](/./models/#protooapayloadtype) | optional |  Default: HEARTBEAT_EVENT |






<a name=".ProtoMessage"></a>

### ProtoMessage



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [uint32](#uint32) | required | Contains id of ProtoPayloadType or other custom PayloadTypes (e.g. ProtoOAPayloadType) |
| payload | [bytes](#bytes) | optional | Serialized protobuf message that corresponds to payloadType |
| clientMsgId | [string](#string) | optional | Request message id, assigned by the client that will be returned in the response |





 

 

 

 



## Scalar Value Types

| .proto Type | Notes | C++ | Java | Python | Go | C# | PHP | Ruby |
| ----------- | ----- | --- | ---- | ------ | -- | -- | --- | ---- |
| <a name="double" /> double |  | double | double | float | float64 | double | float | Float |
| <a name="float" /> float |  | float | float | float | float32 | float | float | Float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum or Fixnum (as required) |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int | uint32 | uint | integer | Bignum or Fixnum (as required) |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long | uint64 | ulong | integer/string | Bignum |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int | int32 | int | integer | Bignum or Fixnum (as required) |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long | int64 | long | integer/string | Bignum |
| <a name="bool" /> bool |  | bool | boolean | boolean | bool | bool | boolean | TrueClass/FalseClass |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode | string | string | string | String (UTF-8) |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str | []byte | ByteString | string | String (ASCII-8BIT) |

