# Statistics API Response

## Response Information

### Boolean Responses

The 4 Boolean Requests "Is Recording Input", "Is Recording Input from Save State", "Is Playing Input", and "Is Movie Active".
Have the *Boolean Response* as declared below.

Against normal Convention a `Boolean` Byte will be `0x02` for `true`, and `0x01` for `false`. This is to help
visually separate them if reading the raw output, or using a parser more insane than this Author.

As such a *Boolean Response* has the following format.

| 0x0     | 0x1 - 0x3 |
|:--------|:----------|
| Boolean | Padding   |

Example <br>
`01 00 00 00` - False <br>
`02 00 00 00` - True

### Get Responses

The 7 Get Requests "Get Current Frame", "Get Movie Length", "Get Rerecord Count", "Get Current Input Count",
"Get Total Input Count", "Get Current Lag Count", and "Get Total Lag Count", have the following response.

| 0x0 - 0x3  | 
|:-----------|
| The Number |

The Number is whatever was requested "Current Frame", "Movie Length", etc.

### Errors

No Sub Errors exist in the Graphics API.

[Return to Response](./socket_response.md)