# BetaOrion

Lightweight UI library for Roblox scripts, Orion / BetterOrion style.

## Installation

```lua
local OrionLib = loadstring(game:HttpGet("https://gist.githubusercontent.com/Polinorsik/d9442cbecdf1893b527ffd8d1a452c6b/raw/16616fdd2894c732383e39212658d59fb17e4a59/betaorion"))()
```

## Quick start

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({ Name = "My Script", ToggleUIKey = Enum.KeyCode.RightShift })
local Tab = Window:MakeTab({ Name = "Main", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Actions", Side = "Left" })

Sec:AddButton({
    Name = "Click me",
    Callback = function() end,
})

OrionLib:Init()
```

---

## OrionLib

### MakeWindow

```lua
OrionLib:MakeWindow(Config)
```

Example:

```lua
local Window = OrionLib:MakeWindow({ Name = "My Script", SubName = "v1.0" })
```

| Field | Type | Default |
|---|---|---|
| `Name` | string | `"Better Orion"` |
| `SubName` | string | `""` |
| `Size` | UDim2 | `600x400` |
| `MinSize` | UDim2 | `400x200` |
| `MaxSize` | UDim2 | `4000x2000` |
| `IntroEnabled` | bool | `false` |
| `IntroText` | string | `"Better Orion"` |
| `IntroIcon` | string | — |
| `ShowIcon` | bool | `false` |
| `Icon` | string | — |
| `Transparency` | number | `0.35` |
| `ToggleUIKey` | Enum.KeyCode | `Enum.KeyCode.Tab` |
| `SearchBar` | bool | `false` |
| `FreeMouse` | bool | `true` |
| `NewUI` | bool | `false` |
| `BackgroundURL` | string | `""` |
| `BackgroundTransparency` | number | `0.2` |
| `WatermarkConfig` | table | `{Enabled, Visible, ShowFPS, ShowPing, ShowName, ShowClockTime, Icon}` |

### MakeNotification

```lua
OrionLib:MakeNotification(Config)
```

Example:

```lua
OrionLib:MakeNotification({ Name = "Loaded", Content = "Script ready", Time = 5 })
```

| Field | Default |
|---|---|
| `Name` | `"Notification Title"` |
| `Content` | `"Notification Content"` |
| `Image` | `"server"` |
| `Time` | `5` |
| `Color` | theme color |
| `TextColor` | theme color |
| `Sound` | `""` |
| `SoundVolume` | `1` |

### Init

```lua
OrionLib:Init()
```

Example:

```lua
OrionLib:Init()
```

No arguments. Shows the window.

### Destroy

```lua
OrionLib:Destroy()
```

Example:

```lua
OrionLib:Destroy()
```

No arguments. Destroys the window and everything inside.

### IsRunning

```lua
OrionLib:IsRunning()
```

Example:

```lua
if OrionLib:IsRunning() then
    print("Window is alive")
end
```

Returns `true` / `false`.

### SetConfigTab

```lua
OrionLib:SetConfigTab(TabName)
```

Example:

```lua
local Settings = Window:MakeTab({ Name = "Settings", Icon = "settings" })
OrionLib:SetConfigTab("Settings")
```

| Field | Type |
|---|---|
| `TabName` | string |

### SetNotifyingState

```lua
OrionLib:SetNotifyingState(Config)
```

Example:

```lua
OrionLib:SetNotifyingState({ Enabled = true, Printing = true })
```

| Field | Default |
|---|---|
| `Enabled` | `true` |
| `Printing` | `true` |

### SetCornerRadius

```lua
OrionLib:SetCornerRadius(n)
```

Example:

```lua
OrionLib:SetCornerRadius(10)
```

| Field | Type |
|---|---|
| `n` | number |

### SaveAndLoadSizes

```lua
OrionLib:SaveAndLoadSizes()
```

Example:

```lua
OrionLib:SaveAndLoadSizes()
```

No arguments.

### LoadAutoloadConfigs

```lua
OrionLib:LoadAutoloadConfigs()
```

Example:

```lua
task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)
```

No arguments.

**Properties:**

- `OrionLib.Flags` — table `[flag] = element`
- `OrionLib.SelectedTheme` — current theme
- `OrionLib.ToggleUIKey` — window toggle key

---

## Window

### MakeTab

```lua
Window:MakeTab(Config)
```

Example:

```lua
local Tab = Window:MakeTab({ Name = "Main", Icon = "home" })
```

| Field | Default |
|---|---|
| `Name` | `"Tab"` |
| `Icon` | `""` |
| `PremiumOnly` | `false` |

### SetSize

```lua
Window:SetSize(UDim2)
```

Example:

```lua
Window:SetSize(UDim2.fromOffset(800, 500))
```

### SetColor

```lua
Window:SetColor(Color3)
```

Example:

```lua
Window:SetColor(Color3.fromRGB(25, 25, 25))
```

### SetTransparency

```lua
Window:SetTransparency(n)
```

Example:

```lua
Window:SetTransparency(0.2)
```

### SetStrokeColor

```lua
Window:SetStrokeColor(Color3)
```

Example:

```lua
Window:SetStrokeColor(Color3.fromRGB(80, 150, 20))
```

### SetStrokeTransparency

```lua
Window:SetStrokeTransparency(n)
```

Example:

```lua
Window:SetStrokeTransparency(0.5)
```

### SetTextColor

```lua
Window:SetTextColor(Color3)
```

Example:

```lua
Window:SetTextColor(Color3.fromRGB(240, 240, 240))
```

### SetTextTransparency

```lua
Window:SetTextTransparency(n)
```

Example:

```lua
Window:SetTextTransparency(0)
```

### SetIconColor

```lua
Window:SetIconColor(Color3)
```

Example:

```lua
Window:SetIconColor(Color3.fromRGB(255, 255, 255))
```

### SetToggleKey

```lua
Window:SetToggleKey(key)
```

Example:

```lua
Window:SetToggleKey(Enum.KeyCode.RightShift)
```

### SetThemeColor

```lua
Window:SetThemeColor(theme, elem, val)
```

Example:

```lua
Window:SetThemeColor("Default", "Main", { Color = Color3.fromRGB(20, 20, 20), Transparency = 0.35 })
```

### SetThemeTransparency

```lua
Window:SetThemeTransparency(theme, elem, n)
```

Example:

```lua
Window:SetThemeTransparency("Default", "Stroke", 0.5)
```

### NewUI

```lua
Window:NewUI(bool)
```

Example:

```lua
Window:NewUI(true)
```

### SetMainCorners

```lua
Window:SetMainCorners(n)
```

Example:

```lua
Window:SetMainCorners(12)
```

### SetElementsCorners

```lua
Window:SetElementsCorners(n)
```

Example:

```lua
Window:SetElementsCorners(8)
```

### SetBackground

```lua
Window:SetBackground(url)
```

Example:

```lua
Window:SetBackground("rbxassetid://123456789")
```

### SetBackgroundTransparency

```lua
Window:SetBackgroundTransparency(n)
```

Example:

```lua
Window:SetBackgroundTransparency(0.3)
```

### SetBackgroundVisibility

```lua
Window:SetBackgroundVisibility(bool)
```

Example:

```lua
Window:SetBackgroundVisibility(true)
```

### SetWatermarkText

```lua
Window:SetWatermarkText(str)
```

Example:

```lua
Window:SetWatermarkText("My Cheat | v1.0")
```

### SetWatermarkVisibility

```lua
Window:SetWatermarkVisibility(bool)
```

Example:

```lua
Window:SetWatermarkVisibility(true)
```

### SetWatermarkColor

```lua
Window:SetWatermarkColor(c)
```

Example:

```lua
Window:SetWatermarkColor(Color3.fromRGB(25, 25, 25))
```

### SetWatermarkTextColor

```lua
Window:SetWatermarkTextColor(c)
```

Example:

```lua
Window:SetWatermarkTextColor(Color3.new(1, 1, 1))
```

### SetWatermarkIconColor

```lua
Window:SetWatermarkIconColor(c)
```

Example:

```lua
Window:SetWatermarkIconColor(Color3.fromRGB(255, 200, 50))
```

### SetWatermarkTransparency

```lua
Window:SetWatermarkTransparency(n)
```

Example:

```lua
Window:SetWatermarkTransparency(0.3)
```

### SetWatermarkPosition

```lua
Window:SetWatermarkPosition(UDim2)
```

Example:

```lua
Window:SetWatermarkPosition(UDim2.new(0, 15, 0, 15))
```

### DestroyWatermark

```lua
Window:DestroyWatermark()
```

Example:

```lua
Window:DestroyWatermark()
```

### DestroyElement

```lua
Window:DestroyElement(flag)
```

Example:

```lua
Window:DestroyElement("esp_enabled")
```

### GetToggleUIKey

```lua
Window:GetToggleUIKey()
```

Example:

```lua
local key = Window:GetToggleUIKey()
```

---

## Tab

### AddSection

```lua
Tab:AddSection(Config)
```

Example:

```lua
local Section = Tab:AddSection({ Name = "Main", Side = "Left" })
```

| Field | Default |
|---|---|
| `Name` | `"Section"` |
| `Side` | `"Left"` |

---

## Section — AddLabel

```lua
Section:AddLabel(Text)
```

Example:

```lua
Section:AddLabel("Status: running")
```

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddParagraph

```lua
Section:AddParagraph(Title, Content)
```

Example:

```lua
Section:AddParagraph("Welcome", "This is a demo script")
```

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddButton

```lua
Section:AddButton(Config)
```

Example:

```lua
Section:AddButton({
    Name = "Notify",
    Callback = function() end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Button"` |
| `Callback` | `function() end` |
| `Icon` | `"rbxassetid://3944703587"` |
| `DoubleTap` | `false` |
| `TapDelay` | `0.5` |
| `Settings` | `false` |

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddToggle

```lua
Section:AddToggle(Config)
```

Example:

```lua
Section:AddToggle({
    Name = "ESP",
    Default = false,
    Flag = "esp_enabled",
    Save = true,
    Callback = function(Value) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Toggle"` |
| `Default` | `false` |
| `Callback` | `function(Value) end` |
| `Color` | `Color3.fromRGB(50,50,50)` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Binded` | `false` |
| `DefaultBind` | `""` |
| `Settings` | `false` |

**Properties:** `Toggle.Value` (bool), `Toggle.BindValue` (string), `Toggle.Type = "Toggle"`

**Methods:** `:Set(bool)`, `:SetBind(key)`, `:SetName(str)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`, `:ChangeVisibility(bool)`

## Section — AddSlider

```lua
Section:AddSlider(Config)
```

Example:

```lua
Section:AddSlider({
    Name = "Speed",
    Min = 1, Max = 100, Default = 16, Increment = 1,
    ValueName = "spd",
    Flag = "speed",
    Save = true,
    Callback = function(Value) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Slider"` |
| `Min` | `0` |
| `Max` | `100` |
| `Increment` | `1` |
| `Default` | `50` |
| `ValueName` | `""` |
| `Color` | `Color3.fromRGB(50,50,50)` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Callback` | `function(Value) end` |
| `InputEndedCallback` | `function(Value) end` |

**Property:** `Slider.Value` (number)

**Methods:** `:Set(number)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddDropdown

```lua
Section:AddDropdown(Config)
```

Example:

```lua
Section:AddDropdown({
    Name = "Mode",
    Options = {"Legit", "Rage", "Silent"},
    Default = "Legit",
    Flag = "aim_mode",
    Save = true,
    Callback = function(Value) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Dropdown"` |
| `Options` | `{}` |
| `Multi` | `false` |
| `Default` | `Multi and {} or ""` |
| `MaxSize` | `5` |
| `Search` | `false` |
| `OptionsSize` | `28` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Callback` | `function(Value) end` |

**Property:** `Dropdown.Value` — string (single) or table (multi)

**Methods:** `:Set(value)`, `:Refresh(options, delete)`, `:ChangeVisibility(bool)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`

## Section — AddPlayersDropdown

```lua
Section:AddPlayersDropdown(Config)
```

Example:

```lua
Section:AddPlayersDropdown({
    Name = "Target",
    Search = true,
    Flag = "target_player",
    Save = true,
    Callback = function(Value) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Dropdown"` |
| `Multi` | `false` |
| `MaxSize` | `5` |
| `Search` | `false` |
| `OptionsSize` | `28` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Callback` | `function(Value) end` |

**Property:** `Dropdown.Value` — string (username) or nil

**Methods:** `:Set(value)`, `:Refresh()`, `:ChangeVisibility(bool)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`

## Section — AddBind

```lua
Section:AddBind(Config)
```

Example:

```lua
Section:AddBind({
    Name = "Fly",
    Default = Enum.KeyCode.F,
    Hold = false,
    Flag = "bind_fly",
    Save = true,
    Callback = function(holding) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Bind"` |
| `Default` | `""` |
| `Hold` | `false` |
| `Callback` | `function(holding) end` |
| `Flag` | `nil` |
| `Save` | `false` |
| `UIBind` | `false` |
| `Button` | `false` |
| `ButtonIcon` | `"rbxassetid://3944703587"` |
| `DoubleTap` | `false` |
| `TapDelay` | `0.5` |
| `Color` | `Color3.fromRGB(50,50,50)` |

**Property:** `Bind.Value` (string, key name)

**Methods:** `:Set(key)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddTextbox

```lua
Section:AddTextbox(Config)
```

Example:

```lua
Section:AddTextbox({
    Name = "Message",
    Default = "",
    TextDisappear = false,
    Callback = function(Text) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Textbox"` |
| `Default` | `""` |
| `TextDisappear` | `false` |
| `Callback` | `function(Text) end` |

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddColorpicker

```lua
Section:AddColorpicker(Config)
```

Example:

```lua
Section:AddColorpicker({
    Name = "ESP Color",
    Default = Color3.fromRGB(255, 80, 80),
    DefaultTransparency = 0,
    Flag = "esp_color",
    Save = true,
    Callback = function(Color, Transparency) end,
})
```

| Field | Default |
|---|---|
| `Name` | `"Colorpicker"` |
| `Default` | `Color3.fromRGB(255,255,255)` |
| `DefaultTransparency` | `0` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Callback` | `function(Color, Transparency) end` |

**Properties:** `Colorpicker.Value` (Color3), `Colorpicker.TransparencyValue` (number)

**Methods:** `:Set(Color3, Transparency, notCallback)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

---

## Config system

```lua
local Settings = Window:MakeTab({ Name = "Settings", Icon = "settings" })
OrionLib:SetConfigTab("Settings")
```

Populates the tab with:

- Edit Theme — Window / Elements / Stroke / Text, New UI, Corner Radius.
- Edit Background — background list, Custom Background, Transparency.
- Save Backgrounds — link, name, Save / Delete.
- Save Config — list, name, Load / Save / Delete / Autoload / Remove Autoload / Refresh.
- Save Themes — list, name, Load / Save / Delete / Autoload / Remove Autoload / Refresh.

Requires executor file functions: `writefile`, `isfile`, `listfiles`, `readfile`, `isfolder`, `makefolder`, `getcustomasset`.

### Save paths

```
BetterOrion/
  Config/<GameId>/<ConfigName>.json
  Themes/<ThemeName>.json
  Backgrounds/Backgrounds/<Name>.jpg
  Backgrounds/Settings/SelectedBackground.json
  Autoload/<GameId>/AutoloadConfig.txt
  Autoload/<GameId>/AutoloadTheme.txt
  Autoload/<GameId>/AutoloadBackground.txt
```

### Flags

```lua
Section:AddToggle({ Name = "ESP", Flag = "esp_enabled", Save = true, Callback = function(v) end })
```

`Save Config` stores the flag's `Value` and `BindValue`. `Load Config` restores them via `:Set(v.Value)` and `:SetBind(v.BindValue)`.

### Autoload

```lua
task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)
```

---

## Full example

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({
    Name = "Demo",
    SubName = "v1.0",
    ToggleUIKey = Enum.KeyCode.RightShift,
    ShowIcon = true,
    Icon = "moon",
    FreeMouse = true,
})

local Tab = Window:MakeTab({ Name = "Main", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Actions", Side = "Left" })

Sec:AddButton({
    Name = "Notify",
    Callback = function()
        OrionLib:MakeNotification({ Name = "Hi", Content = "It works!", Time = 3 })
    end,
})

Sec:AddToggle({
    Name = "ESP",
    Default = false,
    Flag = "esp_enabled",
    Save = true,
    Callback = function(v) print("ESP:", v) end,
})

local Settings = Window:MakeTab({ Name = "Settings", Icon = "settings" })
OrionLib:SetConfigTab("Settings")

task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)

OrionLib:Init()
```

## License

MIT
