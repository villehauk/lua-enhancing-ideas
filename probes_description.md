.probes

.probes = primal object emitting stream

`description`: a .probes file will be the input, listener or anything related
it will be native to lua, but other languages might use it as well.

`objective`: the .probe files will be actively listening to impulses in ports, folders, peripherals,
files and so on.
or even the internet. Those impulses will be probed, readed and things might happen

`enhancements`: use C for functions

`advantages`: almost no advantage, but I want it to be faster and optimal than any javascript or any
python module and also make it easy to configure. It might be used to create modularized programs
more easily and modularize data.

also, it might be used in parallel programming to solve clashing problems
and to make multiple things at once


`how they work`: in a .probes file, you create the probe. The more probes a .probes file have, the
slower it will act because it has a fixed number of calls per second.
Each time it gather information, it will send files in .satlite format to the probe pushdata

the receiving end file will be a .lua script.

in the .probes file
it might be used as so:

```lua
local probe1 = probe()
setmetatable(probe1,"keyboardprobe")

probe1.pulselisten(keyboard["k"])

probe1.pushdata()

local probe2 = probe()
setmetatable(probe2,"folderprobe")
probe2.listen("newfilecreation")

probe2.pushdata()
```

-- in the .lua script
-- it might be used as so:
```lua

local probes = require "luaprobeslib"
local lods = require "satlitelib"

local t1 = probes.activate("./probes/probe1.probes")

local t2 = probes.activate("./probes/probe2.probes")
```
-- in a .c or .cpp file
-- it might be used as so:
```c
#include <luaprobeslib.h>
#include <satlitelib.h>
```
