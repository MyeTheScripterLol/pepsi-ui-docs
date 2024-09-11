# Comprehensive UI Library Documentation

## Table of Contents
1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Core Components](#core-components)
   - [Window](#window)
   - [Tab](#tab)
   - [Section](#section)
4. [UI Elements](#ui-elements)
   - [Label](#label)
   - [Toggle](#toggle)
   - [Textbox](#textbox)
   - [Slider](#slider)
   - [Button](#button)
   - [Keybind](#keybind)
   - [Dropdown](#dropdown)
   - [SearchBox](#searchbox)
   - [Colorpicker](#colorpicker)
   - [Persistence](#persistence)
5. [Advanced Features](#advanced-features)
   - [Designer](#designer)
   - [Flags](#flags)
6. [Utility Functions](#utility-functions)
7. [Best Practices](#best-practices)
8. [Cleanup](#cleanup)

## Introduction

This UI library provides a comprehensive set of tools for creating graphical user interfaces in Roblox games. It offers a wide range of customizable elements and features to enhance user interaction and experience.

## Getting Started

To use this UI library, start by loading it:

```lua
local library = loadstring(game:GetObjects("rbxassetid://7657867786")[1].Source)()
```

## Core Components

### Window

The Window is the top-level container for your UI.

```lua
local Window = library:CreateWindow({
    Name = "Window Name",
    Themeable = {
        Info = "Discord Server: VzYTJ7Y"
    }
})
```

#### Options:
- `Name`: (string) The title of the window
- `DefaultTheme`: (JSON | nil) Custom theme settings
- `Themeable`: (boolean | table) Theming options
  - `Info`: (string) Additional information displayed in the designer

### Tab

Tabs help organize different sections of your UI.

```lua
local Tab = Window:CreateTab({
    Name = "Tab Name",
    Image = "rbxassetid://123456789"
})
```

#### Options:
- `Name`: (string) The name of the tab
- `Image`: (string | number) Icon for the tab

### Section

Sections group related UI elements within a tab.

```lua
local Section = Tab:CreateSection({
    Name = "Section Name",
    Side = "Left"
})
```

#### Options:
- `Name`: (string) The name of the section
- `Side`: (string) "Left" or "Right" side of the tab

## UI Elements

### Label

Labels display non-interactive text.

```lua
Section:AddLabel({
    Text = "Label Text",
    Flag = "LabelFlag"
})
```

#### Options:
- `Text`: (string) The text to display
- `Flag`: (string) Unique identifier for the label

### Toggle

Toggles allow users to switch between two states.

```lua
Section:AddToggle({
    Name = "Toggle Name",
    Flag = "ToggleFlag",
    Value = false,
    Callback = function(Value) end,
    Keybind = {
        Flag = "ToggleKeybind",
        Mode = "Toggle"
    }
})
```

#### Options:
- `Name`: (string) The name of the toggle
- `Flag`: (string) Unique identifier for the toggle
- `Value`: (boolean) Initial state
- `Callback`: (function) Function called when the toggle changes
- `Keybind`: (table) Keybind options
  - `Flag`: (string) Unique identifier for the keybind
  - `Mode`: (string) "Toggle", "Hold", or "Dynamic"

### Textbox

Textboxes allow users to input text.

```lua
Section:AddTextbox({
    Name = "Textbox Name",
    Flag = "TextboxFlag",
    Value = "Default text",
    Placeholder = "Enter text here",
    Callback = function(Value) end
})
```

#### Options:
- `Name`: (string) The name of the textbox
- `Flag`: (string) Unique identifier for the textbox
- `Value`: (string) Initial text
- `Placeholder`: (string) Placeholder text
- `Callback`: (function) Function called when the text changes

### Slider

Sliders allow users to select a numeric value within a range.

```lua
Section:AddSlider({
    Name = "Slider Name",
    Flag = "SliderFlag",
    Value = 50,
    Min = 0,
    Max = 100,
    Decimals = 2,
    Callback = function(Value) end,
    Format = function(Value) return "Value: " .. Value end
})
```

#### Options:
- `Name`: (string) The name of the slider
- `Flag`: (string) Unique identifier for the slider
- `Value`: (number) Initial value
- `Min`: (number) Minimum value
- `Max`: (number) Maximum value
- `Decimals`: (number) Number of decimal places
- `Callback`: (function) Function called when the value changes
- `Format`: (function) Custom formatting for the displayed value

### Button

Buttons trigger actions when clicked.

```lua
Section:AddButton({
    Name = "Button Name",
    Callback = function() end
})
```

#### Options:
- `Name`: (string) The name of the button
- `Callback`: (function) Function called when the button is clicked

### Keybind

Keybinds allow users to set custom key combinations for actions.

```lua
Section:AddKeybind({
    Name = "Keybind Name",
    Flag = "KeybindFlag",
    Value = Enum.KeyCode.F,
    Callback = function() end,
    Pressed = function() end
})
```

#### Options:
- `Name`: (string) The name of the keybind
- `Flag`: (string) Unique identifier for the keybind
- `Value`: (EnumItem) Initial key
- `Callback`: (function) Function called when the keybind is changed
- `Pressed`: (function) Function called when the key is pressed

### Dropdown

Dropdowns allow users to select from a list of options.

```lua
Section:AddDropdown({
    Name = "Dropdown Name",
    Flag = "DropdownFlag",
    Value = "Option 1",
    List = {"Option 1", "Option 2", "Option 3"},
    Callback = function(Value) end,
    Multi = false
})
```

#### Options:
- `Name`: (string) The name of the dropdown
- `Flag`: (string) Unique identifier for the dropdown
- `Value`: (any) Initial selected value
- `List`: (table) List of options
- `Callback`: (function) Function called when a selection is made
- `Multi`: (boolean) Allow multiple selections

### SearchBox

SearchBoxes are similar to dropdowns but with a search functionality.

```lua
Section:AddSearchBox({
    Name = "SearchBox Name",
    Flag = "SearchBoxFlag",
    Value = "Option 1",
    List = {"Option 1", "Option 2", "Option 3"},
    Callback = function(Value) end,
    RegEx = false
})
```

#### Options:
- `Name`: (string) The name of the search box
- `Flag`: (string) Unique identifier for the search box
- `Value`: (any) Initial selected value
- `List`: (table) List of options
- `Callback`: (function) Function called when a selection is made
- `RegEx`: (boolean) Enable regular expression search

### Colorpicker

Colorpickers allow users to select colors.

```lua
Section:AddColorpicker({
    Name = "Colorpicker Name",
    Flag = "ColorpickerFlag",
    Value = Color3.new(1, 0, 0),
    Callback = function(Value) end,
    Rainbow = false
})
```

#### Options:
- `Name`: (string) The name of the colorpicker
- `Flag`: (string) Unique identifier for the colorpicker
- `Value`: (Color3) Initial color
- `Callback`: (function) Function called when the color changes
- `Rainbow`: (boolean) Enable rainbow mode

### Persistence

Persistence allows saving and loading of UI states.

```lua
Section:AddPersistence({
    Name = "Persistence Name",
    Flag = "PersistenceFlag",
    Value = "config.json",
    Workspace = "MyConfigs",
    Callback = function(Value) end,
    LoadCallback = function(FilePath) end,
    SaveCallback = function(FilePath) end
})
```

#### Options:
- `Name`: (string) The name of the persistence element
- `Flag`: (string) Unique identifier for the persistence
- `Value`: (string) Default file name
- `Workspace`: (string) Folder name for saved configs
- `Callback`: (function) Function called when a file is selected
- `LoadCallback`: (function) Function called before loading a file
- `SaveCallback`: (function) Function called after saving a file

## Advanced Features

### Designer

The Designer allows for customization of the UI's appearance.

```lua
Window:CreateDesigner({
    Background = {
        Asset = "rbxassetid://13337",
        Transparency = 0.5,
        Visible = true
    },
    Image = "rbxassetid://7483871523",
    Info = "Extra info displayed in designer",
    Credit = true
})
```

#### Options:
- `Background`: (table) Background settings
- `Image`: (string) Image asset ID
- `Info`: (string) Additional information
- `Credit`: (boolean) Show credit information

### Flags

Flags are used to uniquely identify and access UI elements:

```lua
local flagValue = library.Flags.MyFlag
```

## Utility Functions

- `library.subs.Wait(Time)`: Waits for a specified time, returns true if the library is still active
- `library.subs.updatecolors()`: Re-applies all colors from the designer
- `library.subs.removeSpaces(String)`: Removes spaces from a string
- `library.subs.Color3ToHex(Color3)`: Converts Color3 to hex
- `library.subs.Color3FromHex(String/Hex)`: Converts hex to Color3
- `library.subs.textToSize(String)`: Calculates the size of text
- `library.subs.Instance_new(Class, Parent)`: Creates a new instance with protection

## Best Practices

1. Use unique flags for each UI element to avoid conflicts
2. Group related elements in sections for better organization
3. Use the Designer for consistent theming across your UI
4. Implement persistence for user-friendly configuration saving and loading
5. Utilize callbacks to respond to user interactions effectively

## Cleanup

To remove the UI and clean up resources:

```lua
library:Unload()
```

This will disconnect all signals and destroy all created instances.

---

This documentation provides a comprehensive overview of the UI library's features and usage. For specific implementation details or advanced usage, refer to the library's source code or reach out to the library's maintainer.
