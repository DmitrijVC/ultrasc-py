# ultrasc
Simple python3 module for uploading images to UltraSC.tk

## Installation
**Through pip:** <br>
`pip install git+https://github.com/DmitrijVC/ultrasc-py.git#egg=ultrasc`

**If you are using PyCharm or venv:** <br>
Open CMD in your project folder. <br>
Activate your virtual environment `.\venv\Scripts\activate` <br>
And use the same command as above  

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
