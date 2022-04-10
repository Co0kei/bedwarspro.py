bedwarspro.py
==================

An asynchronous Bedwars Pro API wrapper for Python.
---------------------------------------------------------------------

This project is a fork of [hypixel.py](https://github.com/duhby/hypixel.py) by duhby.

### Installation

``` sh
pip install bedwarspro --upgrade
````

### Quick Example

``` python
import asyncio

import bedwarspro
from bedwarspro import BedwarsProException


async def main():
    """ A simple example, retrieving a player's data via a name and a UUID """
    
    client = bedwarspro.Client('api-key')

    async with client:
        try:
            player = await client.player('Co0kei')
            
            # Here you can view the raw player data returned by the API
            print(player.raw)  
            
            # Here are all the current properties for a player
            print(f'{player.first_login} {player.rank} {player.name} {player.uuid}') 

        except BedwarsProException as error:
            print(error)

    # Opening a new context will open a new aiohttp.ClientSession
    # while keeping your Client attributes
    async with client:
        try:
            player = await client.player('c2647ae1-a89f-4524-bb6c-513a709b01bf')
            print(player.raw)  

        except BedwarsProException as error:
            print(error)
        
if __name__ == '__main__':
    # If you are running python version 3.8 or higher on Windows, 
    # then you must add the following line before you start an event loop
    asyncio.set_event_loop_policy(asyncio.WindowsSelectorEventLoopPolicy())
    
    asyncio.run(main())
```