# BetaOrion

Lightweight UI library for Roblox scripts, Orion / BetterOrion style.

## Installation

```lua
local OrionLib = loadstring(game:HttpGet("https://gist.githubusercontent.com/Polinorsik/d9442cbecdf1893b527ffd8d1a452c6b/raw/16616fdd2894c732383e39212658d59fb17e4a59/betaorion"))()
```

## Quick start

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({
    Name = "My Script",
    SubName = "v1.0",
    ToggleUIKey = Enum.KeyCode.RightShift,
})

local Tab = Window:MakeTab({ Name = "Main", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Actions", Side = "Left" })

Sec:AddButton({
    Name = "Click me",
    Callback = function()
        OrionLib:MakeNotification({ Name = "Hi", Content = "Works!", Time = 3 })
    end,
})

OrionLib:Init()
```

## API

### `OrionLib`

| Function | Description |
|---|---|
| `OrionLib:MakeWindow(Config)` | Create a window. Returns `Window`. |
| `OrionLib:MakeNotification(Config)` | Show a notification. |
| `OrionLib:Init()` | Show the window. |
| `OrionLib:Destroy()` | Destroy the window and everything inside. |
| `OrionLib:IsRunning()` | `true` / `false` — whether the window is alive. |
| `OrionLib:SetConfigTab(TabName)` | Populate the given tab with the config system. |
| `OrionLib:SetNotifyingState({Enabled, Printing})` | Toggle notifications and console printing. |
| `OrionLib:SetCornerRadius(n)` | Window corner radius. |
| `OrionLib:SaveAndLoadSizes()` | Auto-save window size and position. |
| `OrionLib:LoadAutoloadConfigs()` | Load the autoload config. |

**Properties:**

- `OrionLib.Flags` — table `[flag] = element`
- `OrionLib.SelectedTheme` — current theme
- `OrionLib.ToggleUIKey` — window toggle key

### `MakeWindow(Config)`

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

### `MakeNotification(Config)`

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

### `Window`

| Function | Description |
|---|---|
| `Window:MakeTab(Config)` | Create a tab. |
| `Window:SetSize(UDim2)` | Window size. |
| `Window:SetColor(Color3)` | Window color. |
| `Window:SetTransparency(n)` | Transparency. |
| `Window:SetStrokeColor(Color3)` | Stroke color. |
| `Window:SetStrokeTransparency(n)` | Stroke transparency. |
| `Window:SetTextColor(Color3)` | Text color. |
| `Window:SetTextTransparency(n)` | Text transparency. |
| `Window:SetIconColor(Color3)` | Tab icon color. |
| `Window:SetToggleKey(key)` | Window toggle key. |
| `Window:SetThemeColor(theme, elem, val)` | Change theme color. |
| `Window:SetThemeTransparency(theme, elem, n)` | Change theme transparency. |
| `Window:NewUI(bool)` | New style. |
| `Window:SetMainCorners(n)` | Corner radius of main elements. |
| `Window:SetElementsCorners(n)` | Corner radius of elements. |
| `Window:SetBackground(url)` | Background by URL. |
| `Window:SetBackgroundTransparency(n)` | Background transparency. |
| `Window:SetBackgroundVisibility(bool)` | Background visibility. |
| `Window:SetWatermarkText(str)` | Watermark text. |
| `Window:SetWatermarkVisibility(bool)` | Watermark visibility. |
| `Window:SetWatermarkColor(c)` | Watermark color. |
| `Window:SetWatermarkTextColor(c)` | Watermark text color. |
| `Window:SetWatermarkIconColor(c)` | Watermark icon color. |
| `Window:SetWatermarkTransparency(n)` | Watermark transparency. |
| `Window:SetWatermarkPosition(UDim2)` | Watermark position. |
| `Window:DestroyWatermark()` | Remove the watermark. |
| `Window:DestroyElement(flag)` | Remove an element by flag. |
| `Window:GetToggleUIKey()` | Get the window toggle key. |

### `MakeTab(Config)`

| Field | Default |
|---|---|
| `Name` | `"Tab"` |
| `Icon` | `""` |
| `PremiumOnly` | `false` |

Returns **Tab**.

### `Tab:AddSection(Config)`

| Field | Default |
|---|---|
| `Name` | `"Section"` |
| `Side` | `"Left"` |

Returns **Section**.

## Section elements

### `Section:AddLabel(Text)`

| Field | Default |
|---|---|
| `Text` | `"Label"` |

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddParagraph(Title, Content)`

| Field | Default |
|---|---|
| `Title` | `"Text"` |
| `Content` | `"Content"` |

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddButton(Config)`

| Field | Default |
|---|---|
| `Name` | `"Button"` |
| `Callback` | `function() end` |
| `Icon` | `"rbxassetid://3944703587"` |
| `DoubleTap` | `false` |
| `TapDelay` | `0.5` |
| `Settings` | `false` |

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddToggle(Config)`

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

### `Section:AddSlider(Config)`

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

### `Section:AddDropdown(Config)`

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

### `Section:AddPlayersDropdown(Config)`

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

### `Section:AddBind(Config)`

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

### `Section:AddTextbox(Config)`

| Field | Default |
|---|---|
| `Name` | `"Textbox"` |
| `Default` | `""` |
| `TextDisappear` | `false` |
| `Callback` | `function(Text) end` |

**Methods:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddColorpicker(Config)`

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

## Config system

```lua
local Settings = Window:MakeTab({ Name = "Settings", Icon = "settings" })
OrionLib:SetConfigTab("Settings")
```

`SetConfigTab` populates the tab with:

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
Sec:AddToggle({
    Name = "ESP",
    Flag = "esp_enabled",
    Save = true,
    Callback = function(v) end,
})
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

## Notifications

```lua
OrionLib:MakeNotification({
    Name = "Loaded",
    Content = "Script ready",
    Image = "check",
    Time = 5,
    Color = Color3.fromRGB(25, 25, 25),
    TextColor = Color3.new(1, 1, 1),
    Sound = "",
    SoundVolume = 1,
})
```

```lua
OrionLib:SetNotifyingState({
    Enabled = true,
    Printing = true,
})
```

## Full example

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({
    Name = "Demo",
    SubName = "v1.0",
    Size = UDim2.fromOffset(700, 450),
    ToggleUIKey = Enum.KeyCode.RightShift,
    ShowIcon = true,
    Icon = "moon",
    FreeMouse = true,
    WatermarkConfig = {
        Enabled = true,
        Visible = true,
        ShowFPS = true,
        ShowPing = true,
        ShowName = true,
        ShowClockTime = true,
        Icon = "activity",
    },
})

local HomeTab = Window:MakeTab({ Name = "Home", Icon = "home" })
local VisualsTab = Window:MakeTab({ Name = "Visuals", Icon = "eye" })
local MiscTab = Window:MakeTab({ Name = "Misc", Icon = "box" })
local Settings = Window:MakeTab({ Name = "Settings", Icon = "settings" })

local HomeSec = HomeTab:AddSection({ Name = "Info", Side = "Left" })
HomeSec:AddParagraph("Welcome", "Demo script")
HomeSec:AddLabel("Status: running")

local EspSec = VisualsTab:AddSection({ Name = "ESP", Side = "Left" })
EspSec:AddToggle({
    Name = "ESP Enabled",
    Default = false,
    Flag = "esp_enabled",
    Save = true,
    Callback = function(v) print("ESP:", v) end,
})
EspSec:AddColorpicker({
    Name = "ESP Color",
    Default = Color3.fromRGB(255, 80, 80),
    Flag = "esp_color",
    Save = true,
    Callback = function(c, t) print("Color:", c, "Transparency:", t) end,
})

local MiscSec = MiscTab:AddSection({ Name = "Actions", Side = "Left" })
MiscSec:AddButton({
    Name = "Notify",
    Callback = function()
        OrionLib:MakeNotification({ Name = "Hi", Content = "It works!", Time = 3 })
    end,
})
MiscSec:AddSlider({
    Name = "Speed",
    Min = 1, Max = 100, Default = 16, Increment = 1,
    Flag = "speed",
    Save = true,
    Callback = function(v) print("Speed:", v) end,
})
MiscSec:AddPlayersDropdown({
    Name = "Target",
    Search = true,
    Flag = "target",
    Save = true,
    Callback = function(v) print("Target:", v) end,
})
MiscSec:AddBind({
    Name = "Toggle ESP",
    Default = Enum.KeyCode.F,
    Flag = "bind_esp",
    Save = true,
    Callback = function()
        local esp = OrionLib.Flags["esp_enabled"]
        if esp then esp:Set(not esp.Value) end
    end,
})

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
