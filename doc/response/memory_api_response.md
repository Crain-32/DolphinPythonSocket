# Memory API

## Response Information

### Read Memory

The `Response` Body will have the following format.


| 0x0 - 0x3      | 0x4 - 0x5 | 0x6 - ... |
|:---------------|:----------|:----------|
| Memory Address | Amount    | Values    |

Memory Address - The Virtual Memory Address read from.
Content Length - The unsigned short of how much data was requested.
Values - Byte Array of length `Content Length` of the returned value.

### Write Memory

A successful response will include no additional information outside the normal header.

### Errors

If the Error Code of `0x08` is provided, the following will be appended to the Error Header.

| 0x0            | 0x01 - 0x03 | 
|:---------------|:------------|
| Sub-Error Code | Padding     |

Here are the following Sub-Error Codes

`0x01` Out of Bounds Exception, the requested Memory Address is not in the emulated memory. 
// Not 100% how to test for that. Requested a Memory Range Feature in the Scripting PR.


[Return to Response](./socket_response.md)