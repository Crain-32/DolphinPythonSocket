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

| 0x0            | 0x01          | 0x0N % 4 = 0 | 
|:---------------|:--------------|:-------------|
| Content Length | Content ..... | Padding      |

- Content Length - Length of the following Content Stream in Bytes, with the Padding
- Content - UTF-8 Encoded String of the absolute Path to the `.sav` file.
  - File Extension is ***REQUIRED***
- Padding - 0x00 Padding to ensure that the request body is 4 Byte aligned.

Example <br>
`0F 43 3A 2F` <br>
`2F 45 78 61` <br>
`6D 70 6C 65` <br>
`2E 73 61 76` <br>
0x0F - 15 Bytes of Content, which was `C://Example.sav`.

As this Request Body was 16 bytes total, no additional padding was required.

### Save State : `0x03`

Same Request Body as `Load State`, but saving to the file instead of loading from it.

### Play Movie : `0x04`

The `Request` Body will have the following format.

| 0x0            | 0x01          | 0x0N % 4 = 0 | 
|:---------------|:--------------|:-------------|
| Content Length | Content ..... | Padding      |

- Content Length - Length of the following Content Stream in Bytes, with the Padding
- Content - UTF-8 Encoded String of the absolute Path to the `.dtm` file.
  - File Extension is ***REQUIRED***
- Padding - 0x00 Padding to ensure that the request body is aligned.

Example <br>
`0F 43 3A 2F` <br> 
`2F 45 78 61` <br>
`6D 70 6C 65` <br>
`2E 64 74 6D` <br>
0x0F - 15 Bytes of Content, which was `C://Example.dtm`.

### Save Movie : `0x05`

Same Request Body as `Load Movie`, but saving to the file instead of loading from it.


[Return to Request](./socket_request.md)