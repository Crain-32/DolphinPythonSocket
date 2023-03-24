# Dolphin's Scripting Model

More documentation can be found (here) [Add Link once Dolphin has a link], this is cover the parts of the
Scripting Model we care about in this Socket, and hopefully help explain some limitations we have in the Plugin.

## Event Callbacks

Dolphin's Internal Scripting is Event-Callback based, and for ease of use we'll
primarily focus on the following event.

- `OnFrameStart`

The following Events are supported by Dolphin, with potential support in future versions of the Plugin.    

- `OnGCControllerPolled`
- `OnInstructionHit`
- `OnMemoryAddressRead`
- `OnMemoryAddressWrite`
- `OnWiiInputPolled`

## APIs

The following APIs are available in Dolphin and most have full support in this Plugin. For more information on how to use
these, check out the [Request Protocol](./request/socket_request.md) and [Response Protocol](./response/socket_response.md)

### BitAPI - No Support

Performs various Bit Operations on inputs. (Local emulation is currently recommended)

### [EmuAPI](./request/emu_api_request.md) - Full Support

Provides control over a Save State, the running TAS Movie, and Advancing Frames.

### [GameCubeControllerAPI](./request/gamecube_controller_api_request.md) - Full Support

Check Inputs for specifics frames, currently polling inputs, or controller amount.

### [GraphicsAPI](./request/graphics_api_request.md) - Partial Support

The only support this Plugin provides is to write an overlay on the Screen. 
(This is a limitation of the Developer, feel free to create a PR and improve this)

### [MemoryAPI](./request/memory_api_request.md) - Full Support

Read/Write Access to the MEM1 and MEM2 Address Space

### [RegistersAPI](./request/registers_api_request.md) - Full Support

Read/Write Access to a subset of registers

### [StatisticsAPI](./request/statistics_api_request.md) - Full Support

Get basic information on the current Movie.

## Multi-Script Support

Although Dolphin's Scripting model supports multiple scripts running in parallel, for your own sanity this
Plugin recommends to be run solo.

If you've found a limitation in the Plugin that the Dolphin Scripting Model supports, feel free to raise an issue.  