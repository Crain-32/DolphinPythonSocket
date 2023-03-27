# Registers API Response

## Response Information

All "Write" Operations will return nothing in the `Response` Body.

### Read Operations

| 0x0 - 0x3 | 0x3 - 0x7 |
|:----------|:----------|
| Value     | Extension |

Value - the first 32 bits of the Register.
Extension - Additional 32 bits if the Register Supports 64 bit operations. 

### Errors

If the Error Code of `0x10` is provided, the following will be appended to the Error Header.

| 0x0            | 0x01 - 0x03 | 
|:---------------|:------------|
| Sub-Error Code | Padding     |

Here are the following Sub-Error Codes

`0x01` Invalid Type Request, the Requested Write/Read Size is not supported by the Register.


[Return to Response](./socket_response.md)