# Protocol Buffers

Protocol buffers or Protobuf is language- and platform-neutral, extensible mechanism for serializing structured data, a way of encoding structured data in an efficient yet extensible format.

You define how you want your data to be structured once, then you use special generated source code to easily write and read your structured data to and from a variety of data streams and using a variety of languages.

You specify how you want the information you're serializing to be structured by defining protocol buffer message types in .proto files.

Each protocol buffer message is a small logical record of the information, containing the series of name-value pairs.

Here's a very basic example of a .proto file that defines a message containing information about a person:

```
message Person {

    required string name = 1;  
    required int32 id = 2;  
    optional string email = 3;  


    enum PhoneType {  
        MOBILE = 0;  
        HOME = 1;  
        WORK = 2;  
    }  

    message PhoneNumber {  
       required string number = 1;  
       optional PhoneType type = 2 [default = HOME];  
    }  

    repeated PhoneNumber phone = 4;  
}
```

As you can see, the message format is simple - each message type has one or more uniquely numbered fields, and each field has a name and a value type, where value types can be numbers (integer or floating-point), booleans, strings, raw bytes, or even (as in the example above) other protocol buffer message types, allowing you to structure your data hierarchically.

You can find more information about writing .proto files in the [Protocol Buffer Language Guide](https://developers.google.com/protocol-buffers/docs/proto).

Once you've defined your messages, you run the protocol buffer compiler for your application's language on your .proto file to generate data access classes.

These provide simple accessors for each field (like name() and set_name()) as well as methods to serialize/parse the whole structure to/from raw bytes - so, for instance, if your chosen language is C++, running the compiler on the above example will generate a class called Person.

You can then use this class in your application to populate, serialize, and retrieve Person protocol buffer messages.

Learn more about the Protocol Buffers [here](https://developers.google.com/protocol-buffers/docs/overview).

!!! note
    Open API uses Protocol Buffers version 2 syntax, you can use the latest version of Protocol Buffers compiler/SDKs as they are backward compatible and work with both version 2 and 3 message files.

## ProtoMessages

The network communication in Open API 2.0 is performed by means of ProtoMessage objects - the protobuf messages designed by Spotware.

In order to deal with the network fragmentation we will send messages to the network using the following frame structure:

```
 +--------------------------+-----------------------------------------+  
 | Message Length (4 bytes) | Serialized ProtoMessage object (byte[]) |  
 +--------------------------+-----------------------------------------+  
                            |<---------- Message Length ------------->|
```

ProtoMessage has the following structure:

```
 +----------------------+  
 | int32 payloadType    |  
 | byte[] payload       |  
 | string clientMsgId   |  
 +----------------------+
```

It contains 2 mandatory fields:

* **payloadType**: Contains the ProtoPayloadType ID, This field tells us what is the type of the protobuf object serialized in the second field.
* **payload**: Serialized protobuf message that corresponds to payloadType.

And an optional field:

* **clientMsgId**: Request message ID, assigned by the client that will be returned in the response.

The actual ProtoMessage definition looks as follows:

```
message ProtoMessage {  
required uint32 payloadType = 1; //Contains ID of the ProtoPayloadType or other
custom PayloadTypes (e.g. ProtoCHPayloadType).  
optional bytes payload = 2; //Serialized protobuf message that corresponds to
the payloadType  
optional string clientMsgId = 3; //The request message ID, assigned by the
client that will be returned in the response.  
}
```

!!! note
    The system architecture is little-endian (that is, little end first), you must reverse the byte array you want to read or write.

### Naming Convention

All messages could be divided into the Request messages, Response messages, Event messages, and Model messages:

#### Request

Request messages are used for sending requests to the server, example:

```
ProtoAuthReq
```

Where Req means request command message

#### Response

Response messages are used to receive data back from the server, example:

```
ProtoAuthRes
```

Where Res means response command message.

#### Event

Event messages are used for notifying subscribers with asynchronous messages.

The classic example is ping command, its proto class name is ProtoPingEvent.

The naming convention of events is ProtoEventNameEvent.

#### Model

Model messages describe entities that participate in the Server domain model.

Naming conventions of the Model messages is ProtoEntityName, example:

```
ProtoOrder

ProtoUser

ProtoPosition
```

## Compiling Protobuf Classes

Protobuf is the flexible and automated solution designed to simplify the serializing and retrieving structured data. 

With protocol buffers, you write a .proto description of the data structure you wish to store.

From that, the protocol buffer compiler creates a class that implements automatic encoding and parsing of the protocol buffer data with an efficient binary format.

The generated class provides getters and setters for the fields that make up a protocol buffer and takes care of the details of reading and writing the protocol buffer as a unit.

Importantly, the protocol buffer format supports the idea of extending the format over time in such a way that the code can still read data encoded with the old format.

You can download the latest version of Open API Protocol Buffers message files from [**here**](https://github.com/spotware/Open-API-2.0-protobuf-messages).

After you downloaded the message proto files, extract them, and use latest available version of Google Protocol Buffers for your operating system to compile it.

You can download the latest version of Google Protocol Buffers from [here](https://github.com/protocolbuffers/protobuf/releases).

To compile the message files use the Google Protocol Buffers [tutorial](https://developers.google.com/protocol-buffers/docs/tutorials) for your programming language that you want to use.

!!! note
    The system architecture is little-endian (that is, little end first), you must reverse the byte array you want to read or write.

## Endpoints

Open API 2.0 utilizes Spotware's Proxy Cloud to ensure fast and smooth operation of your application.

Currently the following proxies are available for Open API:

**For accessing Demo accounts:**

```
demo.ctraderapi.com:5035
```
**For accessing Live accounts:**

```
live.ctraderapi.com:5035
```

### Limitations
The endpoints are subject to the following limitations:

 * 50 requests per second per application for non historical data requests.
 * 5 requests per second per application for historical data requests.
 * 25 concurrent connections per application.