## What you need?

One of the most common tasks you will need to implement in an Open API application is the calculation of the current positions P&L.

To achieve this, you need to be able to convert values between different currencies.

This is a tedious task and this tutorial will walk you through this process.

## Symbols

Any symbol is made up of two different assets, one is base asset and the other one is quote asset.

For example EURUSD, EUR is base asset and USD is the quote asset.

The quote price of EURUSD gives you the amount of USD that is equal to 1 EUR.

## Symbol Tick/Pip Size

A Tick is the lowest amount that a symbol price can change.

Each broker or symbol can have different Tick values.

A Pip is X amount of Ticks, usually Pips are larger than ticks. For example 1 Pip of EURUSD can be 10 Ticks.

### Calculating a Symbol's Tick/Pip Size

To get the amount/size of a symbol Tick/Pip follow these steps:

 1. Get the symbol full data ([ProtoOASymbol](../models/#protooasymbol)) by sending a [ProtoOASymbolByIdReq](../messages/#protooasymbolbyidreq) message, you have to populate the message with symbol and trading account IDs.
 2. After sending the request message you will receive a [ProtoOASymbolByIdRes](../messages/#protooasymbolbyidres) message, use the response message symbol field to get the symbol model.
 3. The symbol model has a digits field, the Tick size is 1 over 10 to power of symbol digits or mathematically 1 / Pow(10, digits).
 4. The symbol model has a pipPosition field, the symbol Pip size is 1 over 10 to power of symbol pipPosition or mathematically 1 / Pow(10, pipPosition).
 5. Now you have both symbol Tick and Pip size.

## Symbol Rate Conversion

To convert a symbol rate to another symbol rate you should use the ([ProtoOASymbolsForConversionReq](../models/#protooasymbolsforconversionreq)) request message, the response of this message is a ([ProtoOASymbolsForConversionReq](../models/#protooasymbolsforconversionreq)), which contains the symbol conversion chain that you should use for converting the current rate of first Asset to last asset.

You must have the asset IDs to be able to use ([ProtoOASymbolsForConversionReq](../models/#protooasymbolsforconversionreq)), as this message has two required fields which are the first asset ID and the last asset ID.

As an example for converting the current rate of GBPJPY to trading account deposit asset which is USD we have to follow these steps:

 1. We need the conversion chain from GBPJPY quote asset which is JPY to account deposit asset which is USD, to get the conversion chain we send a ([ProtoOASymbolsForConversionReq](../models/#protooasymbolsforconversionreq)), we set the first asset to JPY asset ID and the last asset to USD asset ID.
 2. After sending the request message we will receive a ([ProtoOASymbolsForConversionRes](../models/#protooasymbolsforconversionres)), its symbol field has all the symbols that we need to use for converting JPY to USD rate.
 3. Then we have to use the returned conversion symbols to convert the JPY rate to USD, the below pseudocode might help understand better the process:

```
fromAsset = "JPY"
toAsset = "USD"

// rate will be our conversion result
rate = 1

// symbols are the ProtoOASymbolsForConversionRes symbols field
symbols[] = ProtoOASymbolsForConversionRes(fromAsset,toAsset)

asset = fromAsset 

FOR symbol in symbols:
	IF symbol.baseAsset == asset:
		rate = rate * symbol.price
		asset = symbol.quoteAsset
	ELSE:
		rate = rate * 1 / symbol.price
		asset = symbol.baseAsset
```

We recommend you to get all of the conversion chain symbols for each asset when you get the assets data, instead of sending a ([ProtoOASymbolsForConversionReq](../models/#protooasymbolsforconversionreq)) everytime you need to convert rates.

## Symbol Tick/Pip Value

The Tick value is the monetary value of one Tick of a symbol, or the monetary value of lowest amount of price change for 1 unit volume.

The Pip value is the monetary value of one Pip of a symbol for 1 unit volume.

### Calculating a Symbol's Tick/Pip value

Calculating a symbol's Tick/Pip value is a bit tricky because it's not fixed like Tick/Pip size, it keeps changing based on currency conversion rates, and you have to use the latest currency conversion rates to calculate it.

If a symbol quote currency is the same as the account deposit currency then the symbol Tick value is equal to its Tick size.

You have to have all the trading account symbols, symbols conversion chain symbols, and assets data to be able to calculate a symbol Pip/Tick value and also each symbol's latest Bid/Ask prices.

To calculate a symbol's Tick value when the symbol quote asset is not same as account deposit asset follow these steps:

 1. Converte the symbol rate to account deposit currency, to do this follow the symbol rate conversion tutorial
 2. Multiply the symbol tick size to the conversion rate

Now you have the symbol Tick value, what about Pip value? to get Pip value we multiply the Tick value to the product of symbol Pip size divided by symbol Tick size:

```
pipValue = tickValue * (pipSize / tickSize)
```

You can use a symbol Pip/Tick value for calculating positions profit/loss or risk management.

## Calculating a Position Profit/Loss

Now let's try to calculate a position profit/loss, for example we have a buy EURUSD position, the volume is 0.01 lots or 1000 units, the position entry is at 1.20345, and the quote price of EURUSD is 1.19654.

Lets first find how much is the position return, to do that we subtract the entry  price from quote price, if it was a sell position we would subtract quote price from entry  price:

```
return = quote price - entry price
```

Now we get -0.00691, which is our position return, but we don't know the monetary value of this amount of EURUSD based on our position volume.

Let's now change the return to Pips, so to change absolute price to Pips we multiply the price to 10 to power of symbol Pip Position and then we round it:

```
pips = Round(return * Pow(10, PipPosition), symbol.Digits - symbol.PipPosition)
```

The symbol Pip position is in ([ProtoOASymbol](../models/#protooasymbol)).

Now we have the number of Pips, but we still don't know the monetary value, now let's change the Pips to monetary value:

```
volume = positionVolumeMonetary / 100

grossProfit = Pips * Symbol.PipValue * volume

// You can get a position Money digits from ProtoOAPosition model via reconcile request or execution event
// Pow means Power
// Swap can be positive/negative
positionSwapMonetary = positionSwap / Pow(10, MoneyDigits)
// API gives commission in negative form
// We multiply the commission by two because we must calculate the position for both opening and closing orders of position
positionDoubleCommissionMonetary = (positionCommission * 2) / Pow(10, MoneyDigits)

netProfit = GrossProfit + positionDoubleCommissionMonetary + positionSwapMonetary
```

