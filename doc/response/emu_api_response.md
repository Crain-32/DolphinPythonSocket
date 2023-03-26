# EMU API

## Response Information

A successful response will include no additional information outside the normal header.

### Errors

If the Error Code of `0x12` is provided, the following will be appended to the Error Header.

| 0x0            | 0x01 - 0x03 | 
|:---------------|:------------|
| Sub-Error Code | Padding     |

Here are the following Sub-Error Codes

`0x01` The supplied file doesn't exist.