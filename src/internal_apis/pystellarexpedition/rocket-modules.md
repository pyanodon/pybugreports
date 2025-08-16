# Rocket Modules
*As of August 16th, 2025*

## Data

We define the equipment grid and the equipment category and the equipment grid proxy which is just an invisible car.

Then we can create our equipments with custom definition and with some prefilled in stuff to help. We store the equipment size and equipment name in a global variable for use later. Then we can define the equipment, each equipment is essentially a dummy. We define an item, a `battery-equipment`, and a recipe for each using the `create_equipment` function.

`create_equipment` looks like this:
```lua
--- @param definition ItemEquipmentRecipeHybrid
---
--- @class ItemEquipmentRecipeHybrid
--- @field name string
--- @field icon string|nil
--- @field icon_size number|nil Default size is 64
--- @field stack_size number|nil Default size is 10
--- @field shape table
--- @field hidden bool|nil
--- @field categories string[] The categories of the equipment
--- @field category string The recipe category
--- @field ingredients table|nil
--- @field results talbe|nil
local function create_equipment(definition)
  -- ...
end
```
`definition` is a mixture of item, equipment and recipe prototype. Example:
```lua
create_equipment{
  name = "lander",
  icon = "__pystellarexpeditiongraphics__/graphics/icons/lander-module.png",
  icon_size = 64,
  categories = {"rocket-silo-equipment"},
  stack_size = 1,
  shape = {
    width = 2,
    height = 2,
    type = "full"
  },
}
```

After we defined equipment we can now define the rocket part recipes for them using the local `iterate_counts` function. Which has this definition:
```lua
--- Creates a loop like this:
--- a: 1, b: 0, c: 0
--- a: 2, b: 0, c: 0
--- a: 3, b: 0, c: 0
--- a: 0, b: 1, c: 0
--- a: 1, b: 1, c: 0
--- Essentially binary counting
--- @param labels string[]
--- @param max number
--- @param print_func fun(row: table<string, number>) A table of labels and numbers
--- @param include_zero bool Whether to include zeros in the print_func row param
local function iterate_counts(labels, max, print_func, include_zero)
  -- ...
end
```
We use this function to create every possible `rocket-part` recipe and trim out some that can't exist using `get_size`
```lua
--- Gets the size of an equipment
--- @param name string
local function get_size(name)
  -- ...
end
```
This uses one of the globals we talked about earlier.

### Problems with get_size and trimming
Currently we're doing it stupidly which means just not really trimming anything which leads with lots of impossible recipes. This isn't necessarily bad but still doesn't feel good.

I think implementing: [https://en.wikipedia.org/wiki/Knuth's_Algorithm_X](https://en.wikipedia.org/wiki/Knuth%27s_Algorithm_X), Would be a great step in the right direction.

`get_size` also doesn't account for custom shapes which we will have in the future.

## Control

### WIP
