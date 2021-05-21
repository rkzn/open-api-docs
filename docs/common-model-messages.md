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

