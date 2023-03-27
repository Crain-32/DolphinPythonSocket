# Graphics API Requests : [Response](../response/graphics_api_response.md)

## Header Information

The following values are from the Header.

- Requested API - `0x04`
- API Version - `0x01` for version `1.0`

## API Operations

### Draw Text : `0x01` // TODO figure out how long to persist the overlay.

The `Request` Body will have the following format.

| 0x0            | 0x01          | 0x0N % 4 = 0 | 
|:---------------|:--------------|:-------------|
| Content Length | Content ..... | Padding      |

- Content Length - Length of the following Content Stream in Bytes, with the Padding
- Content - UTF-8 Encoded String to be displayed on the screen.
  - LF is the universal New Line Character
- Padding - 0x00 Padding to ensure that the request body is 4 Byte aligned.
69
120
97
109
112
108
101

Example <br>
`07 45 78 61` <br>
`6D 70 6C 65` <br>
`0x07` - 7 Bytes of Content, which was `Example`.

As this Request Body was 8 bytes total, no additional padding was required.


[Return to Request](./socket_request.md)