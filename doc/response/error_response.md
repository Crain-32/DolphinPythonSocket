# Error Response

If the `Error Code` of the [Response](./socket_response.md) is not `0x00`, the following apply.

Depending on the Code, more bytes might be after the `Transaction ID`. (Shocker) 
The underlying Socket will *not* disconnect on Error, see [how to use the plugin](../usage.md)

## Error Codes

The following Error Codes are defined for now.

- `0x01` : Unsupported Protocol Version
- `0x02` : Invalid API Requested
- `0x03` : Invalid API Operation Requested
- `0x04` : Invalid API Version Requested
- `0x05` : Duplicate Transaction ID
- `0x06` : Missing Request Body
- `0x07` : Reserved for MemoryAPI Errors
- `0x08` : Reserved for StatisticsAPI Errors
- `0x09` : Reserved for RegisterAPI Errors
- `0x10` : Reserved for GraphicsAPI Errors
- `0x11` : Reserved for GameCubeControllerAPI Errors
- `0x12` : Reserved for EMUApi Errors