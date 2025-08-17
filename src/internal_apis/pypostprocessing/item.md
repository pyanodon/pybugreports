# Items
*As of August 16th, 2025*<br>
```lua
---@class data.ItemPrototype
---@field public add_flag fun(self: data.ItemPrototype, flag: string): data.ItemPrototype
---@field public remove_flag fun(self: data.ItemPrototype, flag: string): data.ItemPrototype
---@field public has_flag fun(self: data.ItemPrototype, flag: string): boolean
---@field public spoil fun(self: data.ItemPrototype, spoil_result: (string | table), spoil_ticks: number): data.ItemPrototype
```

## Example Usage
`ITEM` function can be used like this to create a new item:
```lua
ITEM {
  type = "item",
  name = "example-item",
  icon = "__pyexample__/graphics/icons/example.png",
  icon_size = 64,
  stack_size = 50
}
```
It can also be used like this to get an existing item:
```lua
ITEM("example-item")
```

## Item Functions
### Spoil
`@field public spoil fun(self: data.ItemPrototype, spoil_result: (string | table), spoil_ticks: number): data.ItemPrototype`
```lua
local spoil_result = "iron-plate"
local spoil_ticks = 5 * 60 -- 5 Seconds
ITEM("example-item"):spoil(spoil_result, spoil_ticks)
```

### Add Flag
`@field public add_flag fun(self: data.ItemPrototype, flag: string): data.ItemPrototype`
```lua
local flag = "placeable-by-player"
ITEM("example-item"):add_flag(flag)
```

### Remove Flag
`@field public remove_flag fun(self: data.ItemPrototype, flag: string): data.ItemPrototype`
```lua
local flag = "placeable-by-player"
ITEM("example-item"):remove_flag(flag)
```

### Has Flag
`@field public has_flag fun(self: data.ItemPrototype, flag: string): boolean`
```lua
local flag = "placeable-by-player"
local has_flag = ITEM("example-item"):has_flag(flag)
```
