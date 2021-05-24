# Models
<a name="top"></a>

<a name="OpenApiModelMessages"></a>
<p align="right"><a href="#top">Top</a></p>

<a name=".ProtoOAArchivedSymbol"></a>

### ProtoOAArchivedSymbol



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| symbolId | [int64](#int64) | required |  |
| name | [string](#string) | required |  |
| utcLastUpdateTimestamp | [int64](#int64) | required |  |
| description | [string](#string) | optional |  |






<a name=".ProtoOAAsset"></a>

### ProtoOAAsset
Asset entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| assetId | [int64](#int64) | required | The unique asset ID. |
| name | [string](#string) | required | The asset name. |
| displayName | [string](#string) | optional | User friendly name. |
| digits | [int32](#int32) | optional | Precision of the asset. |






<a name=".ProtoOAAssetClass"></a>

### ProtoOAAssetClass
Asset class entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [int64](#int64) | optional | Unique asset ID. |
| name | [string](#string) | optional | Asset class name. |






<a name=".ProtoOABonusDepositWithdraw"></a>

### ProtoOABonusDepositWithdraw
Bonus deposit/withdrawal entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| operationType | [ProtoOAChangeBonusType](#protooachangebonustype) | required | Type of the operation. Deposit/Withdrawal. |
| bonusHistoryId | [int64](#int64) | required | The unique ID of the bonus deposit/withdrawal operation. |
| managerBonus | [int64](#int64) | required | Total amount of broker&#39;s bonus after the operation. |
| managerDelta | [int64](#int64) | required | Amount of bonus deposited/withdrew by manager. |
| ibBonus | [int64](#int64) | required | Total amount of introducing broker&#39;s bonus after the operation. |
| ibDelta | [int64](#int64) | required | Amount of bonus deposited/withdrew by introducing broker. |
| changeBonusTimestamp | [int64](#int64) | required | Time when the bonus operation was executed. |
| externalNote | [string](#string) | optional | Note added to operation. Visible to the trader. |
| introducingBrokerId | [int64](#int64) | optional | ID of introducing broker who deposited/withdrew bonus. |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects managerBonus, managerDelta, ibBonus, ibDelta. |






<a name=".ProtoOAClosePositionDetail"></a>

### ProtoOAClosePositionDetail
Trading details for closing deal.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| entryPrice | [double](#double) | required | Position price at the moment of filling the closing order. |
| grossProfit | [int64](#int64) | required | Amount of realized gross profit after closing deal execution. |
| swap | [int64](#int64) | required | Amount of realized swap related to closed volume. |
| commission | [int64](#int64) | required | Amount of realized commission related to closed volume. |
| balance | [int64](#int64) | required | Account balance after closing deal execution. |
| quoteToDepositConversionRate | [double](#double) | optional | Quote/Deposit currency conversion rate on the time of closing deal execution. |
| closedVolume | [int64](#int64) | optional | Closed volume in cents. |
| balanceVersion | [int64](#int64) | optional | Balance version of the account related to closing deal operation. |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects grossProfit, swap, commission, balance. |






<a name=".ProtoOACtidProfile"></a>

### ProtoOACtidProfile
Trader profile entity. Empty due to GDPR.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| userId | [int64](#int64) | required |  |






<a name=".ProtoOACtidTraderAccount"></a>

### ProtoOACtidTraderAccount
Trader account entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ctidTraderAccountId | [uint64](#uint64) | required | Unique identifier of the trader&#39;s account. Used to match responses to trader&#39;s accounts.cTrader platform. Different brokers might have different ids |
| isLive | [bool](#bool) | optional | If TRUE then the account is belong to Live environment and live host must be used to authorize it |
| traderLogin | [int64](#int64) | optional | TraderLogin for a specific account. Value is displayed on Client App UI |
| lastClosingDealTimestamp | [int64](#int64) | optional |  |
| lastBalanceUpdateTimestamp | [int64](#int64) | optional |  |






<a name=".ProtoOADeal"></a>

### ProtoOADeal
Execution entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| dealId | [int64](#int64) | required | The unique ID of the execution deal. |
| orderId | [int64](#int64) | required | Source order of the deal. |
| positionId | [int64](#int64) | required | Source position of the deal. |
| volume | [int64](#int64) | required | Volume sent for execution, in cents. |
| filledVolume | [int64](#int64) | required | Filled volume, in cents. |
| symbolId | [int64](#int64) | required | The unique identifier of the symbol in specific server environment within cTrader platform. Different servers have different IDs. |
| createTimestamp | [int64](#int64) | required | Time when the deal was sent for execution. |
| executionTimestamp | [int64](#int64) | required | Time when the deal was executed. |
| utcLastUpdateTimestamp | [int64](#int64) | optional | Timestamp when the deal was created, executed or rejected. |
| executionPrice | [double](#double) | optional | Execution price. |
| tradeSide | [ProtoOATradeSide](#protooatradeside) | required | Buy/Sell. |
| dealStatus | [ProtoOADealStatus](#protooadealstatus) | required | Status of the deal. |
| marginRate | [double](#double) | optional | Rate for used margin computation. Represented as Base/Deposit. |
| commission | [int64](#int64) | optional | Amount of trading commission associated with the deal. |
| baseToUsdConversionRate | [double](#double) | optional | Base to USD conversion rate on the time of deal execution. |
| closePositionDetail | [ProtoOAClosePositionDetail](#protooaclosepositiondetail) | optional | Closing position detail. Valid only for closing deal. |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects commission. |






<a name=".ProtoOADepositWithdraw"></a>

### ProtoOADepositWithdraw
Account deposit/withdrawal operation entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| operationType | [ProtoOAChangeBalanceType](#protooachangebalancetype) | required | Type of the operation. Deposit/Withdrawal. |
| balanceHistoryId | [int64](#int64) | required | The unique ID of the deposit/withdrawal operation. |
| balance | [int64](#int64) | required | Account balance after the operation was executed. |
| delta | [int64](#int64) | required | Amount of deposit/withdrawal operation. |
| changeBalanceTimestamp | [int64](#int64) | required | Time when deposit/withdrawal operation was executed. |
| externalNote | [string](#string) | optional | Note added to operation. Visible to the trader. |
| balanceVersion | [int64](#int64) | optional | Balance version used to identify the final balance. Increments each time when the trader&#39;s account balance is changed. |
| equity | [int64](#int64) | optional | Total account&#39;s equity after balance operation was executed. |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects balance, delta, equity. |






<a name=".ProtoOADepthQuote"></a>

### ProtoOADepthQuote
Depth of market entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [uint64](#uint64) | required | Quote ID. |
| size | [uint64](#uint64) | required | Quote size in cents. |
| bid | [uint64](#uint64) | optional | Bid price for bid quotes. |
| ask | [uint64](#uint64) | optional | Ask price for ask quotes. |






<a name=".ProtoOAExpectedMargin"></a>

### ProtoOAExpectedMargin
Expected margin computation entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| volume | [int64](#int64) | required | Volume in cents used for computation of expected margin. |
| buyMargin | [int64](#int64) | required | Buy margin amount. |
| sellMargin | [int64](#int64) | required | Sell margin amount. |






<a name=".ProtoOAHoliday"></a>

### ProtoOAHoliday



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| holidayId | [int64](#int64) | required | Unique ID of holiday. |
| name | [string](#string) | required | Name of holiday. |
| description | [string](#string) | optional | Description of holiday. |
| scheduleTimeZone | [string](#string) | required | Timezone used for holiday. |
| holidayDate | [int64](#int64) | required | Amount of days from 01-01-1970, multiply it by 86400000 to get unix timestamp. |
| isRecurring | [bool](#bool) | required | If TRUE, then the holiday happens each year. |
| startSecond | [int32](#int32) | optional | Amount of seconds from 00:00:00 of the holiday day when holiday actually starts. |
| endSecond | [int32](#int32) | optional | Amount of seconds from 00:00:00 of the holiday day when holiday actually finishes. |






<a name=".ProtoOAInterval"></a>

### ProtoOAInterval
Symbol trading session entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| startSecond | [uint32](#uint32) | required | Interval start, specified in seconds starting from SUNDAY 00:00 in specified time zone (inclusive to the interval). |
| endSecond | [uint32](#uint32) | required | Interval end, specified in seconds starting from SUNDAY 00:00 in specified time zone (exclusive from the interval). |






<a name=".ProtoOALightSymbol"></a>

### ProtoOALightSymbol
Lightweight symbol entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| symbolId | [int64](#int64) | required | The unique identifier of the symbol in specific server environment within cTrader platform. Different brokers might have different IDs. |
| symbolName | [string](#string) | optional | Name of the symbol (e.g. EUR/USD). |
| enabled | [bool](#bool) | optional | If TRUE then symbol is visible for traders. |
| baseAssetId | [int64](#int64) | optional | Base asset. |
| quoteAssetId | [int64](#int64) | optional | Quote asset. |
| symbolCategoryId | [int64](#int64) | optional | Id of the symbol category used for symbols grouping. |
| description | [string](#string) | optional |  |






<a name=".ProtoOAMarginCall"></a>

### ProtoOAMarginCall
Margin call entity, specifies threshold for exact margin call type. Only 3 instances of margin calls are supported, identified by marginCallType. See ProtoOANotificationType for details.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| marginCallType | [ProtoOANotificationType](#protooanotificationtype) | required |  |
| marginLevelThreshold | [double](#double) | required |  |
| utcLastUpdateTimestamp | [int64](#int64) | optional |  |






<a name=".ProtoOAOrder"></a>

### ProtoOAOrder
Trade order entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| orderId | [int64](#int64) | required | The unique ID of the order. Note: trader might have two orders with the same id if orders are taken from accounts from different brokers. |
| tradeData | [ProtoOATradeData](#protooatradedata) | required | Detailed trader data. |
| orderType | [ProtoOAOrderType](#protooaordertype) | required | Order type. |
| orderStatus | [ProtoOAOrderStatus](#protooaorderstatus) | required | Order status. |
| expirationTimestamp | [int64](#int64) | optional | If the order has time in force GTD then expiration is specified. |
| executionPrice | [double](#double) | optional | Price at which an order was executed. For order with FILLED status. |
| executedVolume | [int64](#int64) | optional | Part of the volume that was filled. |
| utcLastUpdateTimestamp | [int64](#int64) | optional | Timestamp of the last update of the order. |
| baseSlippagePrice | [double](#double) | optional | Used for Market Range order with combination of slippageInPoints to specify price range were order can be executed. |
| slippageInPoints | [int64](#int64) | optional | Used for Market Range and STOP_LIMIT orders to to specify price range were order can be executed. |
| closingOrder | [bool](#bool) | optional | If TRUE then the order is closing part of whole position. Must have specified positionId. |
| limitPrice | [double](#double) | optional | Valid only for LIMIT orders. |
| stopPrice | [double](#double) | optional | Valid only for STOP and STOP_LIMIT orders. |
| stopLoss | [double](#double) | optional | Absolute stopLoss price. |
| takeProfit | [double](#double) | optional | Absolute takeProfit price. |
| clientOrderId | [string](#string) | optional | Optional ClientOrderId. Max Length = 50 chars. |
| timeInForce | [ProtoOATimeInForce](#protooatimeinforce) | optional | Order&#39;s time in force. Depends on order type. Default: IMMEDIATE_OR_CANCEL |
| positionId | [int64](#int64) | optional | ID of the position linked to the order (e.g. closing order, order that increase volume of a specific position, etc.). |
| relativeStopLoss | [int64](#int64) | optional | Relative stopLoss that can be specified instead of absolute as one. Specified in 1/100_000 of unit of a price. For BUY stopLoss = entryPrice - relativeStopLoss, for SELL stopLoss = entryPrice &#43; relativeStopLoss. |
| relativeTakeProfit | [int64](#int64) | optional | Relative takeProfit that can be specified instead of absolute one. Specified in 1/100_000 of unit of a price. ForBUY takeProfit = entryPrice &#43; relativeTakeProfit, for SELL takeProfit = entryPrice - relativeTakeProfit. |
| isStopOut | [bool](#bool) | optional | If TRUE then order was stopped out from server side. |
| trailingStopLoss | [bool](#bool) | optional | If TRUE then order is trailingStopLoss. Valid for STOP_LOSS_TAKE_PROFIT order. |
| stopTriggerMethod | [ProtoOAOrderTriggerMethod](#protooaordertriggermethod) | optional | Trigger method for the order. Valid only for STOP and STOP_LIMIT orders. Default: TRADE |






<a name=".ProtoOAPosition"></a>

### ProtoOAPosition
Trade position entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| positionId | [int64](#int64) | required | The unique ID of the position. Note: trader might have two positions with the same id if positions are taken from accounts from different brokers. |
| tradeData | [ProtoOATradeData](#protooatradedata) | required | Position details. See ProtoOATradeData for details. |
| positionStatus | [ProtoOAPositionStatus](#protooapositionstatus) | required | Current status of the position. |
| swap | [int64](#int64) | required | Total amount of charged swap on open position. |
| price | [double](#double) | optional | VWAP price of the position based on all executions (orders) linked to the position. |
| stopLoss | [double](#double) | optional | Current stop loss price. |
| takeProfit | [double](#double) | optional | Current take profit price. |
| utcLastUpdateTimestamp | [int64](#int64) | optional | Time of the last change of the position, including amend SL/TP of the position, execution of related order, cancel or related order, etc. |
| commission | [int64](#int64) | optional | Current unrealized commission related to the position. |
| marginRate | [double](#double) | optional | Rate for used margin computation. Represented as Base/Deposit. |
| mirroringCommission | [int64](#int64) | optional | Amount of unrealized commission related to following of strategy provider. |
| guaranteedStopLoss | [bool](#bool) | optional | If TRUE then position&#39;s stop loss is guaranteedStopLoss. |
| usedMargin | [uint64](#uint64) | optional | Amount of margin used for the position in deposit currency. |
| stopLossTriggerMethod | [ProtoOAOrderTriggerMethod](#protooaordertriggermethod) | optional | Stop trigger method for SL/TP of the position. Default: TRADE |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects swap, commission, mirroringCommission, usedMargin. |






<a name=".ProtoOASymbol"></a>

### ProtoOASymbol
Trading symbol entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| symbolId | [int64](#int64) | required | The unique identifier of the symbol in specific server environment within cTrader platform. Different servers have different IDs. |
| digits | [int32](#int32) | required | Number of price digits to be displayed. |
| pipPosition | [int32](#int32) | required | Pip position on digits. |
| enableShortSelling | [bool](#bool) | optional | If TRUE then the short selling with the symbol is enabled. |
| guaranteedStopLoss | [bool](#bool) | optional | If TRUE then setting of guaranteedStopLoss is available for limited risk accounts. |
| swapRollover3Days | [ProtoOADayOfWeek](#protooadayofweek) | optional | Day of the week when SWAP charge amount will be tripled. Doesn&#39;t impact Rollover Commission. Default: MONDAY |
| swapLong | [double](#double) | optional | SWAP charge for long positions. |
| swapShort | [double](#double) | optional | SWAP charge for short positions. |
| maxVolume | [int64](#int64) | optional | Maximum allowed volume in cents for an order with a symbol. |
| minVolume | [int64](#int64) | optional | Minimum allowed volume in cents for an order with a symbol. |
| stepVolume | [int64](#int64) | optional | Step of the volume in cents for an order. |
| maxExposure | [uint64](#uint64) | optional | Value of max exposure per symbol, per account. Blocks execution if breached. |
| schedule | [ProtoOAInterval](#protooainterval) | repeated | Symbol trading interval, specified in seconds starting from SUNDAY 00:00 in specified time zone. |
| commission | [int64](#int64) | optional | **Deprecated.** Commission base amount. Total commission depends on commissionType. Use preciseTradingCommissionRate. |
| commissionType | [ProtoOACommissionType](#protooacommissiontype) | optional | Commission type. See ProtoOACommissionType for details. Default: USD_PER_MILLION_USD |
| slDistance | [uint32](#uint32) | optional | Minimum allowed distance between stop loss and current market price. |
| tpDistance | [uint32](#uint32) | optional | Minimum allowed distance between take profit and current market price. |
| gslDistance | [uint32](#uint32) | optional | Minimum allowed distance between guaranteed stop loss and current market price. |
| gslCharge | [int64](#int64) | optional | Guaranteed stop loss fee. |
| distanceSetIn | [ProtoOASymbolDistanceType](#protooasymboldistancetype) | optional | Unit of distance measure for slDistance, tpDistance, gslDistance. Default: SYMBOL_DISTANCE_IN_POINTS |
| minCommission | [int64](#int64) | optional | **Deprecated.** Minimum commission amount per trade. Use preciseMinCommission. |
| minCommissionType | [ProtoOAMinCommissionType](#protooamincommissiontype) | optional | Minimum commission Type. See ProtoOAMinCommissionType for details. Default: CURRENCY |
| minCommissionAsset | [string](#string) | optional | Currency for minimum commission. (USD or quote currency). Default: USD |
| rolloverCommission | [int64](#int64) | optional | Amount of commission per trade for Shariah Compliant accounts in deposit currency (swapFree = TRUE). |
| skipRolloverDays | [int32](#int32) | optional | Initial period before the first rolloverCommission will be charged on the account. |
| scheduleTimeZone | [string](#string) | optional | Time zone for the symbol trading intervals. |
| tradingMode | [ProtoOATradingMode](#protooatradingmode) | optional | Rules for trading with the symbol. See ProtoOATradingMode for details. Default: ENABLED |
| rolloverCommission3Days | [ProtoOADayOfWeek](#protooadayofweek) | optional | Day of the week (in UTC) when Administrative Fee charge amount will be tripled. Applied only if RolloverChargePeriod = 0 or 1 Default: MONDAY |
| swapCalculationType | [ProtoOASwapCalculationType](#protooaswapcalculationtype) | optional | Specifies type of SWAP computation as PIPS (0) or PERCENTAGE (1, annual, in percent) Default: PIPS |
| lotSize | [int64](#int64) | optional | Lot size of the Symbol (in cents) |
| preciseTradingCommissionRate | [int64](#int64) | optional | Commission base amount. Total commission depends on commissionType: for non-percentage types it is multiplied by 10^8. |
| preciseMinCommission | [int64](#int64) | optional | Minimum commission amount per trade multiplied by 10^8. |
| holiday | [ProtoOAHoliday](#protooaholiday) | repeated | List of holidays for this symbol specified by broker. |






<a name=".ProtoOASymbolCategory"></a>

### ProtoOASymbolCategory
Symbol category entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| id | [int64](#int64) | required | The unique identifier of the symbol category. |
| assetClassId | [int64](#int64) | required | Link to the asset class. One asset class can have many symbol categories. |
| name | [string](#string) | required | Category name. |






<a name=".ProtoOATickData"></a>

### ProtoOATickData
Historical tick data type.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| timestamp | [int64](#int64) | required | Tick timestamp. |
| tick | [int64](#int64) | required | Tick price. |






<a name=".ProtoOATradeData"></a>

### ProtoOATradeData
Position/order trading details entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| symbolId | [int64](#int64) | required | The unique identifier of the symbol in specific server environment within cTrader platform. Different brokers might have different IDs. |
| volume | [int64](#int64) | required | Volume in cents. |
| tradeSide | [ProtoOATradeSide](#protooatradeside) | required | Buy, Sell. |
| openTimestamp | [int64](#int64) | optional | Time when position was opened or order was created. |
| label | [string](#string) | optional | Text label specified during order request. |
| guaranteedStopLoss | [bool](#bool) | optional | If TRUE then position/order stop loss is guaranteedStopLoss. |
| comment | [string](#string) | optional | User-specified comment. |






<a name=".ProtoOATrader"></a>

### ProtoOATrader
Trading account entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ctidTraderAccountId | [int64](#int64) | required | The unique Trader&#39;s Account ID used to match the responses to the Trader&#39;s Account. |
| balance | [int64](#int64) | required | Current account balance. |
| balanceVersion | [int64](#int64) | optional | Balance version used to identify the final balance. Increments each time when the trader&#39;s account balance is changed. |
| managerBonus | [int64](#int64) | optional | Amount of broker&#39;s bonus allocated to the account. |
| ibBonus | [int64](#int64) | optional | Amount of introducing broker bonus allocated to the account. |
| nonWithdrawableBonus | [int64](#int64) | optional | Broker&#39;s bonus that cannot be withdrew from the account as cash. |
| accessRights | [ProtoOAAccessRights](#protooaaccessrights) | optional | Access rights that an owner has to the account in cTrader platform. See ProtoOAAccessRights for details. Default: FULL_ACCESS |
| depositAssetId | [int64](#int64) | required | Deposit currency of the account. |
| swapFree | [bool](#bool) | optional | If TRUE then account is Shariah compliant. |
| leverageInCents | [uint32](#uint32) | optional | Account leverage (e.g. If leverage = 1:50 then value = 5000). |
| totalMarginCalculationType | [ProtoOATotalMarginCalculationType](#protooatotalmargincalculationtype) | optional | Margin computation type for the account (MAX, SUM, NET). |
| maxLeverage | [uint32](#uint32) | optional | Maximum allowed leverage for the account. Used as validation when a Trader can change leverage value. |
| frenchRisk | [bool](#bool) | optional | **Deprecated.** If TRUE then account is AMF compliant. Use isLimitedRisk and limitedRiskMarginCalculationStrategy. |
| traderLogin | [int64](#int64) | optional | ID of the account that is unique per server (Broker). |
| accountType | [ProtoOAAccountType](#protooaaccounttype) | optional | Account type: HEDGED, NETTED, etc. Default: HEDGED |
| brokerName | [string](#string) | optional | Some whitelabel assigned to trader by broker at the moment of account creation. |
| registrationTimestamp | [int64](#int64) | optional | Unix timestamp of the account registration. Should be used as minimal date in historical data requests. |
| isLimitedRisk | [bool](#bool) | optional | If TRUE then account is compliant to use specific margin calculation strategy. |
| limitedRiskMarginCalculationStrategy | [ProtoOALimitedRiskMarginCalculationStrategy](#protooalimitedriskmargincalculationstrategy) | optional | Special strategy used in margin calculations for this account (if account isLimitedRisk). Default: ACCORDING_TO_LEVERAGE |
| moneyDigits | [uint32](#uint32) | optional | Specifies the exponent of the monetary values. E.g. moneyDigits = 8 must be interpret as business value multiplied by 10^8, then real balance would be 10053099944 / 10^8 = 100.53099944. Affects balance, managerBonus, ibBonus, nonWithdrawableBonus. |






<a name=".ProtoOATrendbar"></a>

### ProtoOATrendbar
Historical Trendbar entity.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| volume | [int64](#int64) | required | Bar volume in ticks. |
| period | [ProtoOATrendbarPeriod](#protooatrendbarperiod) | optional | Bar period. Default: M1 |
| low | [int64](#int64) | optional | Low price of the bar. |
| deltaOpen | [uint64](#uint64) | optional | Delta between open and low price. open = low &#43; deltaOpen. |
| deltaClose | [uint64](#uint64) | optional | Delta between close and low price. close = low &#43; deltaClose. |
| deltaHigh | [uint64](#uint64) | optional | Delta between high and low price. high = low &#43; deltaHigh. |
| utcTimestampInMinutes | [uint32](#uint32) | optional | Timestamp of the bar. Equal to the timestamp of the open tick. |





 


<a name=".ProtoOAAccessRights"></a>

### ProtoOAAccessRights
Enum for specifying access right for a trader.

| Name | Number | Description |
| ---- | ------ | ----------- |
| FULL_ACCESS | 0 | Enable all trading. |
| CLOSE_ONLY | 1 | Only closing trading request are enabled. |
| NO_TRADING | 2 | View only access. |
| NO_LOGIN | 3 | No access. |



<a name=".ProtoOAAccountType"></a>

### ProtoOAAccountType
Enum for specifying type of an account.

| Name | Number | Description |
| ---- | ------ | ----------- |
| HEDGED | 0 | Allows multiple positions on a trading account for a symbol. |
| NETTED | 1 | Only one position per symbol is allowed on a trading account. |
| SPREAD_BETTING | 2 | Spread betting type account. |



<a name=".ProtoOAChangeBalanceType"></a>

### ProtoOAChangeBalanceType
Balance operation entity. Covers all cash movement operations related to account, trading, IB operations, mirroring, etc.

| Name | Number | Description |
| ---- | ------ | ----------- |
| BALANCE_DEPOSIT | 0 | Cash deposit. |
| BALANCE_WITHDRAW | 1 | Cash withdrawal. |
| BALANCE_DEPOSIT_STRATEGY_COMMISSION_INNER | 3 | Received mirroring commission. |
| BALANCE_WITHDRAW_STRATEGY_COMMISSION_INNER | 4 | Paid mirroring commission. |
| BALANCE_DEPOSIT_IB_COMMISSIONS | 5 | For IB account. Commissions paid by trader. |
| BALANCE_WITHDRAW_IB_SHARED_PERCENTAGE | 6 | For IB account. Withdrawal of commissions shared with broker. |
| BALANCE_DEPOSIT_IB_SHARED_PERCENTAGE_FROM_SUB_IB | 7 | For IB account. Commissions paid by sub-ibs. |
| BALANCE_DEPOSIT_IB_SHARED_PERCENTAGE_FROM_BROKER | 8 | For IB account. Commissions paid by broker. |
| BALANCE_DEPOSIT_REBATE | 9 | Deposit rebate for trading volume for period. |
| BALANCE_WITHDRAW_REBATE | 10 | Withdrawal of rebate. |
| BALANCE_DEPOSIT_STRATEGY_COMMISSION_OUTER | 11 | Mirroring commission. |
| BALANCE_WITHDRAW_STRATEGY_COMMISSION_OUTER | 12 | Mirroring commission. |
| BALANCE_WITHDRAW_BONUS_COMPENSATION | 13 | For IB account. Share commission with the Broker. |
| BALANCE_WITHDRAW_IB_SHARED_PERCENTAGE_TO_BROKER | 14 | IB commissions. |
| BALANCE_DEPOSIT_DIVIDENDS | 15 | Deposit dividends payments. |
| BALANCE_WITHDRAW_DIVIDENDS | 16 | Negative dividend charge for short position. |
| BALANCE_WITHDRAW_GSL_CHARGE | 17 | Charge for guaranteedStopLoss. |
| BALANCE_WITHDRAW_ROLLOVER | 18 | Charge of rollover fee for Shariah compliant accounts. |
| BALANCE_DEPOSIT_NONWITHDRAWABLE_BONUS | 19 | Broker&#39;s operation to deposit bonus. |
| BALANCE_WITHDRAW_NONWITHDRAWABLE_BONUS | 20 | Broker&#39;s operation to withdrawal bonus. |
| BALANCE_DEPOSIT_SWAP | 21 | Deposits of negative SWAP. |
| BALANCE_WITHDRAW_SWAP | 22 | SWAP charges. |
| BALANCE_DEPOSIT_MANAGEMENT_FEE | 27 | Mirroring commission. |
| BALANCE_WITHDRAW_MANAGEMENT_FEE | 28 | Mirroring commission. Deprecated since 7.1 in favor of BALANCE_WITHDRAW_COPY_FEE (34). |
| BALANCE_DEPOSIT_PERFORMANCE_FEE | 29 | Mirroring commission. |
| BALANCE_WITHDRAW_FOR_SUBACCOUNT | 30 |  |
| BALANCE_DEPOSIT_TO_SUBACCOUNT | 31 |  |
| BALANCE_WITHDRAW_FROM_SUBACCOUNT | 32 |  |
| BALANCE_DEPOSIT_FROM_SUBACCOUNT | 33 |  |
| BALANCE_WITHDRAW_COPY_FEE | 34 | Withdrawal fees to Strategy Provider. |
| BALANCE_WITHDRAW_INACTIVITY_FEE | 35 | Withdraw of inactivity fee from the balance |
| BALANCE_DEPOSIT_TRANSFER | 36 |  |
| BALANCE_WITHDRAW_TRANSFER | 37 |  |
| BALANCE_DEPOSIT_CONVERTED_BONUS | 38 |  |
| BALANCE_DEPOSIT_NEGATIVE_BALANCE_PROTECTION | 39 |  |



<a name=".ProtoOAChangeBonusType"></a>

### ProtoOAChangeBonusType
Bonus operation type ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| BONUS_DEPOSIT | 0 |  |
| BONUS_WITHDRAW | 1 |  |



<a name=".ProtoOAClientPermissionScope"></a>

### ProtoOAClientPermissionScope
Open API application permission in regards to token ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| SCOPE_VIEW | 0 | Allows to use only view commends. Trade is prohibited. |
| SCOPE_TRADE | 1 | Allows to use all commands. |



<a name=".ProtoOACommissionType"></a>

### ProtoOACommissionType
Enum for specifying type of trading commission.

| Name | Number | Description |
| ---- | ------ | ----------- |
| USD_PER_MILLION_USD | 1 | USD per million USD volume - usually used for FX. Example: 50 USD for 1 mil USD of trading volume. |
| USD_PER_LOT | 2 | USD per 1 lot - usually used for CFDs and futures for commodities, and indices. Example: 15 USD for 1 contract. |
| PERCENTAGE_OF_VALUE | 3 | Percentage of trading volume - usually used for Equities. Example: 0.005% of notional trading volume. Multiplied by 100,00. |
| QUOTE_CCY_PER_LOT | 4 | Quote ccy of Symbol per 1 lot - will be used for CFDs and futures for commodities, and indices. Example: 15 EUR for 1 contract of DAX. |



<a name=".ProtoOADayOfWeek"></a>

### ProtoOADayOfWeek


| Name | Number | Description |
| ---- | ------ | ----------- |
| NONE | 0 |  |
| MONDAY | 1 |  |
| TUESDAY | 2 |  |
| WEDNESDAY | 3 |  |
| THURSDAY | 4 |  |
| FRIDAY | 5 |  |
| SATURDAY | 6 |  |
| SUNDAY | 7 |  |



<a name=".ProtoOADealStatus"></a>

### ProtoOADealStatus
Deal status ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| FILLED | 2 | Deal filled. |
| PARTIALLY_FILLED | 3 | Deal is partially filled. |
| REJECTED | 4 | Deal is correct but was rejected by liquidity provider (e.g. no liquidity). |
| INTERNALLY_REJECTED | 5 | Deal rejected by server (e.g. no price quotes). |
| ERROR | 6 | Deal is rejected by LP due to error (e.g. symbol is unknown). |
| MISSED | 7 | Liquidity provider did not sent response on the deal during specified execution time period. |



<a name=".ProtoOAErrorCode"></a>

### ProtoOAErrorCode
Error code ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| OA_AUTH_TOKEN_EXPIRED | 1 | When token used for account authorization is expired. |
| ACCOUNT_NOT_AUTHORIZED | 2 | When account is not authorized. |
| ALREADY_LOGGED_IN | 14 | When client tries to authorize after it was already authorized |
| CH_CLIENT_AUTH_FAILURE | 101 | Open API client is not activated or wrong client credentials. |
| CH_CLIENT_NOT_AUTHENTICATED | 102 | When a command is sent for not authorized Open API client. |
| CH_CLIENT_ALREADY_AUTHENTICATED | 103 | Client is trying to authenticate twice. |
| CH_ACCESS_TOKEN_INVALID | 104 | Access token is invalid. |
| CH_SERVER_NOT_REACHABLE | 105 | Trading service is not available. |
| CH_CTID_TRADER_ACCOUNT_NOT_FOUND | 106 | Trading account is not found. |
| CH_OA_CLIENT_NOT_FOUND | 107 | Could not find this client id. |
| REQUEST_FREQUENCY_EXCEEDED | 108 | Request frequency is reached. |
| SERVER_IS_UNDER_MAINTENANCE | 109 | Server is under maintenance. |
| CHANNEL_IS_BLOCKED | 110 | Operations are not allowed for this account. |
| CONNECTIONS_LIMIT_EXCEEDED | 67 | Limit of connections is reached for this Open API client. |
| WORSE_GSL_NOT_ALLOWED | 68 | Not allowed to increase risk for Positions with Guaranteed Stop Loss. |
| SYMBOL_HAS_HOLIDAY | 69 | Trading disabled because symbol has holiday. |
| NOT_SUBSCRIBED_TO_SPOTS | 112 | When trying to subscribe to depth, trendbars, etc. without spot subscription. |
| ALREADY_SUBSCRIBED | 113 | When subscription is requested for an active. |
| SYMBOL_NOT_FOUND | 114 | Symbol not found. |
| UNKNOWN_SYMBOL | 115 | Note: to be merged with SYMBOL_NOT_FOUND. |
| INCORRECT_BOUNDARIES | 35 | When requested period (from,to) is too large or invalid values are set to from/to. |
| NO_QUOTES | 117 | Trading cannot be done as not quotes are available. Applicable for Book B. |
| NOT_ENOUGH_MONEY | 118 | Not enough funds to allocate margin. |
| MAX_EXPOSURE_REACHED | 119 | Max exposure limit is reached for a {trader, symbol, side}. |
| POSITION_NOT_FOUND | 120 | Position not found. |
| ORDER_NOT_FOUND | 121 | Order not found. |
| POSITION_NOT_OPEN | 122 | When trying to close a position that it is not open. |
| POSITION_LOCKED | 123 | Position in the state that does not allow to perform an operation. |
| TOO_MANY_POSITIONS | 124 | Trading account reached its limit for max number of open positions and orders. |
| TRADING_BAD_VOLUME | 125 | Invalid volume. |
| TRADING_BAD_STOPS | 126 | Invalid stop price. |
| TRADING_BAD_PRICES | 127 | Invalid price (e.g. negative). |
| TRADING_BAD_STAKE | 128 | Invalid stake volume (e.g. negative). |
| PROTECTION_IS_TOO_CLOSE_TO_MARKET | 129 | Invalid protection prices. |
| TRADING_BAD_EXPIRATION_DATE | 130 | Invalid expiration. |
| PENDING_EXECUTION | 131 | Unable to apply changes as position has an order under execution. |
| TRADING_DISABLED | 132 | Trading is blocked for the symbol. |
| TRADING_NOT_ALLOWED | 133 | Trading account is in read only mode. |
| UNABLE_TO_CANCEL_ORDER | 134 | Unable to cancel order. |
| UNABLE_TO_AMEND_ORDER | 135 | Unable to amend order. |
| SHORT_SELLING_NOT_ALLOWED | 136 | Short selling is not allowed. |



<a name=".ProtoOAExecutionType"></a>

### ProtoOAExecutionType
Execution event type ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ORDER_ACCEPTED | 2 | Order passed validation. |
| ORDER_FILLED | 3 | Order filled. |
| ORDER_REPLACED | 4 | Pending order is changed with a new one. |
| ORDER_CANCELLED | 5 | Order cancelled. |
| ORDER_EXPIRED | 6 | Order with GTD time in force is expired. |
| ORDER_REJECTED | 7 | Order is rejected due to validations. |
| ORDER_CANCEL_REJECTED | 8 | Cancel order request is rejected. |
| SWAP | 9 | Type related to SWAP execution events. |
| DEPOSIT_WITHDRAW | 10 | Type related to event of deposit or withdrawal cash flow operation. |
| ORDER_PARTIAL_FILL | 11 | Order is partially filled. |
| BONUS_DEPOSIT_WITHDRAW | 12 | Type related to event of bonus deposit or bonus withdrawal. |



<a name=".ProtoOALimitedRiskMarginCalculationStrategy"></a>

### ProtoOALimitedRiskMarginCalculationStrategy


| Name | Number | Description |
| ---- | ------ | ----------- |
| ACCORDING_TO_LEVERAGE | 0 |  |
| ACCORDING_TO_GSL | 1 |  |
| ACCORDING_TO_GSL_AND_LEVERAGE | 2 |  |



<a name=".ProtoOAMinCommissionType"></a>

### ProtoOAMinCommissionType
Enum for specifying type of minimum trading commission.

| Name | Number | Description |
| ---- | ------ | ----------- |
| CURRENCY | 1 |  |
| QUOTE_CURRENCY | 2 |  |



<a name=".ProtoOANotificationType"></a>

### ProtoOANotificationType
Type of notification, currently only 3 instances of marginCall are supported.

| Name | Number | Description |
| ---- | ------ | ----------- |
| MARGIN_LEVEL_THRESHOLD_1 | 61 | one of three margin calls, they are all similar. |
| MARGIN_LEVEL_THRESHOLD_2 | 62 | one of three margin calls, they are all similar. |
| MARGIN_LEVEL_THRESHOLD_3 | 63 | one of three margin calls, they are all similar. |



<a name=".ProtoOAOrderStatus"></a>

### ProtoOAOrderStatus
Order status ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ORDER_STATUS_ACCEPTED | 1 | Order request validated and accepted for execution. |
| ORDER_STATUS_FILLED | 2 | Order is fully filled. |
| ORDER_STATUS_REJECTED | 3 | Order is rejected due to validation. |
| ORDER_STATUS_EXPIRED | 4 | Order expired. Might be valid for orders with partially filled volume that were expired on LP. |
| ORDER_STATUS_CANCELLED | 5 | Order is cancelled. Might be valid for orders with partially filled volume that were cancelled by LP. |



<a name=".ProtoOAOrderTriggerMethod"></a>

### ProtoOAOrderTriggerMethod
Stop Order and Stop Lost triggering method ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| TRADE | 1 | Stop Order: buy is triggered by ask, sell by bid; Stop Loss Order: for buy position is triggered by bid and for sell position by ask. |
| OPPOSITE | 2 | Stop Order: buy is triggered by bid, sell by ask; Stop Loss Order: for buy position is triggered by ask and for sell position by bid. |
| DOUBLE_TRADE | 3 | The same as TRADE, but trigger is checked after the second consecutive tick. |
| DOUBLE_OPPOSITE | 4 | The same as OPPOSITE, but trigger is checked after the second consecutive tick. |



<a name=".ProtoOAOrderType"></a>

### ProtoOAOrderType
Order type ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| MARKET | 1 |  |
| LIMIT | 2 |  |
| STOP | 3 |  |
| STOP_LOSS_TAKE_PROFIT | 4 |  |
| MARKET_RANGE | 5 |  |
| STOP_LIMIT | 6 |  |



<a name=".ProtoOAPayloadType"></a>

### ProtoOAPayloadType


| Name | Number | Description |
| ---- | ------ | ----------- |
| PROTO_OA_APPLICATION_AUTH_REQ | 2100 |  |
| PROTO_OA_APPLICATION_AUTH_RES | 2101 |  |
| PROTO_OA_ACCOUNT_AUTH_REQ | 2102 |  |
| PROTO_OA_ACCOUNT_AUTH_RES | 2103 |  |
| PROTO_OA_VERSION_REQ | 2104 |  |
| PROTO_OA_VERSION_RES | 2105 |  |
| PROTO_OA_NEW_ORDER_REQ | 2106 |  |
| PROTO_OA_TRAILING_SL_CHANGED_EVENT | 2107 |  |
| PROTO_OA_CANCEL_ORDER_REQ | 2108 |  |
| PROTO_OA_AMEND_ORDER_REQ | 2109 |  |
| PROTO_OA_AMEND_POSITION_SLTP_REQ | 2110 |  |
| PROTO_OA_CLOSE_POSITION_REQ | 2111 |  |
| PROTO_OA_ASSET_LIST_REQ | 2112 |  |
| PROTO_OA_ASSET_LIST_RES | 2113 |  |
| PROTO_OA_SYMBOLS_LIST_REQ | 2114 |  |
| PROTO_OA_SYMBOLS_LIST_RES | 2115 |  |
| PROTO_OA_SYMBOL_BY_ID_REQ | 2116 |  |
| PROTO_OA_SYMBOL_BY_ID_RES | 2117 |  |
| PROTO_OA_SYMBOLS_FOR_CONVERSION_REQ | 2118 |  |
| PROTO_OA_SYMBOLS_FOR_CONVERSION_RES | 2119 |  |
| PROTO_OA_SYMBOL_CHANGED_EVENT | 2120 |  |
| PROTO_OA_TRADER_REQ | 2121 |  |
| PROTO_OA_TRADER_RES | 2122 |  |
| PROTO_OA_TRADER_UPDATE_EVENT | 2123 |  |
| PROTO_OA_RECONCILE_REQ | 2124 |  |
| PROTO_OA_RECONCILE_RES | 2125 |  |
| PROTO_OA_EXECUTION_EVENT | 2126 |  |
| PROTO_OA_SUBSCRIBE_SPOTS_REQ | 2127 |  |
| PROTO_OA_SUBSCRIBE_SPOTS_RES | 2128 |  |
| PROTO_OA_UNSUBSCRIBE_SPOTS_REQ | 2129 |  |
| PROTO_OA_UNSUBSCRIBE_SPOTS_RES | 2130 |  |
| PROTO_OA_SPOT_EVENT | 2131 |  |
| PROTO_OA_ORDER_ERROR_EVENT | 2132 |  |
| PROTO_OA_DEAL_LIST_REQ | 2133 |  |
| PROTO_OA_DEAL_LIST_RES | 2134 |  |
| PROTO_OA_SUBSCRIBE_LIVE_TRENDBAR_REQ | 2135 |  |
| PROTO_OA_UNSUBSCRIBE_LIVE_TRENDBAR_REQ | 2136 |  |
| PROTO_OA_GET_TRENDBARS_REQ | 2137 |  |
| PROTO_OA_GET_TRENDBARS_RES | 2138 |  |
| PROTO_OA_EXPECTED_MARGIN_REQ | 2139 |  |
| PROTO_OA_EXPECTED_MARGIN_RES | 2140 |  |
| PROTO_OA_MARGIN_CHANGED_EVENT | 2141 |  |
| PROTO_OA_ERROR_RES | 2142 |  |
| PROTO_OA_CASH_FLOW_HISTORY_LIST_REQ | 2143 |  |
| PROTO_OA_CASH_FLOW_HISTORY_LIST_RES | 2144 |  |
| PROTO_OA_GET_TICKDATA_REQ | 2145 |  |
| PROTO_OA_GET_TICKDATA_RES | 2146 |  |
| PROTO_OA_ACCOUNTS_TOKEN_INVALIDATED_EVENT | 2147 |  |
| PROTO_OA_CLIENT_DISCONNECT_EVENT | 2148 |  |
| PROTO_OA_GET_ACCOUNTS_BY_ACCESS_TOKEN_REQ | 2149 |  |
| PROTO_OA_GET_ACCOUNTS_BY_ACCESS_TOKEN_RES | 2150 |  |
| PROTO_OA_GET_CTID_PROFILE_BY_TOKEN_REQ | 2151 |  |
| PROTO_OA_GET_CTID_PROFILE_BY_TOKEN_RES | 2152 |  |
| PROTO_OA_ASSET_CLASS_LIST_REQ | 2153 |  |
| PROTO_OA_ASSET_CLASS_LIST_RES | 2154 |  |
| PROTO_OA_DEPTH_EVENT | 2155 |  |
| PROTO_OA_SUBSCRIBE_DEPTH_QUOTES_REQ | 2156 |  |
| PROTO_OA_SUBSCRIBE_DEPTH_QUOTES_RES | 2157 |  |
| PROTO_OA_UNSUBSCRIBE_DEPTH_QUOTES_REQ | 2158 |  |
| PROTO_OA_UNSUBSCRIBE_DEPTH_QUOTES_RES | 2159 |  |
| PROTO_OA_SYMBOL_CATEGORY_REQ | 2160 |  |
| PROTO_OA_SYMBOL_CATEGORY_RES | 2161 |  |
| PROTO_OA_ACCOUNT_LOGOUT_REQ | 2162 |  |
| PROTO_OA_ACCOUNT_LOGOUT_RES | 2163 |  |
| PROTO_OA_ACCOUNT_DISCONNECT_EVENT | 2164 |  |
| PROTO_OA_SUBSCRIBE_LIVE_TRENDBAR_RES | 2165 |  |
| PROTO_OA_UNSUBSCRIBE_LIVE_TRENDBAR_RES | 2166 |  |
| PROTO_OA_MARGIN_CALL_LIST_REQ | 2167 |  |
| PROTO_OA_MARGIN_CALL_LIST_RES | 2168 |  |
| PROTO_OA_MARGIN_CALL_UPDATE_REQ | 2169 |  |
| PROTO_OA_MARGIN_CALL_UPDATE_RES | 2170 |  |
| PROTO_OA_MARGIN_CALL_UPDATE_EVENT | 2171 |  |
| PROTO_OA_MARGIN_CALL_TRIGGER_EVENT | 2172 |  |
| PROTO_OA_REFRESH_TOKEN_REQ | 2173 |  |
| PROTO_OA_REFRESH_TOKEN_RES | 2174 |  |



<a name=".ProtoOAPositionStatus"></a>

### ProtoOAPositionStatus
Position status ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| POSITION_STATUS_OPEN | 1 |  |
| POSITION_STATUS_CLOSED | 2 |  |
| POSITION_STATUS_CREATED | 3 | Empty position is created for pending order. |
| POSITION_STATUS_ERROR | 4 |  |



<a name=".ProtoOAQuoteType"></a>

### ProtoOAQuoteType
Price quote type.

| Name | Number | Description |
| ---- | ------ | ----------- |
| BID | 1 |  |
| ASK | 2 |  |



<a name=".ProtoOASwapCalculationType"></a>

### ProtoOASwapCalculationType
Enum for specifying SWAP calculation type for symbol.

| Name | Number | Description |
| ---- | ------ | ----------- |
| PIPS | 0 | Specifies type of SWAP computation as PIPS (0) |
| PERCENTAGE | 1 | Specifies type of SWAP computation as PERCENTAGE (1, annual, in percent) |



<a name=".ProtoOASymbolDistanceType"></a>

### ProtoOASymbolDistanceType
Enum for specifying stop loss and take profit distances.

| Name | Number | Description |
| ---- | ------ | ----------- |
| SYMBOL_DISTANCE_IN_POINTS | 1 |  |
| SYMBOL_DISTANCE_IN_PERCENTAGE | 2 |  |



<a name=".ProtoOATimeInForce"></a>

### ProtoOATimeInForce
Order&#39;s time in force ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| GOOD_TILL_DATE | 1 |  |
| GOOD_TILL_CANCEL | 2 |  |
| IMMEDIATE_OR_CANCEL | 3 |  |
| FILL_OR_KILL | 4 |  |
| MARKET_ON_OPEN | 5 |  |



<a name=".ProtoOATotalMarginCalculationType"></a>

### ProtoOATotalMarginCalculationType
Enum for specifying margin calculation type for an account.

| Name | Number | Description |
| ---- | ------ | ----------- |
| MAX | 0 |  |
| SUM | 1 |  |
| NET | 2 |  |



<a name=".ProtoOATradeSide"></a>

### ProtoOATradeSide
Trader side ENUM. Used for order, position, deal.

| Name | Number | Description |
| ---- | ------ | ----------- |
| BUY | 1 |  |
| SELL | 2 |  |



<a name=".ProtoOATradingMode"></a>

### ProtoOATradingMode
Enum for specifying symbol trading mode.

| Name | Number | Description |
| ---- | ------ | ----------- |
| ENABLED | 0 |  |
| DISABLED_WITHOUT_PENDINGS_EXECUTION | 1 |  |
| DISABLED_WITH_PENDINGS_EXECUTION | 2 |  |
| CLOSE_ONLY_MODE | 3 |  |



<a name=".ProtoOATrendbarPeriod"></a>

### ProtoOATrendbarPeriod
Trendbar period ENUM.

| Name | Number | Description |
| ---- | ------ | ----------- |
| M1 | 1 |  |
| M2 | 2 |  |
| M3 | 3 |  |
| M4 | 4 |  |
| M5 | 5 |  |
| M10 | 6 |  |
| M15 | 7 |  |
| M30 | 8 |  |
| H1 | 9 |  |
| H4 | 10 |  |
| H12 | 11 |  |
| D1 | 12 |  |
| W1 | 13 |  |
| MN1 | 14 |  |
