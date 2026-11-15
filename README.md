# Growtopia Item ID Database (Lucifer v2.88 Validated)

Database seluruh ID item Growtopia yang valid, akurat, dan lengkap diekstrak langsung dari database Lucifer v2.88.

- **Total Unique Items**: 16.480 items
- **Format File**: `Nama Item = ID`
- **Tervalidasi**: Termasuk item Air Vent (2810), Soil (8772), dsb.

## Cara Baca Database di Lua
```lua
local itemDB = {}
local function loadItemDatabase(filePath)
    local f = io.open(filePath, "r")
    if not f then return false end
    for line in f:lines() do
        local name, id = line:match("^([^=]+)%s*=%s*(%d+)$")
        if name and id then
            name = name:gsub("^%s+", ""):gsub("%s+$", "")
            itemDB[name] = tonumber(id)
            itemDB[tonumber(id)] = name
        end
    end
    f:close()
    return true
end
```
