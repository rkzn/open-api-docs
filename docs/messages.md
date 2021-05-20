# Messages
<a name="top"></a>

<a name="OpenApiMessages"></a>
<p align="right"><a href="#top">Top</a></p>

<a name=".ProtoOAAccountAuthReq"></a>

### ProtoOAAccountAuthReq
Request for the authorizing trading account session. Requires established authorized connection with the client application using ProtoOAApplicationAuthReq.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ACCOUNT_AUTH_REQ |
| ctidTraderAccountId | [int64](#int64) | required | The unique identifier of the trader&#39;s account in cTrader platform. |
| accessToken | [string](#string) | required | The Access Token issued for providing access to the Trader&#39;s Account. |






<a name=".ProtoOAAccountAuthRes"></a>

### ProtoOAAccountAuthRes
Response to the ProtoOAApplicationAuthRes request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ACCOUNT_AUTH_RES |
| ctidTraderAccountId | [int64](#int64) | required | The unique identifier of the trader&#39;s account in cTrader platform. |






<a name=".ProtoOAAccountDisconnectEvent"></a>

### ProtoOAAccountDisconnectEvent
Event that is sent when the established session for an account is dropped on the server side.
A new session must be authorized for the account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ACCOUNT_DISCONNECT_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | The unique identifier of the trader&#39;s account in cTrader platform. |






<a name=".ProtoOAAccountLogoutReq"></a>

### ProtoOAAccountLogoutReq
Request for logout of  trading account session.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ACCOUNT_LOGOUT_REQ |
| ctidTraderAccountId | [int64](#int64) | required | The unique identifier of the trader&#39;s account in cTrader platform. |






<a name=".ProtoOAAccountLogoutRes"></a>

### ProtoOAAccountLogoutRes
Response to the ProtoOATraderLogoutReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ACCOUNT_LOGOUT_RES |
| ctidTraderAccountId | [int64](#int64) | required | The unique identifier of the trader&#39;s account in cTrader platform. |






<a name=".ProtoOAAccountsTokenInvalidatedEvent"></a>

### ProtoOAAccountsTokenInvalidatedEvent
Event that is sent when a session to a specific trader&#39;s account is terminated by the server but the existing connections with the other trader&#39;s accounts are maintained.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ACCOUNTS_TOKEN_INVALIDATED_EVENT |
| ctidTraderAccountIds | [int64](#int64) | repeated | The unique identifier of the trader&#39;s account in cTrader platform. |
| reason | [string](#string) | optional | The disconnection reason explained. For example: Access Token is expired or recalled. |






<a name=".ProtoOAAmendOrderReq"></a>

### ProtoOAAmendOrderReq
Request for amending the existing pending order. Allowed only if the Access Token has &#34;trade&#34; permissions for the trading account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_AMEND_ORDER_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| orderId | [int64](#int64) | required | The unique ID of the order. |
| volume | [int64](#int64) | optional | Volume, represented in 0.01 of a unit (e.g. cents). |
| limitPrice | [double](#double) | optional | The Limit Price, can be specified for the LIMIT order only. |
| stopPrice | [double](#double) | optional | The Stop Price, can be specified for the STOP and the STOP_LIMIT orders. |
| expirationTimestamp | [int64](#int64) | optional | The exact Order expiration time. Should be set for the Good Till Date orders. |
| stopLoss | [double](#double) | optional | The absolute Stop Loss price (e.g. 1.23456). Not supported for the MARKER orders. |
| takeProfit | [double](#double) | optional | The absolute Take Profit price (e.g. 1.23456). Not supported for the MARKER orders. |
| slippageInPoints | [int32](#int32) | optional | Slippage distance for the MARKET_RANGE and the STOP_LIMIT orders. |
| relativeStopLoss | [int64](#int64) | optional | The relative Stop Loss can be specified instead of the absolute one. Specified in 1/100000 of a unit of price. For BUY stopLoss = entryPrice - relativeStopLoss, for SELL stopLoss = entryPrice &#43; relativeStopLoss. |
| relativeTakeProfit | [int64](#int64) | optional | The relative Take Profit can be specified instead of the absolute one. Specified in 1/100000 of a unit of price. For BUY takeProfit = entryPrice &#43; relativeTakeProfit, for SELL takeProfit = entryPrice - relativeTakeProfit. |
| guaranteedStopLoss | [bool](#bool) | optional | If TRUE then the Stop Loss is guaranteed. Available for the French Risk or the Guaranteed Stop Loss Accounts. |
| trailingStopLoss | [bool](#bool) | optional | If TRUE then the Trailing Stop Loss is applied. |
| stopTriggerMethod | [ProtoOAOrderTriggerMethod](/./models/#protooaordertriggermethod) | optional | Trigger method for the STOP or the STOP_LIMIT pending order. Default: TRADE |






<a name=".ProtoOAAmendPositionSLTPReq"></a>

### ProtoOAAmendPositionSLTPReq
Request for amending StopLoss and TakeProfit of existing position. Allowed only if the accessToken has &#34;trade&#34; permissions for the trading account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_AMEND_POSITION_SLTP_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| positionId | [int64](#int64) | required | The unique ID of the position to amend. |
| stopLoss | [double](#double) | optional | Absolute Stop Loss price (1.23456 for example). |
| takeProfit | [double](#double) | optional | Absolute Take Profit price (1.26543 for example). |
| guaranteedStopLoss | [bool](#bool) | optional | If TRUE then the Stop Loss is guaranteed. Available for the French Risk or the Guaranteed Stop Loss Accounts. |
| trailingStopLoss | [bool](#bool) | optional | If TRUE then the Trailing Stop Loss is applied. |
| stopLossTriggerMethod | [ProtoOAOrderTriggerMethod](/./models/#protooaordertriggermethod) | optional | The Stop trigger method for the Stop Loss/Take Profit order. Default: TRADE |






<a name=".ProtoOAApplicationAuthReq"></a>

### ProtoOAApplicationAuthReq
Request for the authorizing an application to work with the cTrader platform Proxies.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_APPLICATION_AUTH_REQ |
| clientId | [string](#string) | required | The unique Client ID provided during the registration. |
| clientSecret | [string](#string) | required | The unique Client Secret provided during the registration. |






<a name=".ProtoOAApplicationAuthRes"></a>

### ProtoOAApplicationAuthRes
Response to the ProtoOAApplicationAuthReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_APPLICATION_AUTH_RES |






<a name=".ProtoOAAssetClassListReq"></a>

### ProtoOAAssetClassListReq
Request for a list of asset classes available for the trader&#39;s account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ASSET_CLASS_LIST_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOAAssetClassListRes"></a>

### ProtoOAAssetClassListRes
Response to the ProtoOAAssetListReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ASSET_CLASS_LIST_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| assetClass | [ProtoOAAssetClass](/./models/#protooaassetclass) | repeated | List of the asset classes. |






<a name=".ProtoOAAssetListReq"></a>

### ProtoOAAssetListReq
Request for the list of assets available for a trader&#39;s account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ASSET_LIST_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOAAssetListRes"></a>

### ProtoOAAssetListRes
Response to the ProtoOAAssetListReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ASSET_LIST_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| asset | [ProtoOAAsset](/./models/#protooaasset) | repeated | The list of assets. |






<a name=".ProtoOACancelOrderReq"></a>

### ProtoOACancelOrderReq
Request for cancelling existing pending order. Allowed only if the accessToken has &#34;trade&#34; permissions for the trading account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_CANCEL_ORDER_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| orderId | [int64](#int64) | required | The unique ID of the order. |






<a name=".ProtoOACashFlowHistoryListReq"></a>

### ProtoOACashFlowHistoryListReq
Request for getting Trader&#39;s historical data of deposits and withdrawals.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_CASH_FLOW_HISTORY_LIST_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| fromTimestamp | [int64](#int64) | required | The UNIX time from which the search starts &gt;=0 (1-1-1970). Validation: toTimestamp - fromTimestamp &lt;= 604800000 (1 week). |
| toTimestamp | [int64](#int64) | required | The UNIX time where to stop searching &lt;= 2147483646000 (19-1-2038). |






<a name=".ProtoOACashFlowHistoryListRes"></a>

### ProtoOACashFlowHistoryListRes
Response to the ProtoOACashFlowHistoryListReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_CASH_FLOW_HISTORY_LIST_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| depositWithdraw | [ProtoOADepositWithdraw](/./models/#protooadepositwithdraw) | repeated | The list of deposit and withdrawal operations. |






<a name=".ProtoOAClientDisconnectEvent"></a>

### ProtoOAClientDisconnectEvent
Event that is sent when the connection with the client application is cancelled by the server. All the sessions for the traders&#39; accounts will be terminated.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_CLIENT_DISCONNECT_EVENT |
| reason | [string](#string) | optional | The disconnection reason explained. For example: The application access was blocked by cTrader Administrator. |






<a name=".ProtoOAClosePositionReq"></a>

### ProtoOAClosePositionReq
Request for closing or partially closing of an existing position. Allowed only if the accessToken has &#34;trade&#34; permissions for the trading account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_CLOSE_POSITION_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| positionId | [int64](#int64) | required | The unique ID of the position to close. |
| volume | [int64](#int64) | required | Volume to close, represented in 0.01 of a unit (e.g. cents). |






<a name=".ProtoOADealListReq"></a>

### ProtoOADealListReq
Request for getting Trader&#39;s deals historical data (execution details).


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_DEAL_LIST_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| fromTimestamp | [int64](#int64) | required | The UNIX time from which the search starts &gt;=0 (1-1-1970). Validation: toTimestamp - fromTimestamp &lt;= 604800000 (1 week). |
| toTimestamp | [int64](#int64) | required | The UNIX time where to stop searching &lt;= 2147483646000 (19-1-2038). |
| maxRows | [int32](#int32) | optional | The maximum number of the deals to return. |






<a name=".ProtoOADealListRes"></a>

### ProtoOADealListRes
The response to the ProtoOADealListRes request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_DEAL_LIST_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| deal | [ProtoOADeal](/./models/#protooadeal) | repeated | The list of the deals. |
| hasMore | [bool](#bool) | required | If TRUE then the response will provide more than 10000 deals. |






<a name=".ProtoOADepthEvent"></a>

### ProtoOADepthEvent
Event that is sent when the structure of depth of market is changed. Requires subscription on the depth of markets for the symbol, see ProtoOASubscribeDepthQuotesReq.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_DEPTH_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [uint64](#uint64) | required | Unique identifier of the Symbol in cTrader platform. |
| newQuotes | [ProtoOADepthQuote](/./models/#protooadepthquote) | repeated | The list of changes in the depth of market quotes. |
| deletedQuotes | [uint64](#uint64) | repeated | The list of quotes to delete. |






<a name=".ProtoOAErrorRes"></a>

### ProtoOAErrorRes
Generic response when an ERROR occurred.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ERROR_RES |
| ctidTraderAccountId | [int64](#int64) | optional | The unique identifier of the trader&#39;s account in cTrader platform. |
| errorCode | [string](#string) | required | The name of the ProtoErrorCode or the other custom ErrorCodes (e.g. ProtoCHErrorCode). |
| description | [string](#string) | optional | The error description. |
| maintenanceEndTimestamp | [int64](#int64) | optional | The timestamp in seconds when the current maintenance session will be ended. |






<a name=".ProtoOAExecutionEvent"></a>

### ProtoOAExecutionEvent
Event that is sent following the successful order acceptance or execution by the server. Acts as response to the ProtoOANewOrderReq, ProtoOACancelOrderReq, ProtoOAAmendOrderReq, ProtoOAAmendPositionSLTPReq, ProtoOAClosePositionReq requests. Also, the event is sent when a Deposit/Withdrawal took place.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_EXECUTION_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| executionType | [ProtoOAExecutionType](/./models/#protooaexecutiontype) | required | Type of the order operation. For example: ACCEPTED, FILLED, etc. |
| position | [ProtoOAPosition](/./models/#protooaposition) | optional | Reference to the position linked with the execution |
| order | [ProtoOAOrder](/./models/#protooaorder) | optional | Reference to the initial order. |
| deal | [ProtoOADeal](/./models/#protooadeal) | optional | Reference to the deal (execution). |
| bonusDepositWithdraw | [ProtoOABonusDepositWithdraw](/./models/#protooabonusdepositwithdraw) | optional | Reference to the Bonus Deposit or Withdrawal operation. |
| depositWithdraw | [ProtoOADepositWithdraw](/./models/#protooadepositwithdraw) | optional | Reference to the Deposit or Withdrawal operation. |
| errorCode | [string](#string) | optional | The name of the ProtoErrorCode or the other custom ErrorCodes (e.g. ProtoCHErrorCode). |
| isServerEvent | [bool](#bool) | optional | If TRUE then the event generated by the server logic instead of the trader&#39;s request. (e.g. stop-out). |






<a name=".ProtoOAExpectedMarginReq"></a>

### ProtoOAExpectedMarginReq
Request for getting the margin estimate. Can be used before sending a new order request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_EXPECTED_MARGIN_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | required | Unique identifier of the Symbol in cTrader platform. |
| volume | [int64](#int64) | repeated | Volume represented in 0.01 of a unit (e.g. cents). |






<a name=".ProtoOAExpectedMarginRes"></a>

### ProtoOAExpectedMarginRes
The response to the ProtoOAExpectedMarginReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_EXPECTED_MARGIN_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| margin | [ProtoOAExpectedMargin](/./models/#protooaexpectedmargin) | repeated | The buy and sell margin estimate. |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects margin.buyMargin, margin.sellMargin. |






<a name=".ProtoOAGetAccountListByAccessTokenReq"></a>

### ProtoOAGetAccountListByAccessTokenReq
Request for getting the list of granted trader&#39;s account for the access token.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_ACCOUNTS_BY_ACCESS_TOKEN_REQ |
| accessToken | [string](#string) | required | The Access Token issued for providing access to the Trader&#39;s Account. |






<a name=".ProtoOAGetAccountListByAccessTokenRes"></a>

### ProtoOAGetAccountListByAccessTokenRes
Response to the ProtoOAGetAccountListByAccessTokenReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_ACCOUNTS_BY_ACCESS_TOKEN_RES |
| accessToken | [string](#string) | required | The Access Token issued for providing access to the Trader&#39;s Account. |
| permissionScope | [ProtoOAClientPermissionScope](/./models/#protooaclientpermissionscope) | optional | SCOPE_VIEW, SCOPE_TRADE. |
| ctidTraderAccount | [ProtoOACtidTraderAccount](/./models/#protooactidtraderaccount) | repeated | The list of the accounts. |






<a name=".ProtoOAGetCtidProfileByTokenReq"></a>

### ProtoOAGetCtidProfileByTokenReq
Request for getting details of Trader&#39;s profile. Limited due to GDRP requirements.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_CTID_PROFILE_BY_TOKEN_REQ |
| accessToken | [string](#string) | required | The Access Token issued for providing access to the Trader&#39;s Account. |






<a name=".ProtoOAGetCtidProfileByTokenRes"></a>

### ProtoOAGetCtidProfileByTokenRes
Response to the ProtoOAGetCtidProfileByTokenReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_CTID_PROFILE_BY_TOKEN_RES |
| profile | [ProtoOACtidProfile](/./models/#protooactidprofile) | required | Trader&#39;s profile. |






<a name=".ProtoOAGetTickDataReq"></a>

### ProtoOAGetTickDataReq
Request for getting historical tick data for the symbol.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_TICKDATA_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | required | Unique identifier of the Symbol in cTrader platform. |
| type | [ProtoOAQuoteType](/./models/#protooaquotetype) | required | Bid/Ask (1/2). |
| fromTimestamp | [int64](#int64) | required | The exact time of starting the search in milliseconds. Must be bigger of equal to zero (1-1-1970). Validation: toTimestamp - fromTimestamp &lt;= 604800000 (1 week). |
| toTimestamp | [int64](#int64) | required | The exact time of finishing the search in milliseconds &lt;= 2147483646000 (19-1-2038). |






<a name=".ProtoOAGetTickDataRes"></a>

### ProtoOAGetTickDataRes
Response to the ProtoOAGetTickDataReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_TICKDATA_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| tickData | [ProtoOATickData](/./models/#protooatickdata) | repeated | The list of ticks. |
| hasMore | [bool](#bool) | required | If TRUE then the number of records by filter is larger than chunkSize, the response contains the number of records that is equal to chunkSize. |






<a name=".ProtoOAGetTrendbarsReq"></a>

### ProtoOAGetTrendbarsReq
Request for getting historical trend bars for the symbol.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_TRENDBARS_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| fromTimestamp | [int64](#int64) | required | The exact time of starting the search in milliseconds. Must be bigger or equal to zero (1-1-1970). Validation: toTimestamp - fromTimestamp &lt;= X, where X depends on series period: M1, M2, M3, M4, M5: 302400000 (5 weeks); M10, M15, M30, H1: 21168000000 (35 weeks), H4, H12, D1: 31622400000 (1 year); W1, MN1: 158112000000 (5 years). |
| toTimestamp | [int64](#int64) | required | The exact time of finishing the search in milliseconds. Smaller or equal to 2147483646000 (19-1-2038). |
| period | [ProtoOATrendbarPeriod](/./models/#protooatrendbarperiod) | required | Specifies period of trend bar series (e.g. M1, M10, etc.). |
| symbolId | [int64](#int64) | required | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOAGetTrendbarsRes"></a>

### ProtoOAGetTrendbarsRes
Response to the ProtoOAGetTrendbarsReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_GET_TRENDBARS_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| period | [ProtoOATrendbarPeriod](/./models/#protooatrendbarperiod) | required | Specifies period of trend bar series (e.g. M1, M10, etc.). |
| timestamp | [int64](#int64) | required | Equals to toTimestamp from the request. |
| trendbar | [ProtoOATrendbar](/./models/#protooatrendbar) | repeated | The list of trend bars. |
| symbolId | [int64](#int64) | optional | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOAMarginCallListReq"></a>

### ProtoOAMarginCallListReq
Request for a list of existing margin call thresholds configured for a user.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CALL_LIST_REQ |
| ctidTraderAccountId | [int64](#int64) | required |  |






<a name=".ProtoOAMarginCallListRes"></a>

### ProtoOAMarginCallListRes
Response with a list of existing user Margin Calls, usually contains 3 items.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CALL_LIST_RES |
| marginCall | [ProtoOAMarginCall](/./models/#protooamargincall) | repeated |  |






<a name=".ProtoOAMarginCallTriggerEvent"></a>

### ProtoOAMarginCallTriggerEvent
Event that is sent when account margin level reaches target marginLevelThreshold. Event is sent no more than once every 10 minutes to avoid spamming.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CALL_TRIGGER_EVENT |
| ctidTraderAccountId | [int64](#int64) | required |  |
| marginCall | [ProtoOAMarginCall](/./models/#protooamargincall) | required |  |






<a name=".ProtoOAMarginCallUpdateEvent"></a>

### ProtoOAMarginCallUpdateEvent
Event that is sent when a Margin Call threshold configuration is updated.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CALL_UPDATE_EVENT |
| ctidTraderAccountId | [int64](#int64) | required |  |
| marginCall | [ProtoOAMarginCall](/./models/#protooamargincall) | required |  |






<a name=".ProtoOAMarginCallUpdateReq"></a>

### ProtoOAMarginCallUpdateReq
Request to modify marginLevelThreshold of specified marginCallType for ctidTraderAccountId.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CALL_UPDATE_REQ |
| ctidTraderAccountId | [int64](#int64) | required |  |
| marginCall | [ProtoOAMarginCall](/./models/#protooamargincall) | required |  |






<a name=".ProtoOAMarginCallUpdateRes"></a>

### ProtoOAMarginCallUpdateRes
If this response received, it means that margin call was successfully updated.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CALL_UPDATE_RES |






<a name=".ProtoOAMarginChangedEvent"></a>

### ProtoOAMarginChangedEvent
Event that is sent when the margin allocated to a specific position is changed.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_MARGIN_CHANGED_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| positionId | [uint64](#uint64) | required | The unique ID of the position. |
| usedMargin | [uint64](#uint64) | required | The new value of the margin used. |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects usedMargin. |






<a name=".ProtoOANewOrderReq"></a>

### ProtoOANewOrderReq
Request for sending a new trading order. Allowed only if the accessToken has the &#34;trade&#34; permissions for the trading account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_NEW_ORDER_REQ |
| ctidTraderAccountId | [int64](#int64) | required | The unique identifier of the trader&#39;s account in cTrader platform. |
| symbolId | [int64](#int64) | required | The unique identifier of a symbol in cTrader platform. |
| orderType | [ProtoOAOrderType](/./models/#protooaordertype) | required | The type of an order - MARKET, LIMIT, STOP, MARKET_RANGE, STOP_LIMIT. |
| tradeSide | [ProtoOATradeSide](/./models/#protooatradeside) | required | The trade direction - BUY or SELL. |
| volume | [int64](#int64) | required | The volume represented in 0.01 of a unit (e.g. US$ 10.00 = 1000). |
| limitPrice | [double](#double) | optional | The limit price, can be specified for the LIMIT order only. |
| stopPrice | [double](#double) | optional | Stop Price, can be specified for the STOP and the STOP_LIMIT orders only. |
| timeInForce | [ProtoOATimeInForce](/./models/#protooatimeinforce) | optional | The specific order execution or expiration instruction - GOOD_TILL_DATE, GOOD_TILL_CANCEL, IMMEDIATE_OR_CANCEL, FILL_OR_KILL, MARKET_ON_OPEN. Default: GOOD_TILL_CANCEL |
| expirationTimestamp | [int64](#int64) | optional | The exact Order expiration time. Should be set for the Good Till Date orders. |
| stopLoss | [double](#double) | optional | The absolute Stop Loss price (1.23456 for example). Not supported for the MARKER orders. |
| takeProfit | [double](#double) | optional | The absolute Take Profit price (1.23456 for example). Unsupported for the MARKER orders. |
| comment | [string](#string) | optional | User-specified comment. MaxLength = 512. |
| baseSlippagePrice | [double](#double) | optional | Base price to calculate relative slippage price for MARKET_RANGE order. |
| slippageInPoints | [int32](#int32) | optional | Slippage distance for MARKET_RANGE and STOP_LIMIT order. |
| label | [string](#string) | optional | User-specified label. MaxLength = 100. |
| positionId | [int64](#int64) | optional | Reference to the existing position if the Order is intended to modify it. |
| clientOrderId | [string](#string) | optional | Optional user-specific clientOrderId (similar to FIX ClOrderID). MaxLength = 50. |
| relativeStopLoss | [int64](#int64) | optional | Relative Stop Loss that can be specified instead of the absolute as one. Specified in 1/100000 of unit of a price. For BUY stopLoss = entryPrice - relativeStopLoss, for SELL stopLoss = entryPrice &#43; relativeStopLoss. |
| relativeTakeProfit | [int64](#int64) | optional | Relative Take Profit that can be specified instead of the absolute one. Specified in 1/100000 of unit of a price. For BUY takeProfit = entryPrice &#43; relativeTakeProfit, for SELL takeProfit = entryPrice - relativeTakeProfit. |
| guaranteedStopLoss | [bool](#bool) | optional | If TRUE then stopLoss is guaranteed. Available for the French Risk or the Guaranteed Stop Loss Accounts. |
| trailingStopLoss | [bool](#bool) | optional | If TRUE then the Stop Loss is Trailing. |
| stopTriggerMethod | [ProtoOAOrderTriggerMethod](/./models/#protooaordertriggermethod) | optional | Trigger method for the STOP or the STOP_LIMIT pending order. Default: TRADE |






<a name=".ProtoOAOrderErrorEvent"></a>

### ProtoOAOrderErrorEvent
Event that is sent when errors occur during the order requests.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_ORDER_ERROR_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| errorCode | [string](#string) | required | The name of the ProtoErrorCode or the other custom ErrorCodes (e.g. ProtoCHErrorCode). |
| orderId | [int64](#int64) | optional | The unique ID of the order. |
| positionId | [int64](#int64) | optional | The unique ID of the position. |
| description | [string](#string) | optional | The error description. |






<a name=".ProtoOAReconcileReq"></a>

### ProtoOAReconcileReq
Request for getting Trader&#39;s current open positions and pending orders data.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_RECONCILE_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOAReconcileRes"></a>

### ProtoOAReconcileRes
The response to the ProtoOAReconcileReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_RECONCILE_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| position | [ProtoOAPosition](/./models/#protooaposition) | repeated | The list of trader&#39;s account open positions. |
| order | [ProtoOAOrder](/./models/#protooaorder) | repeated | The list of trader&#39;s account pending orders. |






<a name=".ProtoOARefreshTokenReq"></a>

### ProtoOARefreshTokenReq
Request to refresh the access token using refresh token of granted trader&#39;s account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_REFRESH_TOKEN_REQ |
| refreshToken | [string](#string) | required | The Refresh Token issued for updating Access Token. |






<a name=".ProtoOARefreshTokenRes"></a>

### ProtoOARefreshTokenRes
Response to the ProtoOARefreshTokenReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_REFRESH_TOKEN_RES |
| accessToken | [string](#string) | required | The Access Token issued for providing access to the Trader&#39;s Account. |
| tokenType | [string](#string) | required | bearer |
| expiresIn | [int64](#int64) | required | Access Token expiration in seconds |
| refreshToken | [string](#string) | required |  |






<a name=".ProtoOASpotEvent"></a>

### ProtoOASpotEvent
Event that is sent when a new spot event is generated on the server side. Requires subscription on the spot events, see ProtoOASubscribeSpotsReq.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SPOT_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | required | Unique identifier of the Symbol in cTrader platform. |
| bid | [uint64](#uint64) | optional | Bid price. Specified in 1/100_000 of unit of a price. (e.g. 1.23 -&gt; 123_000) |
| ask | [uint64](#uint64) | optional | Ask price. Specified in 1/100_000 of unit of a price. |
| trendbar | [ProtoOATrendbar](/./models/#protooatrendbar) | repeated | Returns live trend bar. Requires subscription on the trend bars. |
| sessionClose | [uint64](#uint64) | optional | Last session close. Specified in 1/100_000 of unit of a price. |






<a name=".ProtoOASubscribeDepthQuotesReq"></a>

### ProtoOASubscribeDepthQuotesReq
Request for subscribing on depth of market of the specified symbol.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SUBSCRIBE_DEPTH_QUOTES_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | repeated | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOASubscribeDepthQuotesRes"></a>

### ProtoOASubscribeDepthQuotesRes
Response to the ProtoOASubscribeDepthQuotesReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SUBSCRIBE_DEPTH_QUOTES_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOASubscribeLiveTrendbarReq"></a>

### ProtoOASubscribeLiveTrendbarReq
Request for subscribing for live trend bars. Requires subscription on the spot events, see ProtoOASubscribeSpotsReq.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SUBSCRIBE_LIVE_TRENDBAR_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| period | [ProtoOATrendbarPeriod](/./models/#protooatrendbarperiod) | required | Specifies period of trend bar series (e.g. M1, M10, etc.). |
| symbolId | [int64](#int64) | required | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOASubscribeLiveTrendbarRes"></a>

### ProtoOASubscribeLiveTrendbarRes
Response to the ProtoOASubscribeLiveTrendbarReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SUBSCRIBE_LIVE_TRENDBAR_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOASubscribeSpotsReq"></a>

### ProtoOASubscribeSpotsReq
Request for subscribing on spot events of the specified symbol.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SUBSCRIBE_SPOTS_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | repeated | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOASubscribeSpotsRes"></a>

### ProtoOASubscribeSpotsRes
Response to the ProtoOASubscribeSpotsReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SUBSCRIBE_SPOTS_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOASymbolByIdReq"></a>

### ProtoOASymbolByIdReq
Request for getting a full symbol entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOL_BY_ID_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | repeated | Unique identifier of the symbol in cTrader platform. |






<a name=".ProtoOASymbolByIdRes"></a>

### ProtoOASymbolByIdRes
Response to the ProtoOASymbolByIdReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOL_BY_ID_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbol | [ProtoOASymbol](/./models/#protooasymbol) | repeated | Symbol entity with the full set of fields. |
| archivedSymbol | [ProtoOAArchivedSymbol](/./models/#protooaarchivedsymbol) | repeated | Archived symbols. |






<a name=".ProtoOASymbolCategoryListReq"></a>

### ProtoOASymbolCategoryListReq
Request for a list of symbol categories available for a trading account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOL_CATEGORY_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOASymbolCategoryListRes"></a>

### ProtoOASymbolCategoryListRes
Response to the ProtoSymbolCategoryListReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOL_CATEGORY_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolCategory | [ProtoOASymbolCategory](/./models/#protooasymbolcategory) | repeated | The list of symbol categories. |






<a name=".ProtoOASymbolChangedEvent"></a>

### ProtoOASymbolChangedEvent
Event that is sent when the symbol is changed on the Server side.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOL_CHANGED_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | repeated | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOASymbolsForConversionReq"></a>

### ProtoOASymbolsForConversionReq
Request for getting a conversion chain between two assets that consists of several symbols. Use when no direct quote is available


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOLS_FOR_CONVERSION_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| firstAssetId | [int64](#int64) | required | The ID of the firs asset in the conversation chain. e.g.: for EUR/USD the firstAssetId is EUR ID and lastAssetId is USD ID. |
| lastAssetId | [int64](#int64) | required | The ID of the last asset in the conversation chain. e.g.: for EUR/USD the firstAssetId is EUR ID and lastAssetId is USD ID. |






<a name=".ProtoOASymbolsForConversionRes"></a>

### ProtoOASymbolsForConversionRes
Response to the ProtoOASymbolsForConversionReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOLS_FOR_CONVERSION_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbol | [ProtoOALightSymbol](/./models/#protooalightsymbol) | repeated | Conversion chain of the symbols (e.g. EUR/USD, USD/JPY, GBP/JPY -&gt; EUR/GBP). |






<a name=".ProtoOASymbolsListReq"></a>

### ProtoOASymbolsListReq
Request for a list of symbols available for a trading account. Symbol entries are returned with the limited set of fields.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOLS_LIST_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| includeArchivedSymbols | [bool](#bool) | optional |  Default: false |






<a name=".ProtoOASymbolsListRes"></a>

### ProtoOASymbolsListRes
Response to the ProtoOASymbolsListReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_SYMBOLS_LIST_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbol | [ProtoOALightSymbol](/./models/#protooalightsymbol) | repeated | The list of symbols. |
| archivedSymbol | [ProtoOAArchivedSymbol](/./models/#protooaarchivedsymbol) | repeated | The list of archived symbols. |






<a name=".ProtoOATraderReq"></a>

### ProtoOATraderReq
Request for getting data of Trader&#39;s Account.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_TRADER_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOATraderRes"></a>

### ProtoOATraderRes
Response to the ProtoOATraderReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_TRADER_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| trader | [ProtoOATrader](/./models/#protooatrader) | required | The Trader account information. |






<a name=".ProtoOATraderUpdatedEvent"></a>

### ProtoOATraderUpdatedEvent
Event that is sent when a Trader is updated on Server side.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_TRADER_UPDATE_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| trader | [ProtoOATrader](/./models/#protooatrader) | required | The Trader account information. |






<a name=".ProtoOATrailingSLChangedEvent"></a>

### ProtoOATrailingSLChangedEvent
Event that is sent when the level of the Trailing Stop Loss is changed due to the price level changes.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_TRAILING_SL_CHANGED_EVENT |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| positionId | [int64](#int64) | required | The unique ID of the position. |
| orderId | [int64](#int64) | required | The unique ID of the order. |
| stopPrice | [double](#double) | required | New value of the Stop Loss price. |
| utcLastUpdateTimestamp | [int64](#int64) | required | The exact UTC time when the Stop Loss was updated. |






<a name=".ProtoOAUnsubscribeDepthQuotesReq"></a>

### ProtoOAUnsubscribeDepthQuotesReq
Request for unsubscribing from the depth of market of the specified symbol.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_UNSUBSCRIBE_DEPTH_QUOTES_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | repeated | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOAUnsubscribeDepthQuotesRes"></a>

### ProtoOAUnsubscribeDepthQuotesRes
Response to the ProtoOAUnsubscribeDepthQuotesReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_UNSUBSCRIBE_DEPTH_QUOTES_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOAUnsubscribeLiveTrendbarReq"></a>

### ProtoOAUnsubscribeLiveTrendbarReq
Request for unsubscribing from the live trend bars.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_UNSUBSCRIBE_LIVE_TRENDBAR_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| period | [ProtoOATrendbarPeriod](/./models/#protooatrendbarperiod) | required | Specifies period of trend bar series (e.g. M1, M10, etc.). |
| symbolId | [int64](#int64) | required | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOAUnsubscribeLiveTrendbarRes"></a>

### ProtoOAUnsubscribeLiveTrendbarRes
Response to the ProtoOASubscribeLiveTrendbarReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_UNSUBSCRIBE_LIVE_TRENDBAR_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOAUnsubscribeSpotsReq"></a>

### ProtoOAUnsubscribeSpotsReq
Request for unsubscribing from the spot events of the specified symbol.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_UNSUBSCRIBE_SPOTS_REQ |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |
| symbolId | [int64](#int64) | repeated | Unique identifier of the Symbol in cTrader platform. |






<a name=".ProtoOAUnsubscribeSpotsRes"></a>

### ProtoOAUnsubscribeSpotsRes
Response to the ProtoOASubscribeSpotsRes request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_UNSUBSCRIBE_SPOTS_RES |
| ctidTraderAccountId | [int64](#int64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts. |






<a name=".ProtoOAVersionReq"></a>

### ProtoOAVersionReq
Request for getting the proxy version. Can be used to check the current version of the Open API scheme.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_VERSION_REQ |






<a name=".ProtoOAVersionRes"></a>

### ProtoOAVersionRes
Response to the ProtoOAVersionReq request.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| payloadType | [ProtoOAPayloadType](/./models/#protooapayloadtype) | optional |  Default: PROTO_OA_VERSION_RES |
| version | [string](#string) | required | The current version of the server application. |





 

 

 

 



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

