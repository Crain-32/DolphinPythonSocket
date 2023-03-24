# Request Header

All inbound requests must have the following header format (Each Cell is a Byte)


| 0x0              | 0x01           | 0x02                    | 0x03        | 
|:-----------------|:---------------|:------------------------|:------------|
| Protocol Version | Requested API  | Requested API Operation | API Version |
| API Specific     | Transaction ID | Transaction ID          | Padding     |

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

### Api Specific

Reserved for the API Spec to use.

### Transaction ID

Two bytes used to coordinate the [response](../response/socket_response.md) back to the client.

### Padding

This byte is ignored, but `0x00` is recommended.


## Example Header

`01 02 XX 01` </br>
`XX 31 21 23`