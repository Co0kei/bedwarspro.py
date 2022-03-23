bedwarspro.py
==================

An asynchronous Bedwars Pro API wrapper for Python.
---------------------------------------------------------------------

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
    client = bedwarspro.Client('api-key')

    async with client:
        try:
            player = await client.player('Co0kei')
            print(player.raw)  # the raw player data
            print(f'[{player.first_login}] [{player.rank}] {player.name} {player.uuid}')  # here are all the current properties for a player

        except BedwarsProException as error:
            print(error)

if __name__ == '__main__':
    # If you are running python version 3.8 or higher on Windows, then you must add the following line before you start an event loop
    asyncio.set_event_loop_policy(asyncio.WindowsSelectorEventLoopPolicy())
    
    asyncio.run(main())
```