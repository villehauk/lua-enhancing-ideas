Lunar object data serialization (.lods, .probe, .satlite) -- ideas --

.probe = this might be another thing

.satlite = serialized acknowledgement tables lite

{{ metatable declarations }}

```lua
function instanciate(tab,values)
  local values = values or {}
  local object = {}
  for key,value in pairs(tab) do
    object[key] = values[key] or tab[key]
  end
  setmetatable(object,tab)
  return object
end

function applyheirloom(tab)
  tab.__index = tab
end

-- metatables.lods

local firstmetatable = {
  [1] = 30
}
applyheirloom(firstmetatable)

local secondmetatable = {
  [1] = instanciate(firstmetatable),
  [2] = instanciate(firstmetatable),
  [3] = 3
}

print(secondmetatable[1][1])
```
