# Compound Entities
*As of August 21st, 2025*<br>

Compound entities are entities made up of multiple entities. For example vatbrains are just assembling-machines with a beacon hidden inside them.

These are typically a multi-step process of tracking these manually with storage variable and when things have been placed down and integrating GUI. This is to be put simply, annoying. So I (Lemon) did what any sane programmer would do and just made a special API for it.

## How to use?

The meat and potatoes of this api is that you can do this very easily just at data stage.

Here's a minimal example of how
```lua
local parent = "assembling-machine"
local child = "beacon"
py.compound_attach_entity_to(parent, child, {})
```
And then in the control stage
```lua
require "__pypostprocessing__.lib" -- If you don't have this somewhere already

-- This should be after every other compound entity function as well
py.register_compound_entities()
py.finalize_events() -- If you don't have this either already
```
That's it, you have an assembling machine with a beacon now.

Wait but what about that empty table at the end?

### Options

The `compound_attach_entity_to` function has a lot of options currently. Here's an exhaustive list:
```lua
-- Enable GUI to open the children
-- enable_gui bool

-- Sets the title for the GUI based of a custom function
-- gui_title fun(entity: LuaEntity): string

-- Sets a caption for the Button of the GUI
-- gui_caption string

-- Sets a custom function for the gui when it's being opened
-- gui_function_name fun(event: events.on_gui_opened, player: LuaEntity, gui_root: LuaGuiElement, current_index: number, gui_child: LuaGuiElement)
-- @tparam event events.on_gui_opened Event data of when on_gui_opened is called
-- @tparam player LuaEntity the player who opened the GUI
-- @tparam gui_root LuaGuiElement The root of the preset GUI that you can add to
-- @tparam current_index number The index of the compound-entity child you are
-- @tparam gui_child LuaGuiElement The Button you are in the the gui_root

-- Sets a custom function to run when you press the submenu button
-- gui_submenu_function_name fun(entity: LuaEntity): (LuaGuiElement | LuaEntity)
```

### Example

```lua
py.compound_attach_entity_to("jaw-crusher", "beacon", {
    enable_gui = true
})
```
This is what this looks like:
![Image](../images/compound_entities_1.png)

# API Specification
How this works internally is that compound entity attachments get attached in data stage then smuggled using `mod_data` over to control stage.

In control stage we then register a few events to detect when things are placed or picked up and other functions.

## Data
```lua
-- Attachs an entity to another entity with additional properties
-- @param parent string
-- @param child string
-- 
-- @param additional AdditionalParams
-- @class AdditionalParams
-- @field enable_gui bool Enables an entry in the gui of the parent
-- @field gui_title string The title of the parent gui
-- @field gui_function_name string The name of the register compound function that handles adding the button to the gui
-- @field gui_submenu_function string The fuction called when you hit the button itself
-- @field gui_caption string The text the button has
-- @field position_offset MapPosition https://lua-api.factorio.com/2.0.64/concepts/MapPosition.html
--
-- @see https://pyanodon.github.io/pybugreports/internal_apis/compound_entities.html 
function py.compound_attach_entity_to(parent, child, additional)
    -- ...
end
```

## Control
### Register Compound Function
```lua
-- Registers a new compound function
-- @param name string Name of the function
-- @param func (GuiTitleFunction|GuiFunction|GuiSubmenuFunction)
--
-- @function GuiTitleFunction
-- @param entity LuaEntity parent entity
-- @return string Title
-- 
-- @function GuiFunction
-- @param event events.on_gui_opened Event data of when on_gui_opened is called
-- @param player LuaEntity the player who opened the GUI
-- @param gui_root LuaGuiElement The root of the preset GUI that you can add to
-- @param current_index number The index of the compound-entity child you are
-- @param gui_child LuaGuiElement The Button you are in the the gui_root
-- @return nil
--
-- @function GuiSubmenuFunction
-- @param entity Parent entity
-- @return (LuaGuiElement|LuaEntity) Anything that can be put in `player.opened`
-- 
-- @see https://pyanodon.github.io/pybugreports/internal_apis/compound_entities.html 
function py.register_compound_function(name, func)
    -- ...
end
```

### Get Compound Function Name
```lua
-- Gets a registered compound_function from a name
-- @param name string The name of the function
function py.get_compound_function(name)
    -- ...
end
```

### Get Compound Entity Children
```lua
-- Gets the compound entity's children from it's unit_number
-- @param unit_number number Unit number of the parent
function py.get_compound_entity_children(unit_number)
    -- ...
end
```

### Get Compound Entity Parent
```lua
-- Gets the compound_entity parent from a child's unit_number
-- @param unit_number number Unit number of a child
function py.get_compound_entity_parent(unit_number)
    -- ...
end
```

### Register Compound Entities
```lua
-- Register all compound_entities and create their events
function py.register_compound_entities()
    -- ...
end
```

#### Compound Attach Entity To
```lua
-- Adds a new child to a compound entity
-- Unsure about using this on non compound register parents, beware...
-- 
-- @param parent LuaEntity the parent compound entity
-- @param child string Name of the child
-- @param info Info
--
-- @class Info
-- @field enable_gui bool Not sure if it works but it's the same as the normal enable_gui property
-- @field possition_offset MapPosition https://lua-api.factorio.com/2.0.64/concepts/MapPosition.html
function py.compound_attach_entity_to(parent, child_name, info)
    -- ...
end
```

#### Delete Attached Entity by Filter Function
```lua
-- Deletes children from a parent by a filter function
-- Do not worry about validity it is checked internally
--
-- @param parent_unit_number number Unit number of the parent
-- @param filter_func fun(child: LuaEntity): bool Return true if delete
function py.delete_attached_entities_by_filter(parent_unit_number, filter_func)
```
