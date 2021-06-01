## Historical Bars Data

To get the historical price data of a symbol, follow these steps:

 1. Create a [ProtoOAGetTrendbarsReq](../messages/#protooagettrendbarsreq) message.
 2. You have to fill the message fields with the trading account ID (**not login number**), symbol ID, period (time frame), and from/to timestamps, which are in Unix time milliseconds, the timestamps are subject to some limitations that you can find in the message reference table.
 3. Send the message, and you will receive a [ProtoOAGetTrendbarsRes](../messages/#protooagettrendbarsres) message, which will contain the historical data on its trendbar field.
 4. Transform the data from relative format to actual price format, To do that you have to use the trend bar low and divide it by 100000 and round the result to symbol digits. Then for getting high, open, close price levels, first add the trend bar delta level of each to low. At last divide each by 100000, and round the result to the symbol's digits.
 5. Now you have the historical price data for your requested time period.

## Historical Tick Data

You can get the historical tick price data from the API.

To get the tick data follow these steps:

 1. Create a [ProtoOAGetTickDataReq](../messages/#protooagettickdatareq) message.
 2. You have to fill the message fields with the trading account ID, symbol ID, type (bid/ask), and from/to timestamps, which are in Unix time milliseconds, The timestamps are subject to some limitations that you can find on the message reference table.
 3. Send the message, and you will receive a [ProtoOAGetTickDataRes](../messages/#protooagettickdatares) message, which will contain the historical data in its tickData field.
 4. Transform the data from relative format to actual price format, To do that you have to divide each tick by 100000, round the result to symbol digits.
 5. Now you have the historical tick data for your requested time period, there is an "hasMore" boolean field on ProtoOAGetTickDataRes, use it to check if there is more data than the amount returned.

## Live Bars Data

You can subscribe and receive live bars data from the API.

To receive live bars data follow these steps:

 1. Create a [ProtoOASubscribeLiveTrendbarReq](../messages/#protooasubscribelivetrendbarreq) message.
 2. You have to fill the message fields with the trading account ID, symbol ID, and period (time frame).
 3. Send the message, and you will receive a [ProtoOASubscribeLiveTrendbarRes](../messages/#protooasubscribelivetrendbarres) message. This means that you are now subscribed to live bars data, and you will receive [ProtoOASpotEvent](../messages/#protooaspotevent) messages.
 4. When you receive a [ProtoOASpotEvent](../messages/#protooaspotevent) message, use its trendbar field to get the last closed bar data. You have to transform the relative price to actual price by dividing the trend bar low to 100000, round the result to symbol digits. Then for getting high, open, close price levels first, add the trend bar delta level of each to low, divide each by 100000, and round the result to symbol digits.
 5. If you don't need the live bars data anymore, you can unsubscribe from it by sending a [ProtoOAUnsubscribeLiveTrendbarReq](../messages/#protooaunsubscribelivetrendbarreq) message with your subscription detail (symbol ID, period, and trading account ID). You should receive a [ProtoOAUnsubscribeLiveTrendbarRes](../messages/#protooaunsubscribelivetrendbarres) message as a response.

## Live Quotes

You can subscribe and receive live the bid/ask quotes for a symbol from the API.

To receive live quotes data follow these steps:

 1. Create a [ProtoOASubscribeSpotsReq](../messages/#protooasubscribespotsreq) message.
 2. You have to fill the message fields with the trading account ID and symbol ID.
 3. Send the message, and you will receive a [ProtoOASubscribeSpotsRes](../messages/#protooasubscribespotsres) message. This means that you are now subscribed to live quotes, and you will receive [ProtoOASpotEvent](../messages/#protooaspotevent) messages.
 4. When you receive a [ProtoOASpotEvent](../messages/#protooaspotevent) message, use its ask/bid fields to get the lastest ask/bid levels. You have to transform the relative price to actual price by dividing it to 100000 and round the result to the symbol digits. The message doesn't always have both bid/ask, it gives you the latest changed price of either bid/ask or both.
 5. If you don't need the live bars data anymore you can unsubscribe from it by sending a [ProtoOAUnsubscribeSpotsReq](../messages/#protooaunsubscribespotsreq) message with your subscription details (symbol ID and trading account ID). You should receive a [ProtoOAUnsubscribeSpotsRes](../messages/#protooaunsubscribespotsres) message.

## Depth Quotes

You can subscribe and receive live depth or Level II quotes for a symbol from the API.

To receive the market depth data follow these steps:

 1. Create a [ProtoOASubscribeDepthQuotesReq](../messages/#protooasubscribedepthquotesreq) message.
 2. You have to fill the message fields with the trading account ID and symbol ID.
 3. Send the message, and you will receive a [ProtoOASubscribeDepthQuotesRes](../messages/#protooasubscribedepthquotesres) message. This means that you are now subscribed to depth quotes, and you will receive [ProtoOADepthEvent](../messages/#protooadepthevent) messages.
 4. When you receive a [ProtoOADepthEvent](../messages/#protooadepthevent) message, use it's newQuotes/deletedQuotes fields to get the lastest market depth data. You have to transform the relative price to actual price by dividing it to 100000 and round the result to symbol digits. You also have to transform the depth quote size from cents by dividing it to 100.
 5. If you don't need the depth quotes data anymore you can unsubscribe from it by sending a [ProtoOAUnsubscribeDepthQuotesReq](../messages/#protooaunsubscribedepthquotesreq) message with your subscription detail (symbol ID and trading account ID). You should receive a [ProtoOAUnsubscribeDepthQuotesRes](../messages/#protooaunsubscribedepthquotesres) message as a response.