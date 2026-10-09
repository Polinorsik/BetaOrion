# BetaOrion (RU)

Лёгкая UI-библиотека для Roblox-скриптов в стиле Orion / BetterOrion.

## Установка

```lua
local OrionLib = loadstring(game:HttpGet("https://gist.githubusercontent.com/Polinorsik/d9442cbecdf1893b527ffd8d1a452c6b/raw/16616fdd2894c732383e39212658d59fb17e4a59/betaorion"))()
```

## Быстрый старт

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({
    Name = "Мой скрипт",
    SubName = "v1.0",
    ToggleUIKey = Enum.KeyCode.RightShift,
})

local Tab = Window:MakeTab({ Name = "Главная", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Действия", Side = "Left" })

Sec:AddButton({
    Name = "Нажми меня",
    Callback = function()
        OrionLib:MakeNotification({ Name = "Привет", Content = "Работает!", Time = 3 })
    end,
})

OrionLib:Init()
```

## API

### `OrionLib`

| Функция | Описание |
|---|---|
| `OrionLib:MakeWindow(Config)` | Создать окно. Возвращает `Window`. |
| `OrionLib:MakeNotification(Config)` | Показать нотификацию. |
| `OrionLib:Init()` | Показать окно. |
| `OrionLib:Destroy()` | Уничтожить окно и всё содержимое. |
| `OrionLib:IsRunning()` | `true` / `false` — живо ли окно. |
| `OrionLib:SetConfigTab(TabName)` | Наполнить таб конфиг-системой. |
| `OrionLib:SetNotifyingState({Enabled, Printing})` | Вкл/выкл нотификации и вывод в консоль. |
| `OrionLib:SetCornerRadius(n)` | Скругление окна. |
| `OrionLib:SaveAndLoadSizes()` | Автосейв размеров и позиции окна. |
| `OrionLib:LoadAutoloadConfigs()` | Загрузить автозагружаемый конфиг. |

**Свойства:**

- `OrionLib.Flags` — таблица `[flag] = element`
- `OrionLib.SelectedTheme` — текущая тема
- `OrionLib.ToggleUIKey` — клавиша окна

### `MakeWindow(Config)`

| Поле | Тип | По умолчанию |
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

| Поле | По умолчанию |
|---|---|
| `Name` | `"Notification Title"` |
| `Content` | `"Notification Content"` |
| `Image` | `"server"` |
| `Time` | `5` |
| `Color` | цвет темы |
| `TextColor` | цвет темы |
| `Sound` | `""` |
| `SoundVolume` | `1` |

### `Window`

| Функция | Описание |
|---|---|
| `Window:MakeTab(Config)` | Создать таб. |
| `Window:SetSize(UDim2)` | Размер окна. |
| `Window:SetColor(Color3)` | Цвет окна. |
| `Window:SetTransparency(n)` | Прозрачность. |
| `Window:SetStrokeColor(Color3)` | Цвет обводки. |
| `Window:SetStrokeTransparency(n)` | Прозрачность обводки. |
| `Window:SetTextColor(Color3)` | Цвет текста. |
| `Window:SetTextTransparency(n)` | Прозрачность текста. |
| `Window:SetIconColor(Color3)` | Цвет иконок табов. |
| `Window:SetToggleKey(key)` | Клавиша окна. |
| `Window:SetThemeColor(theme, elem, val)` | Сменить цвет темы. |
| `Window:SetThemeTransparency(theme, elem, n)` | Сменить прозрачность темы. |
| `Window:NewUI(bool)` | Новый стиль. |
| `Window:SetMainCorners(n)` | Скругления главных элементов. |
| `Window:SetElementsCorners(n)` | Скругления элементов. |
| `Window:SetBackground(url)` | Фон по URL. |
| `Window:SetBackgroundTransparency(n)` | Прозрачность фона. |
| `Window:SetBackgroundVisibility(bool)` | Видимость фона. |
| `Window:SetWatermarkText(str)` | Текст водяного знака. |
| `Window:SetWatermarkVisibility(bool)` | Видимость. |
| `Window:SetWatermarkColor(c)` | Цвет. |
| `Window:SetWatermarkTextColor(c)` | Цвет текста. |
| `Window:SetWatermarkIconColor(c)` | Цвет иконки. |
| `Window:SetWatermarkTransparency(n)` | Прозрачность. |
| `Window:SetWatermarkPosition(UDim2)` | Позиция. |
| `Window:DestroyWatermark()` | Удалить водяной знак. |
| `Window:DestroyElement(flag)` | Удалить элемент по флагу. |
| `Window:GetToggleUIKey()` | Клавиша окна. |

### `MakeTab(Config)`

| Поле | По умолчанию |
|---|---|
| `Name` | `"Tab"` |
| `Icon` | `""` |
| `PremiumOnly` | `false` |

Возвращает **Tab**.

### `Tab:AddSection(Config)`

| Поле | По умолчанию |
|---|---|
| `Name` | `"Section"` |
| `Side` | `"Left"` |

Возвращает **Section**.

## Элементы Section

### `Section:AddLabel(Text)`

| Поле | По умолчанию |
|---|---|
| `Text` | `"Label"` |

**Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddParagraph(Title, Content)`

| Поле | По умолчанию |
|---|---|
| `Title` | `"Text"` |
| `Content` | `"Content"` |

**Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddButton(Config)`

| Поле | По умолчанию |
|---|---|
| `Name` | `"Button"` |
| `Callback` | `function() end` |
| `Icon` | `"rbxassetid://3944703587"` |
| `DoubleTap` | `false` |
| `TapDelay` | `0.5` |
| `Settings` | `false` |

**Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddToggle(Config)`

| Поле | По умолчанию |
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

**Свойства:** `Toggle.Value` (bool), `Toggle.BindValue` (string), `Toggle.Type = "Toggle"`

**Методы:** `:Set(bool)`, `:SetBind(key)`, `:SetName(str)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`, `:ChangeVisibility(bool)`

### `Section:AddSlider(Config)`

| Поле | По умолчанию |
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

**Свойство:** `Slider.Value` (number)

**Методы:** `:Set(number)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddDropdown(Config)`

| Поле | По умолчанию |
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

**Свойство:** `Dropdown.Value` — string (single) или table (multi)

**Методы:** `:Set(value)`, `:Refresh(options, delete)`, `:ChangeVisibility(bool)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`

### `Section:AddPlayersDropdown(Config)`

| Поле | По умолчанию |
|---|---|
| `Name` | `"Dropdown"` |
| `Multi` | `false` |
| `MaxSize` | `5` |
| `Search` | `false` |
| `OptionsSize` | `28` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Callback` | `function(Value) end` |

**Свойство:** `Dropdown.Value` — string (ник) или nil

**Методы:** `:Set(value)`, `:Refresh()`, `:ChangeVisibility(bool)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`

### `Section:AddBind(Config)`

| Поле | По умолчанию |
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

**Свойство:** `Bind.Value` (string, имя клавиши)

**Методы:** `:Set(key)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddTextbox(Config)`

| Поле | По умолчанию |
|---|---|
| `Name` | `"Textbox"` |
| `Default` | `""` |
| `TextDisappear` | `false` |
| `Callback` | `function(Text) end` |

**Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

### `Section:AddColorpicker(Config)`

| Поле | По умолчанию |
|---|---|
| `Name` | `"Colorpicker"` |
| `Default` | `Color3.fromRGB(255,255,255)` |
| `DefaultTransparency` | `0` |
| `Flag` | `nil` |
| `Save` | `false` |
| `Callback` | `function(Color, Transparency) end` |

**Свойства:** `Colorpicker.Value` (Color3), `Colorpicker.TransparencyValue` (number)

**Методы:** `:Set(Color3, Transparency, notCallback)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Конфиг-система

```lua
local Settings = Window:MakeTab({ Name = "Настройки", Icon = "settings" })
OrionLib:SetConfigTab("Настройки")
```

`SetConfigTab` наполняет таб:

- Edit Theme — Window / Elements / Stroke / Text, New UI, Corner Radius.
- Edit Background — список фонов, Custom Background, Transparency.
- Save Backgrounds — ссылка, имя, Save / Delete.
- Save Config — список, имя, Load / Save / Delete / Autoload / Remove Autoload / Refresh.
- Save Themes — список, имя, Load / Save / Delete / Autoload / Remove Autoload / Refresh.

Требует файловых функций исполнителя: `writefile`, `isfile`, `listfiles`, `readfile`, `isfolder`, `makefolder`, `getcustomasset`.

### Пути сохранения

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

### Флаги

```lua
Sec:AddToggle({
    Name = "ESP",
    Flag = "esp_enabled",
    Save = true,
    Callback = function(v) end,
})
```

`Save Config` сохраняет `Value` и `BindValue` флага. `Load Config` загружает через `:Set(v.Value)` и `:SetBind(v.BindValue)`.

### Автозагрузка

```lua
task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)
```

## Уведомления

```lua
OrionLib:MakeNotification({
    Name = "Загружено",
    Content = "Скрипт готов",
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

---

# ПРИМЕРЫ ИСПОЛЬЗОВАНИЯ

## 1. Минимальный скрипт

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({ Name = "Minimal", ToggleUIKey = Enum.KeyCode.RightShift })
local Tab = Window:MakeTab({ Name = "Main", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Actions", Side = "Left" })

Sec:AddButton({
    Name = "Hello",
    Callback = function()
        OrionLib:MakeNotification({ Name = "Hi", Content = "Hello world!", Time = 3 })
    end,
})

OrionLib:Init()
```

## 2. Toggle с флагом (сохраняется)

```lua
Sec:AddToggle({
    Name = "Auto Sprint",
    Default = false,
    Flag = "auto_sprint",
    Save = true,
    Callback = function(Value)
        if Value then
            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 32
        else
            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 16
        end
    end,
})
```

## 3. Slider, изменяющий WalkSpeed

```lua
Sec:AddSlider({
    Name = "WalkSpeed",
    Min = 1, Max = 200, Default = 16, Increment = 1,
    ValueName = "speed",
    Flag = "walkspeed",
    Save = true,
    Callback = function(Value)
        local plr = game.Players.LocalPlayer
        if plr.Character and plr.Character:FindFirstChild("Humanoid") then
            plr.Character.Humanoid.WalkSpeed = Value
        end
    end,
})
```

## 4. Dropdown с режимами

```lua
Sec:AddDropdown({
    Name = "Mode",
    Options = {"Legit", "Rage", "Silent"},
    Default = "Legit",
    Flag = "aim_mode",
    Save = true,
    Callback = function(Value)
        print("Selected mode:", Value)
    end,
})
```

## 5. Multi-Dropdown с опциями

```lua
Sec:AddDropdown({
    Name = "Features",
    Options = {"ESP", "Aimbot", "Fly", "Noclip"},
    Multi = true,
    Default = {"ESP"},
    Flag = "features",
    Save = true,
    Callback = function(Values)
        for _, v in ipairs(Values) do
            print("Enabled:", v)
        end
    end,
})
```

## 6. Dropdown с иконками

```lua
Sec:AddDropdown({
    Name = "Weapon",
    Options = {
        {Name = "Sword", Image = "rbxassetid://123456789"},
        {Name = "Gun",   Image = "rbxassetid://987654321"},
        {Name = "Bow",   Image = "rbxassetid://111222333"},
    },
    Default = "Sword",
    Flag = "weapon",
    Callback = function(Value)
        print("Weapon:", Value)
    end,
})
```

## 7. Players dropdown (выбор игрока)

```lua
local selectedPlayer = nil

Sec:AddPlayersDropdown({
    Name = "Target",
    Search = true,
    Flag = "target_player",
    Save = true,
    Callback = function(Value)
        selectedPlayer = Value and game.Players:FindFirstChild(Value) or nil
        print("Target:", selectedPlayer and selectedPlayer.Name or "none")
    end,
})

Sec:AddButton({
    Name = "Kill target",
    Callback = function()
        if not selectedPlayer or not selectedPlayer.Character then return end
        local hum = selectedPlayer.Character:FindFirstChild("Humanoid")
        if hum then hum.Health = 0 end
    end,
})
```

## 8. Bind (горячая клавиша) с Hold

```lua
Sec:AddBind({
    Name = "Fly (hold)",
    Default = Enum.KeyCode.F,
    Hold = true,
    Flag = "bind_fly",
    Save = true,
    Callback = function(holding)
        local char = game.Players.LocalPlayer.Character
        if not char then return end
        local hrp = char:FindFirstChild("HumanoidRootPart")
        if not hrp then return end
        if holding then
            hrp.Velocity = Vector3.new(0, 50, 0)
        end
    end,
})
```

## 9. Textbox для ввода значения

```lua
local tpX, tpY, tpZ = 0, 0, 0

Sec:AddTextbox({
    Name = "X",
    Default = "0",
    Callback = function(Text)
        tpX = tonumber(Text) or 0
    end,
})
Sec:AddTextbox({
    Name = "Y",
    Default = "0",
    Callback = function(Text)
        tpY = tonumber(Text) or 0
    end,
})
Sec:AddTextbox({
    Name = "Z",
    Default = "0",
    Callback = function(Text)
        tpZ = tonumber(Text) or 0
    end,
})

Sec:AddButton({
    Name = "Teleport",
    Callback = function()
        local char = game.Players.LocalPlayer.Character
        if char and char:FindFirstChild("HumanoidRootPart") then
            char.HumanoidRootPart.CFrame = CFrame.new(tpX, tpY, tpZ)
        end
    end,
})
```

## 10. Colorpicker для ESP

```lua
local espColor = Color3.fromRGB(255, 80, 80)

Sec:AddColorpicker({
    Name = "ESP Color",
    Default = Color3.fromRGB(255, 80, 80),
    Flag = "esp_color",
    Save = true,
    Callback = function(Color, Transparency)
        espColor = Color
        print("Color:", Color, "Transparency:", Transparency)
    end,
})
```

## 11. Label и Paragraph

```lua
Sec:AddLabel("Status: running")
Sec:AddParagraph("About", "This is a demo script.\nClick buttons to test.")
```

## 12. Связка Toggle → обновление Label

```lua
local statusLabel = Sec:AddLabel("ESP: off")

Sec:AddToggle({
    Name = "ESP",
    Default = false,
    Flag = "esp",
    Callback = function(Value)
        statusLabel:Set("ESP: " .. (Value and "on" or "off"))
    end,
})
```

## 13. Динамический Bind для Toggle

```lua
Sec:AddToggle({
    Name = "Auto Sprint",
    Flag = "auto_sprint",
    Binded = true,
    DefaultBind = "F",
    Callback = function(v) print("sprint:", v) end,
})
```

## 14. Полный скрипт с настройками и автосейвом

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({
    Name = "My Cheat",
    SubName = "v1.0",
    Size = UDim2.fromOffset(700, 450),
    ToggleUIKey = Enum.KeyCode.RightShift,
    ShowIcon = true,
    Icon = "zap",
    FreeMouse = true,
    WatermarkConfig = {
        Enabled = true,
        Visible = true,
        ShowFPS = true,
        ShowName = true,
        Icon = "activity",
    },
})

local HomeTab = Window:MakeTab({ Name = "Home", Icon = "home" })
local MainTab = Window:MakeTab({ Name = "Main", Icon = "zap" })
local SettingsTab = Window:MakeTab({ Name = "Settings", Icon = "settings" })

local HomeSec = HomeTab:AddSection({ Name = "Info", Side = "Left" })
HomeSec:AddParagraph("Welcome", "My Cheat v1.0")
HomeSec:AddLabel("Status: ready")

local MainSec = MainTab:AddSection({ Name = "Player", Side = "Left" })
MainSec:AddSlider({
    Name = "WalkSpeed",
    Min = 1, Max = 200, Default = 16, Increment = 1,
    ValueName = "spd",
    Flag = "walkspeed",
    Save = true,
    Callback = function(v)
        local plr = game.Players.LocalPlayer
        if plr.Character and plr.Character:FindFirstChild("Humanoid") then
            plr.Character.Humanoid.WalkSpeed = v
        end
    end,
})
MainSec:AddToggle({
    Name = "Infinite Jump",
    Flag = "inf_jump",
    Save = true,
    Callback = function(v)
        if v then
            _G.inf_jump_conn = game:GetService("UserInputService").JumpRequest:Connect(function()
                local char = game.Players.LocalPlayer.Character
                if char and char:FindFirstChild("Humanoid") then
                    char.Humanoid:ChangeState(Enum.HumanoidStateType.Jumping)
                end
            end)
        else
            if _G.inf_jump_conn then _G.inf_jump_conn:Disconnect() end
        end
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

## 15. Кнопка с подтверждением (DoubleTap)

```lua
Sec:AddButton({
    Name = "Delete account",
    DoubleTap = true,
    TapDelay = 1,
    Callback = function()
        print("Confirmed!")
    end,
})
```

## 16. Использование флагов извне

```lua
Sec:AddToggle({ Name = "ESP", Flag = "esp", Save = true, Callback = function() end })
Sec:AddSlider({ Name = "Speed", Flag = "spd", Default = 16, Min = 1, Max = 100, Callback = function() end })

-- где-то в другом месте скрипта:
local espFlag = OrionLib.Flags["esp"]
local spdFlag = OrionLib.Flags["spd"]

print(espFlag.Value)   -- текущее значение toggle
espFlag:Set(true)      -- программно включить

print(spdFlag.Value)   -- текущее значение слайдера
spdFlag:Set(50)        -- программно установить
```

## 17. Удаление элемента по флагу

```lua
Sec:AddToggle({ Name = "Temp", Flag = "temp_toggle", Callback = function() end })

-- позже:
Window:DestroyElement("temp_toggle")
```

## 18. Скрыть/показать окно программно

```lua
-- скрыть
game.CoreGui.BetterOrion.MainWindow.Visible = false

-- показать
game.CoreGui.BetterOrion.MainWindow.Visible = true
```

## 19. Уведомление со звуком

```lua
OrionLib:MakeNotification({
    Name = "Alert",
    Content = "Enemy nearby!",
    Image = "alert-triangle",
    Time = 3,
    Sound = "rbxassetid://1234567890",
    SoundVolume = 0.5,
})
```

## 20. Смена темы программно

```lua
Window:SetColor(Color3.fromRGB(30, 30, 30))
Window:SetStrokeColor(Color3.fromRGB(80, 150, 20))
Window:SetTextColor(Color3.fromRGB(240, 240, 240))
Window:SetTransparency(0.2)
```

## License

MIT
