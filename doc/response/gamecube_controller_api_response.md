# GameCube Controller API

## Controller Format

Many of the Operations will use the following as either input, or in their [Response](../response/gamecube_controller_api_response.md)

| 0x0                 | 0x01                | 0x02                 | 0x03                  |  
|:--------------------|:--------------------|:---------------------|:----------------------|
| Left Analog Stick X | Left Analog Stick Y | Right Analog Stick X | Right Analog  Stick Y |
| Left Trigger        | Right Trigger       | D Pad / Port         | Buttons               |

Left Analog Stick X - Byte value between 0-255
Left Analog Stick Y - Byte value between 0-255
Right Analog Stick X - Byte value between 0-255
Right Analog Stick Y - Byte value between 0-255
Left Trigger - Byte Value between 0-255
Right Trigger - Byte Value between 0 -255
D Pad - Values can be combined
- D Pad Left : 0x08
- D Pad Up : 0x04
- D Pad Right : 0x02
- D Pad Down : 0x01
Port - At Least one Specified
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80

Buttons - Values can be combined
 - A : 0x01
 - B : 0x02
 - Y : 0x04
 - X : 0x08
 - Z : 0x10
 - Start : 0x20


Example
`FF FF 00 00`</br>
`80 00 07 25`</br>

Left Analog Stick at (255,255), Right Analog stick at (0,0).
Half Pressed (128) Left Trigger, Unpressed Right Trigger.
D Pad Up, Right, and Down are pressed.
Start, Y, and A are pressed.


## Response Information

### GetCurrentPortNumberOfPoll

The `Response` Body will have the following format.

| 0x0             | 0x01 - 0x03   |
|:----------------|:--------------|
| Controller Port | Content ..... |

Controller Port - Only one value is returned.
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80

### SetInputsForPoll // Should be set inputs for port

No additional information is returned.

### GetInputsForPoll

The `Response` body is the Controller Format.

### GetInputsForPreviousFrame // QoL, specify how many controllers can be requested.

The `Response` body is a list of Controllers, in no particular order. Use the Port Number Nibble.
### IsGcControllerInPort // QoL, specify how many controllers can be requested.

The `Response` Body will have the following format.

| 0x0             | 0x01 - 0x03   |
|:----------------|:--------------|
| Controller Port | Content ..... |

Controller Port - Values are the Ports with Controllers.
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80

`0x00` for no Gamecube Controllers in Ports.
### IsUsingPort QoL, specify how many controllers can be requested.

The `Response` Body will have the following format.

| 0x0             | 0x01 - 0x03   |
|:----------------|:--------------|
| Controller Port | Content ..... |

Controller Port - Values are the Ports in use.
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80

`0x00` for no ports in use.

### Errors

If the Error Code of `0x06` is provided, the following will be appended to the Error Header.

| 0x0            | 0x01 - 0x03 | 
|:---------------|:------------|
| Sub-Error Code | Padding     |

Here are the following Sub-Error Codes

`0x01` Missing the Controller Port.


[Return to Response](./socket_response.md)