# Recipe
*As of version 3.0.36*<br>
```lua
---@class data.RecipePrototype
---@field public standardize fun(self: data.RecipePrototype): data.RecipePrototype
---@field public add_unlock fun(self: data.RecipePrototype, technology_name: string | string[]): data.RecipePrototype
---@field public remove_unlock fun(self: data.RecipePrototype, technology_name: string | string[]): data.RecipePrototype
---@field public replace_unlock fun(self: data.RecipePrototype, technology_old: string | string[], technology_new: string | string[]): data.RecipePrototype
---@field public replace_ingredient fun(self: data.RecipePrototype, old_ingredient: string, new_ingredient: string | data.IngredientPrototype, new_amount: integer?): data.RecipePrototype
---@field public add_ingredient fun(self: data.RecipePrototype, ingredient: data.IngredientPrototype): data.RecipePrototype
---@field public remove_ingredient fun(self: data.RecipePrototype, ingredient_name: string): data.RecipePrototype, integer
---@field public replace_result fun(self: data.RecipePrototype, old_result: string, new_result: string | data.ProductPrototype, new_amount: integer?): data.RecipePrototype
---@field public add_result fun(self: data.RecipePrototype, result: string | data.ProductPrototype): data.RecipePrototype
---@field public remove_result fun(self: data.RecipePrototype, result_name: string): data.RecipePrototype
---@field public clear_ingredients fun(self: data.RecipePrototype): data.RecipePrototype
---@field public multiply_result_amount fun(self: data.RecipePrototype, result_name: string, percent: number): data.RecipePrototype
---@field public multiply_ingredient_amount fun(self: data.RecipePrototype, ingredient_name: string, percent: number): data.RecipePrototype
---@field public add_result_amount fun(self: data.RecipePrototype, result_name: string, increase: number): data.RecipePrototype
---@field public add_ingredient_amount fun(self: data.RecipePrototype, ingredient_name: string, increase: number): data.RecipePrototype
---@field public set_result_amount fun(self: data.RecipePrototype, result_name: string, amount: number): data.RecipePrototype
---@field public set_ingredient_amount fun(self: data.RecipePrototype, ingredient_name: string, amount: number): data.RecipePrototype
---@field public get_main_product fun(self: data.RecipePrototype, allow_multi_product: bool?): LuaItemPrototype?|LuaFluidPrototype?
---@field public get_icons fun(self: data.RecipePrototype): data.IconData
```

## Example Usage
You can create a new recipe like so:
```lua
RECIPE {
  type = "recipe",
  name = "example-recipe",
  ingredients = {},
  results = {{type = "item", name = "example-item", amount = 1}}
}
```
You can also get existing recipes
```lua
RECIPE("example-recipe")
```

## Recipe Functions
### Add Unlock
`@field public add_unlock fun(self: data.RecipePrototype, technology_name: string | string[]): data.RecipePrototype`
```lua
local technology_name = "example-tech"
RECIPE("example-recipe"):add_unlock(technology_name)
```
```lua
local technologies = {"example-tech", "example-tech-2"}
RECIPE("example-recipe"):add_unlock{technologies}
```

### Remove Unlock
`@field public remove_unlock fun(self: data.RecipePrototype, technology_name: string | string[]): data.RecipePrototype`
```lua
local technology_name = "example-tech"
RECIPE("example-recipe"):remove_unlock(technology_name)
```
```lua
local technologies = {"example-tech", "example-tech-2"}
RECIPE("example-recipe"):remove_unlock{technologies}
```

### Replace Unlock
`@field public replace_unlock fun(self: data.RecipePrototype, technology_old: string | string[], technology_new: string | string[]): data.RecipePrototype`

Equivalent to `:remove_unlock(from):add_unlock(to)`
```lua
local from = "example-tech"
local to = "ultra-tech"
RECIPE("example-recipe"):replace_unlock(from, to)
```
```lua
local from = {"example-tech", "example-tech-2"}
local to = {"ultra-tech", "ultra-tech-2"} 
RECIPE("example-recipe"):replace_unlock(from, to)
```

### Add Ingredient
`@field public add_ingredient fun(self: data.RecipePrototype, ingredient: data.IngredientPrototype): data.RecipePrototype`
```lua
RECIPE("example-recipe"):add_ingredient{
  type = "item",
  name = "iron-plate",
  amount = 5
}
```

### Remove Ingredient
`@field public remove_ingredient fun(self: data.RecipePrototype, ingredient_name: string): data.RecipePrototype, integer`
```lua
RECIPE("example-recipe"):remove_ingredient("iron-plate")
```

### Replace Ingredient
`@field public replace_ingredient fun(self: data.RecipePrototype, old_ingredient: string, new_ingredient: string | data.IngredientPrototype, new_amount: integer?): data.RecipePrototype`
```lua
local from = "iron-plate"
local to = "copper-plate"
RECIPE("example-recipe"):replace_ingredient(from, to)
```
```lua
local from = "iron-plate"
local to = {
  type = "item",
  name = "copper-plate",
  amount = 5
}
RECIPE("example-recipe"):replace_ingredient(from, to)
```
```lua
local from = "iron-plate"
local to = "copper-plate"
local amount = 10
RECIPE("example-recipe"):replace_ingredient(from, to, amount)
```

### Clear Ingredients
`@field public clear_ingredients fun(self: data.RecipePrototype): data.RecipePrototype`
```lua
RECIPE("example-recipe"):clear_ingredients()
```

### Add Result
`@field public add_result fun(self: data.RecipePrototype, result: string | data.ProductPrototype): data.RecipePrototype`
```lua
RECIPE("example-recipe"):add_result{
  type = "item",
  name = "iron-plate",
  amount = 5
}
```

### Remove Result
`@field public remove_result fun(self: data.RecipePrototype, result_name: string): data.RecipePrototype`
```lua
RECIPE("example-recipe"):remove_result("iron-plate")
```

### Replace Result
`@field public replace_result fun(self: data.RecipePrototype, old_result: string, new_result: string | data.ProductPrototype, new_amount: integer?): data.RecipePrototype`
```lua
local from = "iron-plate"
local to = "copper-plate"
RECIPE("example-recipe"):replace_result(from, to)
```
```lua
local from = "iron-plate"
local to = {
  type = "item",
  name = "copper-plate",
  amount = 5
}
RECIPE("example-recipe"):replace_result(from, to)
```
```lua
local from = "iron-plate"
local to = "copper-plate"
local amount = 10
RECIPE("example-recipe"):replace_result(from, to, amount)
```

### Multiply Result Amount
`@field public multiply_result_amount fun(self: data.RecipePrototype, result_name: string, percent: number): data.RecipePrototype`
```lua
local name = "iron-plate"
local percent = 1.5
RECIPE("example-recipe"):multiply_result_amount(name, percent)
```

### Multiply Ingredient Amount
`@field public multiply_ingredient_amount fun(self: data.RecipePrototype, ingredient_name: string, percent: number): data.RecipePrototype`
```lua
local name = "iron-plate"
local percent = 1.5
RECIPE("example-recipe"):multiply_ingredient_amount(name, percent)
```

### Add Result Amount
`@field public add_result_amount fun(self: data.RecipePrototype, result_name: string, increase: number): data.RecipePrototype`
```lua
local name = "iron-plate"
local increase = 10
RECIPE("example-recipe"):add_result_amount(name, increase)
```

### Add Ingredient Amount
`@field public add_ingredient_amount fun(self: data.RecipePrototype, ingredient_name: string, increase: number): data.RecipePrototype`
```lua
local name = "iron-plate"
local increase = 10
RECIPE("example-recipe"):add_ingredient_amount(name, increase)
```

### Set Result Amount
`@field public set_result_amount fun(self: data.RecipePrototype, result_name: string, amount: number): data.RecipePrototype`
```lua
local name = "iron-plate"
local amount = 10
RECIPE("example-recipe"):set_result_amount(name, amount)
```

### Set Ingredient Amount
`@field public set_ingredient_amount fun(self: data.RecipePrototype, ingredient_name: string, amount: number): data.RecipePrototype`
```lua
local name = "iron-plate"
local amount = 10
RECIPE("example-recipe"):set_ingredient_amount(name, amount)
```

### Get Main Product
`@field public get_main_product fun(self: data.RecipePrototype, allow_multi_product: bool?): LuaItemPrototype?|LuaFluidPrototype?`
```lua
local main_product = RECIPE("example-recipe"):get_main_product()
```
```lua
local main_products = RECIPE("example-recipe"):get_main_product(true)
```

### Get Icons
`@field public get_icons fun(self: data.RecipePrototype): data.IconData`
```lua
local icons = RECIPE("example-recipe"):get_icons()
```
