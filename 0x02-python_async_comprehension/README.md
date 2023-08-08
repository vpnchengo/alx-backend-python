﻿
# 0x02. Python - Async Comprehension


![](https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/medias/2019/12/ee85b9f67c384e29525b.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20230808%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230808T063714Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=2ae2c9d2ef739fb9dba0b71a912eb44eed01d9008957701e467c8065605f68e5)

## Resources

-   [PEP 530 – Asynchronous Comprehensions](https://peps.python.org/pep-0530/)
-   [What’s New in Python: Asynchronous Comprehensions / Generators](https://www.blog.pythonlibrary.org/2017/02/14/whats-new-in-python-asynchronous-comprehensions-generators/)
-   [Type-hints for generators](https://stackoverflow.com/questions/42531143/how-to-type-hint-a-generator-in-python-3)

## Learning Objectives

-   How to write an asynchronous generator
-   How to use async comprehensions
-   How to type-annotate generators



### [0. Async Generator](https://github.com/vpnchengo/alx-backend-python/blob/main/0x02-python_async_comprehension/0-async_generator.py)

Write a coroutine called  `async_generator`  that takes no arguments.

The coroutine will loop 10 times, each time asynchronously wait 1 second, then yield a random number between 0 and 10. Use the  `random`  module.

```
bob@dylan:~$ cat 0-main.py
#!/usr/bin/env python3

import asyncio

async_generator = __import__('0-async_generator').async_generator

async def print_yielded_values():
    result = []
    async for i in async_generator():
        result.append(i)
    print(result)

asyncio.run(print_yielded_values())

bob@dylan:~$ ./0-main.py
[4.403136952967102, 6.9092712604587465, 6.293445466782645, 4.549663490048418, 4.1326571686139015, 9.99058525304903, 6.726734105473811, 9.84331704602206, 1.0067279479988345, 1.3783306401737838]

```

### [1. Async Comprehensions](https://github.com/vpnchengo/alx-backend-python/blob/main/0x02-python_async_comprehension/1-async_comprehension.py)

Import  `async_generator`  from the previous task and then write a coroutine called  `async_comprehension`  that takes no arguments.

The coroutine will collect 10 random numbers using an async comprehensing over  `async_generator`, then return the 10 random numbers.

```
bob@dylan:~$ cat 1-main.py
#!/usr/bin/env python3

import asyncio

async_comprehension = __import__('1-async_comprehension').async_comprehension


async def main():
    print(await async_comprehension())

asyncio.run(main())

bob@dylan:~$ ./1-main.py
[9.861842105071727, 8.572355293354995, 1.7467182056248265, 4.0724372912858575, 0.5524750922145316, 8.084266576021555, 8.387128918690468, 1.5486451376520916, 7.713335177885325, 7.673533267041574]


```

### [2. Run time for four parallel comprehensions](https://github.com/vpnchengo/alx-backend-python/blob/main/0x02-python_async_comprehension/2-measure_runtime.py)

Import  `async_comprehension`  from the previous file and write a  `measure_runtime`  coroutine that will execute  `async_comprehension`  four times in parallel using  `asyncio.gather`.

`measure_runtime`  should measure the total runtime and return it.

Notice that the total runtime is roughly 10 seconds, explain it to yourself.

```
bob@dylan:~$ cat 2-main.py
#!/usr/bin/env python3

import asyncio


measure_runtime = __import__('2-measure_runtime').measure_runtime


async def main():
    return await(measure_runtime())

print(
    asyncio.run(main())
)

bob@dylan:~$ ./2-main.py
10.021936893463135


```



## Author

-   [alvin](https://github.com/vpnchengo)