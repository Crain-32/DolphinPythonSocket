# Register API Requests : [Response](../response/registers_api_response.md)

## Header Information

The following values are from the Header.

- Requested API - `0x03`
- API Version - `0x01` for version `1.0`

## API Operations

### Read from Register : `0x01`

| 0x0 - 0x2 | 0x3     |
|:----------|:--------|
| Register  | Padding |

Register - 3 Bytes that will be UTF-8 Encoded into a String.

Available Registers
- R : 0-31
- F : 0-31
- PC
- LR

Example
`52 31 00 00`<br>
Read from Register `R1`

### Write to Register : `0x02`

The `Request` Body will have the following format.

| 0x0 - 0x2 | 0x3        | 0x4 - 0x7 or 0x4 - 0xA |
|:----------|:-----------|:-----------------------|
| Register  | Write Type | Content                |

Register - 3 Bytes that will be UTF-8 Encoded into a String.
Write Type - Correlates to the following Write Operations.
- `0x01` : Write U8 to Register
- `0x02` : Write U16 to Register
- `0x03` : Write U32 to Register
- `0x04` : Write U64 to Register
- `0x05` : Write Float to Register
- `0x06` : Write Double to Register

Content : Bytes `0x4-0x7` are read for all types. Bytes 0x8-0xA are required for `0x04` and `0x06`, otherwise ignored. 

Available Registers
- R : 0-31
- F : 0-31
- PC
- LR

Example
`52 31 00 04`<br>
`00 00 00 82`
`00 00 00 12`
Write the U64 `00 00 00 82 00 00 00 12` to Register `R1`

