# Response Header

All output responses have the following header format (Each Cell is a Byte)


| 0x0              | 0x01       | 0x02           | 0x03           | 
|:-----------------|:-----------|:---------------|:---------------|
| Protocol Version | Error Code | Transaction ID | Transaction ID |

## Format

### Protocol Version

Exchange Protocol Specified in the original [Request](../request/socket_request.md).

### Error Code

Value of `0x00` means no Error. Else see the [Error Response](./error_response.md)

### Transaction ID

Transaction ID from the original [Request](../request/socket_request.md) header.

## Additional

If the value of the Error Code is `0x00`, it's safe to assume at least 4 more bytes exist,
which may or may not contain more response information, please see the specific 
API's Spec for precise details.