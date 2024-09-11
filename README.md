# Detailed UI Library Documentation

## Table of Contents
1. [Getting Started](#getting-started)
2. [Core Components](#core-components)
   - [Window](#window)
   - [Tab](#tab)
   - [Section](#section)
3. [UI Elements](#ui-elements)
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
4. [Advanced Features](#advanced-features)
   - [Designer](#designer)
   - [Themeing](#themeing)
5. [Utility Functions](#utility-functions)
6. [Flags and Data Management](#flags-and-data-management)
7. [Cleanup and Unloading](#cleanup-and-unloading)

## Getting Started

To use this UI library, start by loading it:

```lua
local library = loadstring(game:GetObjects("rbxassetid://7657867786")[1].Source)()
```

This gives you access to the main library object, which you'll use to create windows and access utility functions.

## Core Components

### Window

Create a new window, which serves as the main container for your UI:

```lua
local Window = library:CreateWindow({
    Name = "Window Name",
    Themeable = {
        Info = "Additional info",
        Credit = true
    },
    Background = {
        Asset = "rbxassetid://13337",
        Transparency = 0.5,
        Visible = true
    }
})
```

#### Window Options:
- `Name`: String, the title of the window
- `Themeable`: Table, contains theming options
  - `Info`: String, additional information displayed in the designer
  - `Credit`: Boolean, whether to display credit information
- `Background`: Table or String, sets the background image
  - `Asset`: String or Number, the asset ID for the background image
  - `Transparency`: Number, the transparency of the background (0-1 or 0-100)
  - `Visible`: Boolean, whether the background is visible

#### Window Methods:
- `Window:CreateTab(options)`: Creates a new tab
- `Window:CreateDesigner(options)`: Creates a theme designer
- `Window:MoveTabSlider(tabObject)`: Moves the tab slider to the specified tab
- `Window:GoHome()`: Returns to the home tab

### Tab

Create a new tab within a window:

```lua
local Tab = Window:CreateTab({
    Name = "Tab Name",
    Image = "rbxassetid://133337"
})
```

#### Tab Options:
- `Name`: String, the name of the tab
- `Image`: String or Number, the asset ID for the tab icon

#### Tab Methods:
- `Tab:CreateSection(options)`: Creates a new section within the tab

### Section

Create a section within a tab to group related UI elements:

```lua
local Section = Tab:CreateSection({
    Name = "Section Name",
    Side = "Left"
})
```

#### Section Options:
- `Name`: String, the name of the section
- `Side`: String, "Left" or "Right", determines which side of the tab the section appears on

#### Section Methods:
Each of these methods adds a UI element to the section:
- `Section:AddLabel(options)`
- `Section:AddToggle(options)`
- `Section:AddTextbox(options)`
- `Section:AddSlider(options)`
- `Section:AddButton(options)`
- `Section:AddKeybind(options)`
- `Section:AddDropdown(options)`
- `Section:AddSearchBox(options)`
- `Section:AddColorpicker(options)`
- `Section:AddPersistence(options)`

## UI Elements

### Label

Add a text label to a section:

```lua
Section:AddLabel({
    Text = "Label Text",
    Flag = "LabelFlag",
    UnloadValue = "Unloaded",
    UnloadFunc = function() end
})
```

#### Label Options:
- `Text`: String, the text to display
- `Flag`: String, a unique identifier for accessing the label's value
- `UnloadValue`: Any, the value to set when the UI is unloaded
- `UnloadFunc`: Function, called when the UI is unloaded

#### Label Methods:
- `Label:Set(newText)`: Updates the label's text
- `Label:Reset()`: Resets the label to its default text
- `Label:Get()`: Returns the current text

### Toggle

Add a toggle switch to a section:

```lua
Section:AddToggle({
    Name = "Toggle Name",
    Value = false,
    Callback = function(Value) end,
    Flag = "ToggleFlag",
    Location = Table,
    LocationFlag = "LocationFlag",
    UnloadValue = false,
    UnloadFunc = function() end,
    Locked = false,
    Keybind = {
        Flag = "ToggleKeybindFlag",
        Value = Enum.KeyCode.R,
        Mode = "Toggle",
        DynamicTime = 0.65
    },
    Condition = function(Value) return true end,
    AllowDuplicateCalls = false
})
```

#### Toggle Options:
- `Name`: String, the name of the toggle
- `Value`: Boolean, the initial state of the toggle
- `Callback`: Function, called when the toggle state changes
- `Flag`: String, a unique identifier for accessing the toggle's value
- `Location`: Table, a table to store the toggle's value
- `LocationFlag`: String, the key to use in the Location table
- `UnloadValue`: Any, the value to set when the UI is unloaded
- `UnloadFunc`: Function, called when the UI is unloaded
- `Locked`: Boolean, whether the toggle is locked (unchangeable)
- `Keybind`: Table, keybind options for the toggle
- `Condition`: Function, determines if the toggle state can be changed
- `AllowDuplicateCalls`: Boolean, allows callback to fire even if the new value is the same as the old value

#### Toggle Methods:
- `Toggle:Set(newValue)`: Updates the toggle's state
- `Toggle:Reset()`: Resets the toggle to its default state
- `Toggle:Get()`: Returns the current state
- `Toggle:SetLocked(lockedState)`: Sets whether the toggle is locked
- `Toggle:SetCondition(newCondition)`: Sets a new condition for changing the toggle's state

### Textbox

Add a text input box to a section:

```lua
Section:AddTextbox({
    Name = "Textbox Name",
    Value = "Default Text",
    Callback = function(Value) end,
    Flag = "TextboxFlag",
    Location = Table,
    LocationFlag = "LocationFlag",
    UnloadValue = "",
    UnloadFunc = function() end,
    Placeholder = "Enter text...",
    Type = "Default",
    Min = 0,
    Max = 100,
    Decimals = 2,
    Hex = false,
    Binary = false,
    Base = 10,
    Rich = false,
    Lines = false,
    Scaled = false,
    Font = Enum.Font.Code,
    PreFormat = function(Value) return Value end,
    PostFormat = function(Value) return Value end,
    CustomProperties = {
        TextTruncate = Enum.TextTruncate.None
    },
    AllowDuplicateCalls = false
})
```

#### Textbox Options:
- `Name`: String, the name of the textbox
- `Value`: String or Number, the initial value of the textbox
- `Callback`: Function, called when the textbox value changes
- `Flag`: String, a unique identifier for accessing the textbox's value
- `Location`: Table, a table to store the textbox's value
- `LocationFlag`: String, the key to use in the Location table
- `UnloadValue`: Any, the value to set when the UI is unloaded
- `UnloadFunc`: Function, called when the UI is unloaded
- `Placeholder`: String, text to display when the textbox is empty
- `Type`: String, "Default" or "Number"
- `Min`: Number, minimum value (for number type)
- `Max`: Number, maximum value (for number type)
- `Decimals`: Number, number of decimal places (for number type)
- `Hex`: Boolean, whether to display as hexadecimal
- `Binary`: Boolean, whether to display as binary
- `Base`: Number, the number base to use
- `Rich`: Boolean, whether to use rich text
- `Lines`: Boolean, whether to allow multiple lines
- `Scaled`: Boolean, whether to use text scaling
- `Font`: EnumItem, the font to use
- `PreFormat`: Function, called before displaying the value
- `PostFormat`: Function, called after the user inputs a value
- `CustomProperties`: Table, additional properties to apply to the textbox
- `AllowDuplicateCalls`: Boolean, allows callback to fire even if the new value is the same as the old value

#### Textbox Methods:
- `Textbox:Set(newValue)`: Updates the textbox's value
- `Textbox:Reset()`: Resets the textbox to its default value
- `Textbox:Get()`: Returns the current value

### Slider

Add a slider to a section:

```lua
Section:AddSlider({
    Name = "Slider Name",
    Value = 50,
    Callback = function(Value) end,
    Flag = "SliderFlag",
    Location = Table,
    LocationFlag = "LocationFlag",
    UnloadValue = 0,
    UnloadFunc = function() end,
    Min = 0,
    Max = 100,
    Decimals = 2,
    Format = function(Value) return "Value: " .. Value end,
    IllegalInput = false,
    Textbox = {
        Hex = false,
        Binary = false,
        Base = 10,
        PreFormat = function(Value) return Value end,
        PostFormat = function(Value) return Value end,
        IllegalInput = false
    },
    AllowDuplicateCalls = false
})
```

#### Slider Options:
- `Name`: String, the name of the slider
- `Value`: Number, the initial value of the slider
- `Callback`: Function, called when the slider value changes
- `Flag`: String, a unique identifier for accessing the slider's value
- `Location`: Table, a table to store the slider's value
- `LocationFlag`: String, the key to use in the Location table
- `UnloadValue`: Any, the value to set when the UI is unloaded
- `UnloadFunc`: Function, called when the UI is unloaded
- `Min`: Number, the minimum value of the slider
- `Max`: Number, the maximum value of the slider
- `Decimals`: Number, the number of decimal places to display
- `Format`: Function, formats the displayed value
- `IllegalInput`: Boolean, whether to allow input outside the min/max range
- `Textbox`: Table, options for the associated textbox
- `AllowDuplicateCalls`: Boolean, allows callback to fire even if the new value is the same as the old value

#### Slider Methods:
- `Slider:Set(newValue)`: Updates the slider's value
- `Slider:Reset()`: Resets the slider to its default value
- `Slider:Get()`: Returns the current value
- `Slider:SetConstraints(newMin, newMax)`: Sets new minimum and maximum values
- `Slider:SetMin(newMin)`: Sets a new minimum value
- `Slider:SetMax(newMax)`: Sets a new maximum value

### Button

Add a clickable button to a section:

```lua
Section:AddButton({
    Name = "Button Name",
    Callback = function() end,
    Locked = false,
    Condition = function() return true end
})
```

#### Button Options:
- `Name`: String, the text displayed on the button
- `Callback`: Function, called when the button is clicked
- `Locked`: Boolean, whether the button is locked (unclickable)
- `Condition`: Function, determines if the button can be clicked

#### Button Methods:
- `Button:Press()`: Simulates a button press
- `Button:SetLocked(lockedState)`: Sets whether the button is locked
- `Button:SetCondition(newCondition)`: Sets a new condition for clicking the button
- `Button:SetText(newText)`: Changes the button's text
- `Button:SetCallback(newCallback)`: Changes the button's callback function

### Keybind

Add a keybind to a section:

```lua
Section:AddKeybind({
    Name = "Keybind Name",
    Value = Enum.KeyCode.R,
    Callback = function(NewValue, OldValue) end,
    Flag = "KeybindFlag",
    Location = Table,
    LocationFlag = "LocationFlag",
    UnloadValue = Enum.KeyCode.Unknown,
    UnloadFunc = function() end,
    Pressed = function() end,
    KeyNames = {"MouseButton1", "MouseButton2"},
    AllowDuplicateCalls = false
})
```

#### Keybind Options:
- `Name`: String, the name of the keybind
- `Value`: EnumItem, the initial key for the keybind
- `Callback`: Function, called when the keybind is changed
- `Flag`: String, a unique identifier for accessing the keybind's value
- `Location`: Table, a table to store the keybind's value
- `LocationFlag`: String, the key to use in the Location table
- `UnloadValue`: Any, the value to set when the UI is unloaded
- `UnloadFunc`: Function, called when the UI is unloaded
- `Pressed`: Function, called when the keybind is activated
- `KeyNames`: Table, custom names for specific keys
- `AllowDuplicateCalls`: Boolean, allows callback to fire even if the new value is the same as the old value

#### Keybind Methods:
- `Keybind:Set(newValue)`: Updates the keybind's key
- `Keybind:Reset()`: Resets the keybind to its default key
- `Keybind:Get()`: Returns the current key

### Dropdown

Add a dropdown menu to a section:

```lua
Section:AddDropdown({
    Name = "Dropdown Name",
    Value = "Default",
    Callback = function(Value) end,
    Flag = "DropdownFlag",
    Location = Table,
    LocationFlag = "LocationFlag",
    UnloadValue = nil,
    UnloadFunc = function() end,
    List = {"Option1", "Option2", "Option3"},
    Filter = function(Value) return true end,
    Method = "GetDescendants",
    BlankValue = "Select an option",
    Sort = true,
    Multi = false,
    ItemAdded = function(Item) end,
    ItemRemoved = function(Item) end,
    ItemChanged = function(Item, SelectedState) end,
    ItemsCleared = function(Items) end,
    ScrollUpButton = Enum.KeyCode.Up,
    ScrollDownButton = Enum.KeyCode.Down,
    ScrollButtonRate = 5,
    DisablePrecisionScrolling = false,
    AllowDuplicateCalls = false
})
```

#### Dropdown Options:
- `Name`: String, the name of the dropdown
- `Value`: Any, the initial selected value
- `Callback`: Function, called when a selection is made
- `Flag`: String, a unique identifier for accessing the dropdown's value
- `Location`: Table, a table to store the dropdown's value
- `LocationFlag`: String, the key to use in the Location table
- `UnloadValue`: Any, the value to set when the UI is unloaded
- `UnloadFunc`: Function, called when the UI is unloaded
- `List`: Table, the list of options to display
- `Filter`: Function or String, filters the list of options
- `Method`: String or Function, method
- `Others`: explains itself
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
