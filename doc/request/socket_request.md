# Request Header

All inbound requests must have the following header format (Each Cell is a Byte)


| 0x0              | 0x01           | 0x02                    | 0x03        | 
|:-----------------|:---------------|:------------------------|:------------|
| Protocol Version | Requested API  | Requested API Operation | API Version |
| Reserved     | Transaction ID | Transaction ID          | Padding     |

## Format

### Protocol Version

This dictates the expected header format.

### Requested API

Each API can be specified using the following values.

- MemoryAPI - `0x01`
- StatisticsAPI - `0x02`
- RegisterAPI - `0x03`
- GraphicsAPI - `0x04`
- GameCubeControllerAPI - `0x05`
- EMUApi - `0x06`

### Requested API Operation

Dictates the expected Data format after the header, see each specific API's request format for more information.

### API Version (Optional)

Specifics the API version to use based on each API's spec, if `0x00` we assume to use the Latest. ***This is not recommend!***

### Reserved

Reserved for potential future use.

### Transaction ID

Two bytes used to coordinate the [response](../response/socket_response.md) back to the client. 
Must be non-zero. Attempting to register multiple requests with the same Transaction ID will fail. 

### Padding

This byte is ignored, but `0x00` is recommended.


## Example Header

`01 02 05 01` </br>
`00 31 21 23` </br>
Breakdown
- `0x01` : Protocol Version 1
- `0x02` : Statistics API Requested
- `0x05` : Get Current Frame
- `0x01` : API Version 1.0
- `0x00` : Statistics API doesn't use this field for Get Current Frame.
- `0x31 0x21` : Transaction ID of `0x3121`
- `0x23` : Non-Zero Padding.