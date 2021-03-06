# ultrasc
Simple python3 module for uploading images to UltraSC.tk

# OUTDATED
The response changed from `ok:<id>` to `ok:<id>.<stamp>.<key>` <br>
And moved to: https://github.com/Ultra-SC/ultra-py

## Installation
**Through pip:** <br>
`pip install git+https://github.com/DmitrijVC/ultrasc-py.git#egg=ultrasc`

**If you are using PyCharm or venv:** <br>
Open CMD in your project folder. <br>
Activate your virtual environment `.\venv\Scripts\activate` <br>
And use the same command as above  

## Client
**def \_\_init__(self, ws_host, address)**
- Desc: *Client class constructor*
- Arg [ws_host]: *web socket address*
- Arg [address]: *UltraSC address*
- Returns: *Client*
- Raises: *None*

**async def connect(self)**
- Desc: *connects to the specified WebSocket*
- Returns: *None*
- Raises: *WsConnectionError, UnhandledError*
    
**async def disconnect(self)**
- Desc: *disconnects from the specified WebSocket*
- Returns: *None*
- Raises: *None*

**async def send_reader(self, title, description, file_reader, [close])**
- Desc: *sends the image from a reader*
- Arg [title]: *image title*
- Arg [description]: *image description*
- Arg [file_reader]: *binary file reader (BinaryIO)*
- Arg [close]: *close binary file reader after use*
- Returns: *Response*
- Raises: *None*
  
**async def send_bytes(self, title, description, file_content)**
- Desc: *sends the image from it's content*
- Arg [title]: *image title*
- Arg [description]: *image description*
- Arg [file_content]: *image content as bytes*
- Returns: *Response*
- Raises: *None*
    
## Response
**def as_img(self, [static])**
- Desc: *get url to the image*
- Arg [static]: *get static file*
- Returns: *str (url or NaN)*
- Raises: *UploadError*
    
## Examle
```python
from ultrasc import Client
import asyncio


async def execute():
    client = Client()
    await client.connect()
    result = await client.send_reader("Test", "Test", open("data.png", "rb"), close=True)
    print(result.as_img(static=True))
    await client.disconnect()

asyncio.get_event_loop().run_until_complete(
    execute()
)
```
