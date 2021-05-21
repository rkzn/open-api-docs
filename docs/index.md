# Getting Stared

This is the Spotware Open API documentation, here you can find everything you need for working with Open API.

## What's Open API?

Open API is part of cTrader package which is available for all cTrader brokers, it allows third party developers to develop Apps or services for cTrader users and integrate cTrader on their platforms.

It uses [Google Protocol Buffers](https://developers.google.com/protocol-buffers) for sending and receiving messages, it allows you to use any programming language you are familiar with to interact with the API.

## Version 2.0

The Open API 2.0 is the new version of the publicly available Protobuf-based API developed by Spotware.

It allows third-party service providers to integrate additional tools and applications for trading and analysis with the data and functionality from Spotware platform by getting all the required cTID data, market data and performing all possible trading operations on behalf of other cTrader users.

Unlike the Open API version 1.0, which was using a different protocol for each scope (REST and Protocol Buffers), the Open API 2.0 is designed to use solely protocol buffers.

Now by using Protocol Buffers you can retrieve accounts information, market data, and trading data. The API is open for everyone with no restrictions ([Terms of Use](/terms-of-use/)) and it is supported by all trading accounts of any cTrader supported brokers.

## Environments

Open API is available in both Demo and Live environments. We recommend using Demo accounts first and then switch to Live, after you make sure your integration works correctly. But you can use the Live version right away as well on your own risk.
