# Entity
*As of August 16th, 2025*<br>
```lua
---@class data.EntityPrototype
---@field public standardize fun(self: data.EntityPrototype): data.EntityPrototype
---@field public add_flag fun(self: data.EntityPrototype, flag: string): data.EntityPrototype
---@field public remove_flag fun(self: data.EntityPrototype, flag: string): data.EntityPrototype
---@field public has_flag fun(self: data.EntityPrototype, flag: string): boolean
```

## Example Usage
`ENTITY` function can be used like this to create a new entity:
```lua
ENTITY {
  type = "assembling-machine",
  name = "example-entity",
  icon = "__pyexample__/graphics/icons/example.png",
  icon_size = 64,
  ...
}
```
It can also be used to get an existing entity:
```lua
ENTITY("example-entity")
```

## Entity Functions
### Add Flag
`@field public add_flag fun(self: data.EntityPrototype, flag: string): data.EntityPrototype`
```lua
local flag = "placeable-by-player"
ENTITY("example-item"):add_flag(flag)
```

### Remove Flag
`@field public remove_flag fun(self: data.EntityPrototype, flag: string): data.EntityPrototype`
```lua
local flag = "placeable-by-player"
ENTITY("example-item"):remove_flag(flag)
```

### Has Flag
`@field public has_flag fun(self: data.EntityPrototype, flag: string): boolean`
```lua
local flag = "placeable-by-player"
local has_flag = ENTITY("example-item"):has_flag(flag)
```
