# EMU API Requests : [Response](../response/emu_api_response.md)

## Header Information

The following values are from the Header.

- Requested API - `0x06`
- API Version - `0x01` for version `1.0`
- API Specific - Not used.

## API Operations

### Frame Advance : `0x01`

The `Request` Body will ***not*** be parsed, and the emulator will advance one frame.

### Load State : `0x02`

The `Request` Body will have the following format.

| 0x0           | 0x01           | 0x02                    | 0x03        | 
|:--------------|:---------------|:------------------------|:------------|
| Buffer Length | Requested API  | Requested API Operation | API Version |
| API Specific  | Transaction ID | Transaction ID          | Padding     |

### Save State : `0x03`

### Play Movie : `0x04`

### Save Movie : `0x05`
