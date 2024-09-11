# UI Library Documentation

## Getting Started

To use this UI library, start by loading it:

```lua
local library = loadstring(game:GetObjects("rbxassetid://7657867786")[1].Source)()
```

## Core Components

### Window

Create a new window:

```lua
local Window = library:CreateWindow({
    Name = "Window Name",
    Themeable = {
        Info = "Additional info"
    }
})
```

### Tab

Create a new tab within a window:

```lua
local Tab = Window:CreateTab({
    Name = "Tab Name"
})
```

### Section

Create a section within a tab:

```lua
local Section = Tab:CreateSection({
    Name = "Section Name",
    Side = "Left" -- or "Right"
})
```

## UI Elements

### Toggle

```lua
Section:AddToggle({
    Name = "Toggle Name",
    Flag = "UniqueFlagName",
    Callback = function(Value) end,
    Keybind = 1 -- Optional keybind
})
```

### Slider

```lua
Section:AddSlider({
    Name = "Slider Name",
    Flag = "UniqueFlagName",
    Value = 50,
    Min = 0,
    Max = 100,
    Precise = 2, -- Decimal places
    Callback = function(Value) end,
    Format = function(Value) return "Formatted: " .. Value end
})
```

### Button

```lua
Section:AddButton({
    Name = "Button Name",
    Callback = function() end
})
```

### Keybind

```lua
Section:AddKeybind({
    Name = "Keybind Name",
    Callback = function() end
})
```

### Textbox

```lua
Section:AddTextbox({
    Name = "Textbox Name",
    Flag = "UniqueFlagName",
    Value = "Default",
    Callback = function(Value) end
})
```

## Advanced Features

### Dynamic Keybinds

```lua
Section:AddToggle({
    Name = "Dynamic Keybind",
    Keybind = {
        Mode = "Dynamic" -- Switches between hold and toggle based on press duration
    },
    Callback = function(Value) end
})
```

### Custom Formatting

Use the `Format` function to customize how values are displayed:

```lua
Section:AddSlider({
    Name = "Custom Format",
    Format = function(Value)
        if Value == 0 then
            return "Special Case"
        else
            return "Normal: " .. Value
        end
    }
})
```

## Utility Functions

- `Wait(Time)`: Waits for a specified time, returns true if the library is still active.
- `library.subs.updatecolors()`: Re-applies all colors from the designer.
- `library.subs.removeSpaces(String)`: Removes spaces from a string.
- `library.subs.Color3ToHex(Color3)`: Converts Color3 to hex.
- `library.subs.Color3FromHex(String/Hex)`: Converts hex to Color3.

## Flags

Flags are used to uniquely identify and access UI elements:

```lua
local flagValue = library.Flags.UniqueFlagName
```

## Cleanup

To remove the UI and clean up resources:

```lua
library:Unload()
```

This documentation covers the main features of the UI library as demonstrated in the provided example. For more detailed information or additional features, refer to the library's source code or official documentation if available.
