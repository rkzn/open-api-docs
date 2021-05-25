## What you need?

You have to be able to convert one currency value to another for calculating a trading account positions profit/loss, a trading account deposit currency can be any currency, and you must be able to convert the profit/loss of a position to the account currency otherwise your user will have hard time to figure out the exact amount of his return from his trades.

## Forex Symbols

A Forex symbol is made up of two different currencies, one is base currency and the other one is quote currency, for example EURUSD, here EUR is base currency and USD is the quote currency, and the current price of EURUSD gives you the amount of USD that is equal to 1 EUR.

## Symbol Tick/Pip Size

The Tick is the lowest amount that a symbol price can change, each broker or symbol can have different Tick values

The Pip is X amount of Ticks.

### Calculating a Symbol Tick/Pip Size

To get the amount/size of a symbol Tick/Pip follow these steps:

 1. Get the symbol full data ([ProtoOASymbol](../models/#protooasymbol)) by sending a [ProtoOASymbolByIdReq](../messages/#protooasymbolbyidreq) message, you have to populate the message with symbol and trading account IDs
 2. After sending the request message you will receive a [ProtoOASymbolByIdRes](../messages/#protooasymbolbyidres) message, use the response message symbol field to get the symbol model
 3. The symbol model has a digits field, the Tick size is 1 over 10 to power of symbol digits or mathematically 1 / Pow(10, digits)
 4. The symbol model has a pipPosition field, the symbol Pip size is 1 over 10 to power of symbol pipPosition or mathematically 1 / Pow(10, pipPosition)
 5. Now you have both symbol Tick and Pip size

## Symbol Tick/Pip Value

The Tick value is the monetary value of one Tick of a symbol, or the monetary value of lowest amount of price change for 1 unit volume.

The Pip value is the monetary value of one Pip of a symbol for 1 unit volume.

### Calculating a Symbol Tick/Pip value

Calculating a symbol Tick/Pip value is a bit tricky because its not fixed like Tick/Pip size, it keeps changing based on currency conversion rates, and you have to use the latest currency conversion rates to calculate it.

If a symbol quote currency is the same as the account deposit currency then the symbol Tick value is equal to its Tick size.

You have to have all the trading account symbols and assets data to be able to calculate a symbol Pip/Tick value and also each symbol's latest Bid/Ask prices.

To calculate a symbol Tick value when the symbol quote currency is not same as account deposit currency follow these steps:

 1. Find the conversion symbol, it's the symbol that we will use for converting the price, for this we will use API assets and asset IDs
 2. The conversion symbol is the symbol that its base currency (asset ID) or quote currency (asset ID) is same as our symbol quote currency (asset ID), and its base currency (asset ID) or quote currency (asset ID) is same as trading account deposit currency (asset ID)
 3. Iterate over all of the account symbols data and find the conversion symbol based on above instruction
 4. If the account deposit currency (asset ID) is same as conversion symbol base currency (asset ID) then the Tick value is our symbol Tick size divided by conversion symbol current price
 5. If the account deposit currency (asset ID) is not same as conversion symbol base currency (asset ID) then Tick value is product of our symbol Tick size and conversion symbol current price

Now you have the symbol Tick value, what about Pip value? to get Pip value we multiply the Tick value to the product of symbol Pip size divided by symbol Tick size:

```
pipValue = tickValue * (pipSize / tickSize)
```

You can use a symbol Pip/Tick value for calculating positions profit/loss or risk management.

## Calculating a Position Profit/Loss

Now let's try to calculate a position profit/loss, for example we have a buy EURUSD position, the volume is 0.01 lots or 1000 units, the position entry is at 1.20345, and the current price of EURUSD is 1.19654.

Lets first find how much is the position return, to do that we subtract the entry  price from current price, if it was a sell position we would subtract current price from entry  price:

```
return = current price - entry price
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

