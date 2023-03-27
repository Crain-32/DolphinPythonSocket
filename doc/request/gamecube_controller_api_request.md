# GameCube Controller API Requests : [Response](../response/gamecube_controller_api.md)

## Header Information

The following values are from the Header.

- Requested API - `0x05`
- API Version - `0x01` for version `1.0`

## Controller Format

Many of the Operations will use the following as either input, or in their [Response](../response/gamecube_controller_api_response.md)

| 0x0                 | 0x01                | 0x02                 | 0x03                  |  
|:--------------------|:--------------------|:---------------------|:----------------------|
| Left Analog Stick X | Left Analog Stick Y | Right Analog Stick X | Right Analog  Stick Y |
| Left Trigger        | Right Trigger       | D Pad / Port         | Buttons               |

Left Analog Stick X - Byte value between 0-255
Left Analog Stick Y - Byte value between 0-255
Right Analong Stick X - Byte value between 0-255
Right Analong Stick Y - Byte value between 0-255
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

## API Operations

### GetCurrentPortNumberOfPoll : `0x01`

The `Request` Body will ***not*** be parsed, and last controller port polled will be returned.

### SetInputsForPoll : `0x02` // Should be set inputs for port

The `Request` Body will have the Controller Format. Only ***one*** controller port ***must*** be specified.

### GetInputsForPoll : `0x03`

The `Request` Body will ***not*** be parsed, and the Controller Format of  the last polled controller is returned.

### GetInputsForPreviousFrame : `0x04` // QoL, specify how many controllers can be requested.

The `Request` Body will have the following format.

| 0x0             | 0x01 - 0x03   |
|:----------------|:--------------|
| Controller Port | Content ..... |

Controller Port - Values can be combined.
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80

### IsGcControllerInPort : `0x05`// QoL, specify how many controllers can be requested.

The `Request` Body will have the following format.

| 0x0             | 0x01 - 0x03   |
|:----------------|:--------------|
| Controller Port | Content ..... |

Controller Port - Values can be combined.
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80


### IsUsingPort : `0x06` // QoL, specify how many controllers can be requested.

The `Request` Body will have the following format.

| 0x0             | 0x01 - 0x03   |
|:----------------|:--------------|
| Controller Port | Content ..... |

Controller Port - Values can be combined.
- Port 1 : 0x10
- Port 2 : 0x20
- Port 3 : 0x40
- Port 4 : 0x80


[Return to Request](./socket_request.md)