# exo-docs
* [Structs](#structs)
* [Functions](#functions)
* [Hooks](#hooks)

Thanks to nighthawk for helping with docs <3

## Structs
* [GamePacket](#gamepacket)
* [VariantList](#variantlist)
* [Vec2](#vec2)
* [Vec3](#vec3)
* [Player](#player)
* [Object](#object)
* [InventoryItem](#inventoryitem)
* [Tile](#tile)

### GamePacket
| Type | Key | Info |
|:-----|:---:|:-----|
| Number | `type` | Packet's type
| Number | `objtype` | 
| Number | `count1` |
| Number | `count2` |
| Number | `netid` | 
| Number | `item` |
| Number | `flags` | 
| Number | `float1` |
| Number | `int_data` |
| Number | `pos_x` |
| Number | `pos_y` |
| Number | `pos2_x` |
| Number | `pos2_y` |
| Number | `float2` |
| Number | `int_x` |
| Number | `int_y` |

### VariantList
| Type | Name | Description|
|:-----|:----:|:-----------|
| Any | `[0]` | Param 0 |
| Any | `[1]` | Param 1 |
| Any | `[2]` | Param 2 |
| Any | `[3]` | Param 3 |
| Any | `[4]` | Param 4 |
| Any | `[5]` | Param 5 |

### Vec2
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `x` | Position x |
| Number | `y` | Position y |

### Vec3
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `x` | Position x |
| Number | `y` | Position y |
| Number | `z` | Position z |

### Player
| Type | Name | Description|
|:-----|:----:|:-----------|
| String | `name` | Players name |
| Number | `netid` | Players netid |
| Bool | `facing_left` | Is player facing left |
| Number | `punch_speed` | Players punch speed |
| Number | `velocity_x` | Players velocity x |
| Number | `velocity_y` | Players velocity y |
| Number | `freeze_state` | Players freeze state |
| Number | `userid` | Players userid |
| String | `country` | Players flag id |
| Bool | `invis` | Is player invisible |
| Bool | `mod` | Is player mod |
| Bool | `supermod` | Is player supermod |
| Number | `bubble_state` | Players bubble state |
| Number | `state` | Players state |
| Number | `hair_color` | Players hair color |
| Number | `pupil_color` | Players pupil color |
| Number | `punch_effect` | Players punch effect |
| Number | `gravity` | Players gravity |
| Number | `acceleration` | Players acceleration speed |
| Number | `speed` | Players speed |
| Number | `water_speed` | Players speed in water |
| Number | `punch_strenght` | Players punch strenght |
| Number | `hat` | Players hat clothing |
| Number | `shirt` | Players shirt clothing |
| Number | `pants` | Players pants clothing |
| Number | `shoes` | Players shoes clothing |
| Number | `eye` | Players eye clothing |
| Number | `hand` | Players hand clothing |
| Number | `wings` | Players wings clothing |
| Number | `hair` | Players hair clothing |
| Number | `neck` | Players neck clothing |
| Number | `skin_color` | Players skin color |

### Object
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `id` | Item ID |
| Number | `index` | Object index in world |
| Number | `flags` | Object flags |
| Number | `amount` | Item amount |
| [Vec2](#vec2) | `pos` | Object position |

### InventoryItem
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `id` | Item ID |
| Number | `amount` | Item amount |
| Bool | `equipped` | Is item equipped |

### Tile
| Type | Name | Description|
|:-----|:----:|:-----------|
| Number | `fg` | Foreground block ID |
| Number | `bg` | Background block ID |
| Number | `flags` | Tile flags |
| Number | `x` | Tile position x |
| Number | `y` | Tile position y |

## Functions
* [SendPacket](#sendpacket)
* [SendPacketRaw](#sendpacketraw)
* [ProcessVariantList](#processvariantlist)
* [ProcessTankUpdatePacket](#processtankupdatepacket)
* [OnTextGameMessage](#ontextgamemessage)
* [HandleTrackPacket](#handletrackpacket)
* [LogToConsole](#logtoconsole)
* [Sleep](#sleep)
* [GetGameLogic](#getgamelogic)
* [GetLocal](#getlocal)
* [GetWorld](#getworld)
* [GetInventory](#getinventory)
* [GetCamera](#getcamera)
* [ScreenToWorld](#screentoworld)
* [WorldToScreen](#worldtoscreen)
* [GetTile](#gettile)
* [GetTiles](#gettiles)
* [GetObject](#getobject)
* [GetObjects](#getobjects)
* [GetPlayer](#getplayer)
* [GetPlayers](#getplayers)
* [GetItem](#getitem)
* [GetItems](#getitems)

### SendPacket
`SendPacket(int type, string packet)`

Sends text packet with selected type to server.

Example:
```lua
-- Sends respawn packet to server
SendPacket(2, "action|respawn")
```

### SendPacketRaw
`SendPacketRaw(GamePacket packet)`

Sends [GamePacket](#gamepacket) to server

Example:
```lua
-- Sends wear clothing packet to server
local packet = GamePacket()
packet.type = 10 
packet.int_data = 48 -- Clothing ID (Jeans)
SendPacketRaw(packet)
```
### ProcessVariantList

`ProcessVariantList(VariantList varlist, int netid, int delay)`

Description

Example:
```lua
-- No Example
```

### ProcessTankUpdatePacket

`ProcessTankUpdatePacket(GamePacket packet)`

Description

Example:
```lua
-- No Example
```

### OnTextGameMessage

`OnTextGameMessage(string text)`

Description

Example:
```lua
-- No Example
```

### HandleTrackPacket

`HandleTrackPacket(string text)`

Description

Example:
```lua
-- No Example
```

### LogToConsole

`LogToConsole(string text)`

Logs message to Growtopias console (only client side)

Example:
```lua
-- Logs "Hello World!" to Growtopias console
LogToConsole("Hello World!")
```

### Sleep

`Sleep(int ms)`

Description

Example:
```lua
-- No Example
```

### GetGameLogic

`GetGameLogic()`

Returns [GameLogic](#gamelogic) struct

Example:
```lua
-- No Example
```

### GetLocal

`GameLogic:GetLocal()`

Returns local [NetAvatar](#netavatar) struct

Example:
```lua
-- Get player's nickname and change it
local logic = GetGameLogic()
local player = logic:GetLocal()

LogToConsole(player.name)
player.name = "@blabla"
```

### GetWorld

`GameLogic:GetWorld()`

Returns 

Example:
```lua
-- Change world tile block
local logic = GetGameLogic()
local world = logic:GetWorld()
local tile = world:GetTile(45, 23)
tile.fg = 2
```

### GetInventory

`GameLogic:GetInventory()`

Returns [Inventory](#inventoryitem) struct

Example:
```lua
local logic = GetGameLogic()
local inv = logic:GetInventory()

```

### GetCamera

`GameLogic:GetCamera()`

Returns [Camera](#camera) struct

Example:
```lua
local logic = GetGameLogic()
local camera = logic:GetCamera()

```

### ScreenToWorld

`Camera:ScreenToWorld(Vec2 pos)`

Returns world coordinates of selected position

Example:
```lua
-- No Example
```

### WorldToScreen

`Camera:WorldToScreen(Vec2 pos)`

Returns screen coordinates of selected position

Example:
```lua
-- No Example
```

### GetTile

`World:GetTile(int x, int y)`

Returns world [Tiles](#tile) in selected position

Example:
```lua
-- Logs top left corners background block id
local logic = GetGameLogic()
local world = logic:GetWorld()
local tile = world:GetTile(0, 0)

LogToConsole(tile.bg)
```

### GetTiles

`World:GetTiles()`

Returns table of [Tiles](#tile)

Example:
```lua
-- Hide all foreground blocks
local logic = GetGameLogic()
local world = logic:GetWorld()

for _, tile in pairs(world:GetTiles()) do
	tile.fg = 0
end
```

### GetObject

`World:GetObject(int index)`

Returns [WorldObject](#worldobject) of selected index in world

Example:
```lua
-- No Example
```

### GetObjects

`World:GetObjects()`

Returns table of [WorldObject](#worldobject) in world

Example:
```lua
-- Change values of items in world
local logic = GetGameLogic()
local world = logic:GetWorld()

for _, object in pairs(world:GetObjects()) do
	object.amount = 200
	object.id 242 -- World Lock ID
end
```

### GetPlayer

`World:GetPlayer(int netid)`

Returns [Player](#player) of selected netid in world

Example:
```lua
-- Logs random players name in world
local logic = GetGameLogic()
local world = logic:GetWorld()
local players = world:GetPlayers()

LogToConsole(players[math.random(#players + 1) - 1].name)
```

### GetPlayers

`World:GetPlayers()`

Returns table of [Player](#player) in world

Example:
```lua
-- Logs names of players in world
local logic = GetGameLogic()
local world = logic:GetWorld()

for _, player in pairs(world:GetPlayers()) do
	LogToConsole(player.name)
end
```

### GetItem

`Inventory:GetItem(int id)`

Returns [InventoryItem](#inventoryitem) of selected id in players inventory

Example:
```lua
-- Logs amount of dirt blocks in players inventory
local logic = GetGameLogic()
local inv = logic:GetInventory()
local item = inv:GetItem(2)

LogToConsole(item.amount)
```

### GetItems

`Inventory:GetItems()`

Returns table of [InventoryItems](#inventoryitem)

Example:
```lua
-- Logs IDs of items in players inventory
local logic = GetGameLogic()
local inv = logic:GetInventory()

for _, item in pairs(inv:GetItems()) do
	LogToConsole(item.id)
end
```

### FindPattern

`FindPattern(string name, string pattern)`

No Description

```lua
-- No Example
```

### GetAddress

`GetAddress(string name)`

No Description

```lua
-- No Example
```

### PatchBytes

`PatchBytes(int address, string pattern)`

No Description

```lua
-- No Example
```


## Hooks
* [Usage](#usage)
* [Types](#types)
* [Examples](#examples)

If you return true in hook it wont execute the packet

### Usage

#### AddHook
`AddHook(string type, string name, function)`

Hooks selected function to selected [hook type](#types)

#### RemoveHook
`RemoveHook(string name)`

Removes hook with selected name

#### RemoveHooks
`RemoveHooks()`

Removes all hooks

### Types
`Packet`
Arguments: (strint packet, int type)

`ProcessVariantList`
Arguments: (VariantList varlist, int netid, int delay)

`ProcessTankUpdatePacket`
Arguments: (GamePacket packet)

`OnTextGameMessage`
Arguments: (string text)

`HandleTrackPacket`
Arguments: (string text)

### Examples

#### SendPacket
```lua
-- No Example
```

#### SendPacketRaw
```lua
-- No Example
```

#### ProcessVariantList
```lua
-- No Example
```

#### ProcessTankUpdatePacket
```lua
-- No Example
```

#### OnTextGameMessage
```lua
-- Auto Reconnect
function Reconnect()
    varlist = VariantList()
    varlist[0] = "OnReconnect"
    ProcessVariantList(varlist, -1, 0)
end

function reconnect_hook(text)
    if text:find("Too many people logging in at once.") then
        Reconnect()
    end
end

AddHook("OnTextGameMessage", "reconnect_hook", reconnect_hook)
```

#### HandleTrackPacket
```lua
-- No Example
```
