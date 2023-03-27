# DolphinPythonSocket
Python Script to be run on Dolphin's new Scripting Version, allows external access to Dolphin Scripts.


## Documentation

Documentation on the following is Available. 

- [Usage/Notes](./doc/usage.md)
- [Dolphin's Scripting Model](./doc/dolphin_script_model.md)
- [Requests](./doc/request/socket_request.md)
- [Response](./doc/response/socket_response.md)

Note that all operations are so small and structured due to the desire to have this be as fast as possible. This 
translation layer is happening in Python, potentially at dealing with multiple exchanges on a 16~ ms interval, and is
using standard libraries for maximum compatibility. I don't want to consume JSON, as tempting as it is.