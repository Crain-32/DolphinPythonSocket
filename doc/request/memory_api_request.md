# Memory API Requests : [Response](../response/memory_api_response.md)

## Header Information

The following values are from the Header.

- Requested API - `0x03`
- API Version - `0x01` for version `1.0`

## API Operations

Note, due to the special nature of Memory, this Plugin does not expose the different Quality of Life
functions for Reading/Writing Memory. Instead, we expose a Generic Read/Write and let you do the same.
Likewise, we provide no assurance on if you've requested a Read/Write on the same memory block for the same frame.

### Read Memory : `0x01`

The `Request` Body will have the following format.

| 0x0 - 0x3      | 0x4 - 0x5 | 0x6 - 0x7 |
|:---------------|:----------|:----------|
| Memory Address | Amount    | Padding   |

- Memory Address - Virtual Memory address to read from.
- Amount - an unsigned short of the amount of bytes to read.
- Padding - Not read, solely for alignment.

Example <br>
`80 43 3A 2F` <br>
`00 05 00 00` <br> </br>
0x80433A2F - Reading from Memory Address `0x80433A2F`. <br/>
`0x0005` - Reading 5 Bytes <br/>

### Write Memory : `0x02`

The `Request` Body will have the following format.

| 0x0 - 0x3      | 0x4 - 0x5 | 0x6 - 0xN |
|:---------------|:----------|:----------|
| Memory Address | Amount    | Content   |

- Memory Address - Virtual Memory Address to start writing to.
- Amount - an unsigned short of the amount of bytes to read.
- Content - A length of bytes at least `Amount` long. If less than `Amount`
zero will be used, any bytes past amount will be ignored.
- Padding - Make sure to 4 Byte Align this Request.

Example <br>
`80 43 3A 2F` <br>
`00 05 78 61` <br> </br>
0x80433A2F - Writing to Memory Address `0x80433A2F`. <br/>
`0x0005` - Writing 5 Bytes <br/>
`0x78 0x61` - Writing `0x78` to `0x80433A2F`, `0x61` to `0x80433A30`, and `0x00` to `0x80433A31 - 0x80433A33` 


[Return to Request](./socket_request.md)