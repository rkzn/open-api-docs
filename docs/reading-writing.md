## Reading
To read Proto messages from API you have to follow these steps:
 
 1. Read first four bytes, that's the message length, reverse the byte array, and change it to integer
 2. Use the lenght and read that amount of bytes from stream
 3. Now you have the full message bytes, use Google Protocol Buffer SKD for your programming language to deserialize the message to [ProtoMessage](../common-messages/#protomessage)
 4. Use the [ProtoMessage](../common-messages/#protomessage) payloadType field to find the actual message type, then deserialize the payload with Google Protocol Buffer SKD to that message type

## Writing
To write your proto message to API stream follow these steps:
 
 1. Change the proto message object to byte array by using Google Protocol Buffer SKD for your programming language
 2. Get the length of byte array, change it to byte array, reverse it, write the reversed lenght byte array to stream
 3. Write the message byte array to stream

!!! note
	**The system architecture is little-endian (that is, little end first), that's why we have to reverse the byte array before reading or writting.**