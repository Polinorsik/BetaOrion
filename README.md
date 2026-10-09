# BetaOrion / BetaOrion

Lightweight UI library for Roblox / Лёгкая UI-библиотека для Roblox

## Installation / Установка

```lua
local OrionLib = loadstring(game:HttpGet("https://gist.githubusercontent.com/Polinorsik/d9442cbecdf1893b527ffd8d1a452c6b/raw/16616fdd2894c732383e39212658d59fb17e4a59/betaorion"))()
```

## Quick Start / Быстрый старт

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({ Name = "My Script / Мой скрипт", ToggleUIKey = Enum.KeyCode.RightShift })
local Tab = Window:MakeTab({ Name = "Main / Главная", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Actions / Действия", Side = "Left" })

Sec:AddButton({
    Name = "Click me / Нажми меня",
    Callback = function() end,
})

OrionLib:Init()
```

---

## OrionLib

### MakeWindow / Создать окно

```lua
OrionLib:MakeWindow(Config)
```

**Example / Пример:**

```lua
local Window = OrionLib:MakeWindow({ Name = "My Script / Мой скрипт", SubName = "v1.0" })
```

**Window Configuration / Настройки окна**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Better Orion"` | Any / Любое |
| `SubName` | string | `""` | Any / Любое |
| `Size` | UDim2 | `600x400` | Any UDim2 |
| `MinSize` | UDim2 | `400x200` | Any UDim2 |
| `MaxSize` | UDim2 | `4000x2000` | Any UDim2 |
| `IntroEnabled` | bool | `false` | `true`, `false` |
| `IntroText` | string | `"Better Orion"` | Any / Любое |
| `IntroIcon` | string | — | Lucide name |
| `ShowIcon` | bool | `false` | `true`, `false` |
| `Icon` | string | — | Lucide name / rbxassetid |
| `Transparency` | number | `0.35` | `0` – `1` |
| `ToggleUIKey` | Enum.KeyCode | `Enum.KeyCode.Tab` | Any KeyCode |
| `SearchBar` | bool | `false` | `true`, `false` |
| `FreeMouse` | bool | `true` | `true`, `false` |
| `NewUI` | bool | `false` | `true`, `false` |
| `BackgroundURL` | string | `""` | Any URL |
| `BackgroundTransparency` | number | `0.2` | `0` – `1` |
| `WatermarkConfig` | table | `{...}` | `{Enabled, Visible, ShowFPS, ShowPing, ShowName, ShowClockTime, Icon}` |

### MakeNotification / Показать уведомление

```lua
OrionLib:MakeNotification(Config)
```

**Example / Пример:**

```lua
OrionLib:MakeNotification({ Name = "Loaded / Загружено", Content = "Ready / Готово", Time = 5 })
```

**Notification Configuration / Настройки уведомления**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Notification Title"` | Any / Любое |
| `Content` | string | `"Notification Content"` | Any / Любое |
| `Image` | string | `"server"` | Lucide name |
| `Time` | number | `5` | Any positive / Любое положительное |
| `Color` | Color3 | theme color / цвет темы | Any Color3 |
| `TextColor` | Color3 | theme color / цвет темы | Any Color3 |
| `Sound` | string | `""` | rbxassetid |
| `SoundVolume` | number | `1` | `0` – `10` |

### Init / Показать окно

```lua
OrionLib:Init()
```

**Example / Пример:**

```lua
OrionLib:Init()
```

No arguments. Shows the window. / Без аргументов. Показывает окно.

### Destroy / Уничтожить окно

```lua
OrionLib:Destroy()
```

**Example / Пример:**

```lua
OrionLib:Destroy()
```

No arguments. Destroys the window and everything inside. / Без аргументов. Уничтожает окно и всё внутри.

### IsRunning / Проверить, живо ли окно

```lua
OrionLib:IsRunning()
```

**Example / Пример:**

```lua
if OrionLib:IsRunning() then
    print("Alive / Живо")
end
```

Returns `true` / `false`. / Возвращает `true` / `false`.

### SetConfigTab / Наполнить таб конфиг-системой

```lua
OrionLib:SetConfigTab(TabName)
```

**Example / Пример:**

```lua
local Settings = Window:MakeTab({ Name = "Settings / Настройки", Icon = "settings" })
OrionLib:SetConfigTab("Settings / Настройки")
```

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `TabName` | string | — | Name of existing tab / Имя существующего таба |

### SetNotifyingState / Управление уведомлениями

```lua
OrionLib:SetNotifyingState(Config)
```

**Example / Пример:**

```lua
OrionLib:SetNotifyingState({ Enabled = true, Printing = true })
```

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Enabled` | bool | `true` | `true`, `false` |
| `Printing` | bool | `true` | `true`, `false` |

### SetCornerRadius / Скругление окна

```lua
OrionLib:SetCornerRadius(n)
```

**Example / Пример:**

```lua
OrionLib:SetCornerRadius(10)
```

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `n` | number | — | `0` – `20` |

### SaveAndLoadSizes / Сохранить размеры

```lua
OrionLib:SaveAndLoadSizes()
```

**Example / Пример:**

```lua
OrionLib:SaveAndLoadSizes()
```

No arguments. / Без аргументов.

### LoadAutoloadConfigs / Загрузить автоконфиг

```lua
OrionLib:LoadAutoloadConfigs()
```

**Example / Пример:**

```lua
task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)
```

**Properties / Свойства:**

- `OrionLib.Flags` — table `[flag] = element` / таблица `[flag] = element`
- `OrionLib.SelectedTheme` — current theme / текущая тема
- `OrionLib.ToggleUIKey` — window toggle key / клавиша окна

---

## Window / Окно

### MakeTab / Создать таб

```lua
Window:MakeTab(Config)
```

**Example / Пример:**

```lua
local Tab = Window:MakeTab({ Name = "Main / Главная", Icon = "home" })
```

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Tab"` | Any / Любое |
| `Icon` | string | `""` | Lucide name / rbxassetid |
| `PremiumOnly` | bool | `false` | `true`, `false` |

### SetSize / Установить размер

```lua
Window:SetSize(UDim2)
```

**Example / Пример:**

```lua
Window:SetSize(UDim2.fromOffset(800, 500))
```

### SetColor / Установить цвет

```lua
Window:SetColor(Color3)
```

**Example / Пример:**

```lua
Window:SetColor(Color3.fromRGB(25, 25, 25))
```

### SetTransparency / Прозрачность

```lua
Window:SetTransparency(n)
```

**Example / Пример:**

```lua
Window:SetTransparency(0.2)
```

### SetStrokeColor / Цвет обводки

```lua
Window:SetStrokeColor(Color3)
```

**Example / Пример:**

```lua
Window:SetStrokeColor(Color3.fromRGB(80, 150, 20))
```

### SetStrokeTransparency / Прозрачность обводки

```lua
Window:SetStrokeTransparency(n)
```

**Example / Пример:**

```lua
Window:SetStrokeTransparency(0.5)
```

### SetTextColor / Цвет текста

```lua
Window:SetTextColor(Color3)
```

**Example / Пример:**

```lua
Window:SetTextColor(Color3.fromRGB(240, 240, 240))
```

### SetTextTransparency / Прозрачность текста

```lua
Window:SetTextTransparency(n)
```

**Example / Пример:**

```lua
Window:SetTextTransparency(0)
```

### SetIconColor / Цвет иконок

```lua
Window:SetIconColor(Color3)
```

**Example / Пример:**

```lua
Window:SetIconColor(Color3.fromRGB(255, 255, 255))
```

### SetToggleKey / Клавиша окна

```lua
Window:SetToggleKey(key)
```

**Example / Пример:**

```lua
Window:SetToggleKey(Enum.KeyCode.RightShift)
```

### SetThemeColor / Сменить цвет темы

```lua
Window:SetThemeColor(theme, elem, val)
```

**Example / Пример:**

```lua
Window:SetThemeColor("Default", "Main", { Color = Color3.fromRGB(20, 20, 20), Transparency = 0.35 })
```

### SetThemeTransparency / Сменить прозрачность темы

```lua
Window:SetThemeTransparency(theme, elem, n)
```

**Example / Пример:**

```lua
Window:SetThemeTransparency("Default", "Stroke", 0.5)
```

### NewUI / Новый стиль

```lua
Window:NewUI(bool)
```

**Example / Пример:**

```lua
Window:NewUI(true)
```

### SetMainCorners / Скругления главных элементов

```lua
Window:SetMainCorners(n)
```

**Example / Пример:**

```lua
Window:SetMainCorners(12)
```

### SetElementsCorners / Скругления элементов

```lua
Window:SetElementsCorners(n)
```

**Example / Пример:**

```lua
Window:SetElementsCorners(8)
```

### SetBackground / Фон

```lua
Window:SetBackground(url)
```

**Example / Пример:**

```lua
Window:SetBackground("rbxassetid://123456789")
```

### SetBackgroundTransparency / Прозрачность фона

```lua
Window:SetBackgroundTransparency(n)
```

**Example / Пример:**

```lua
Window:SetBackgroundTransparency(0.3)
```

### SetBackgroundVisibility / Видимость фона

```lua
Window:SetBackgroundVisibility(bool)
```

**Example / Пример:**

```lua
Window:SetBackgroundVisibility(true)
```

### SetWatermarkText / Текст водяного знака

```lua
Window:SetWatermarkText(str)
```

**Example / Пример:**

```lua
Window:SetWatermarkText("My Cheat / Мой чит | v1.0")
```

### SetWatermarkVisibility / Видимость водяного знака

```lua
Window:SetWatermarkVisibility(bool)
```

**Example / Пример:**

```lua
Window:SetWatermarkVisibility(true)
```

### SetWatermarkColor / Цвет водяного знака

```lua
Window:SetWatermarkColor(c)
```

**Example / Пример:**

```lua
Window:SetWatermarkColor(Color3.fromRGB(25, 25, 25))
```

### SetWatermarkTextColor / Цвет текста водяного знака

```lua
Window:SetWatermarkTextColor(c)
```

**Example / Пример:**

```lua
Window:SetWatermarkTextColor(Color3.new(1, 1, 1))
```

### SetWatermarkIconColor / Цвет иконки водяного знака

```lua
Window:SetWatermarkIconColor(c)
```

**Example / Пример:**

```lua
Window:SetWatermarkIconColor(Color3.fromRGB(255, 200, 50))
```

### SetWatermarkTransparency / Прозрачность водяного знака

```lua
Window:SetWatermarkTransparency(n)
```

**Example / Пример:**

```lua
Window:SetWatermarkTransparency(0.3)
```

### SetWatermarkPosition / Позиция водяного знака

```lua
Window:SetWatermarkPosition(UDim2)
```

**Example / Пример:**

```lua
Window:SetWatermarkPosition(UDim2.new(0, 15, 0, 15))
```

### DestroyWatermark / Удалить водяной знак

```lua
Window:DestroyWatermark()
```

**Example / Пример:**

```lua
Window:DestroyWatermark()
```

### DestroyElement / Удалить элемент по флагу

```lua
Window:DestroyElement(flag)
```

**Example / Пример:**

```lua
Window:DestroyElement("esp_enabled")
```

### GetToggleUIKey / Получить клавишу окна

```lua
Window:GetToggleUIKey()
```

**Example / Пример:**

```lua
local key = Window:GetToggleUIKey()
```

---

## Tab / Таб

### AddSection / Добавить секцию

```lua
Tab:AddSection()
```

**Example / Пример:**

```lua
local Section = Tab:AddSection({ Name = "Main / Главная", Side = "Left" })
```

**Section Configuration / Настройки секции**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Section"` | Any / Любое |
| `Side?` | string | `"Left"` | `"Left"`, `"Right"` |

---

## Section — AddLabel / Добавить метку

```lua
Section:AddLabel(Text)
```

**Example / Пример:**

```lua
Section:AddLabel("Status: running / Статус: работает")
```

**Methods / Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddParagraph / Добавить параграф

```lua
Section:AddParagraph(Title, Content)
```

**Example / Пример:**

```lua
Section:AddParagraph("Welcome / Добро пожаловать", "Demo script / Демо скрипт")
```

**Methods / Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddButton / Добавить кнопку

```lua
Section:AddButton(Config)
```

**Example / Пример:**

```lua
Section:AddButton({
    Name = "Notify / Уведомить",
    Callback = function() end,
})
```

**Button Configuration / Настройки кнопки**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Button"` | Any / Любое |
| `Callback` | function | `function() end` | Any function |
| `Icon` | string | `"rbxassetid://3944703587"` | rbxassetid |
| `DoubleTap` | bool | `false` | `true`, `false` |
| `TapDelay` | number | `0.5` | Any positive |
| `Settings` | bool | `false` | `true`, `false` |

**Methods / Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddToggle / Добавить тогл

```lua
Section:AddToggle(Config)
```

**Example / Пример:**

```lua
Section:AddToggle({
    Name = "ESP",
    Default = false,
    Flag = "esp_enabled",
    Save = true,
    Callback = function(Value) end,
})
```

**Toggle Configuration / Настройки тогла**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Toggle"` | Any / Любое |
| `Default` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(Value) end` | Any function |
| `Color` | Color3 | `Color3.fromRGB(50,50,50)` | Any Color3 |
| `Flag` | string | `nil` | Any unique string |
| `Save` | bool | `false` | `true`, `false` |
| `Binded` | bool | `false` | `true`, `false` |
| `DefaultBind` | string | `""` | Any key name |
| `Settings` | bool | `false` | `true`, `false` |

**Properties / Свойства:** `Toggle.Value` (bool), `Toggle.BindValue` (string), `Toggle.Type = "Toggle"`

**Methods / Методы:** `:Set(bool)`, `:SetBind(key)`, `:SetName(str)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`, `:ChangeVisibility(bool)`

## Section — AddSlider / Добавить слайдер

```lua
Section:AddSlider(Config)
```

**Example / Пример:**

```lua
Section:AddSlider({
    Name = "Speed / Скорость",
    Min = 1, Max = 100, Default = 16, Increment = 1,
    ValueName = "spd",
    Flag = "speed",
    Save = true,
    Callback = function(Value) end,
})
```

**Slider Configuration / Настройки слайдера**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Slider"` | Any / Любое |
| `Min` | number | `0` | Any number |
| `Max` | number | `100` | Any number |
| `Increment` | number | `1` | Any positive |
| `Default` | number | `50` | `Min` – `Max` |
| `ValueName` | string | `""` | Any / Любое |
| `Color` | Color3 | `Color3.fromRGB(50,50,50)` | Any Color3 |
| `Flag` | string | `nil` | Any unique string |
| `Save` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(Value) end` | Any function |
| `InputEndedCallback` | function | `function(Value) end` | Any function |

**Property / Свойство:** `Slider.Value` (number)

**Methods / Методы:** `:Set(number)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddDropdown / Добавить дропдаун

```lua
Section:AddDropdown(Config)
```

**Example / Пример:**

```lua
Section:AddDropdown({
    Name = "Mode / Режим",
    Options = {"Legit", "Rage", "Silent"},
    Default = "Legit",
    Flag = "aim_mode",
    Save = true,
    Callback = function(Value) end,
})
```

**Dropdown Configuration / Настройки дропдауна**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Dropdown"` | Any / Любое |
| `Options` | table | `{}` | Array of strings or `{Name, Image}` |
| `Multi` | bool | `false` | `true`, `false` |
| `Default` | string/table | `Multi and {} or ""` | Depends on Multi |
| `MaxSize` | number | `5` | Any positive |
| `Search` | bool | `false` | `true`, `false` |
| `OptionsSize` | number | `28` | Any positive |
| `Flag` | string | `nil` | Any unique string |
| `Save` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(Value) end` | Any function |

**Property / Свойство:** `Dropdown.Value` — string (single) or table (multi)

**Methods / Методы:** `:Set(value)`, `:Refresh(options, delete)`, `:ChangeVisibility(bool)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`

## Section — AddPlayersDropdown / Дропдаун игроков

```lua
Section:AddPlayersDropdown(Config)
```

**Example / Пример:**

```lua
Section:AddPlayersDropdown({
    Name = "Target / Цель",
    Search = true,
    Flag = "target_player",
    Save = true,
    Callback = function(Value) end,
})
```

**Players Dropdown Configuration / Настройки дропдауна игроков**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Dropdown"` | Any / Любое |
| `Multi` | bool | `false` | `true`, `false` |
| `MaxSize` | number | `5` | Any positive |
| `Search` | bool | `false` | `true`, `false` |
| `OptionsSize` | number | `28` | Any positive |
| `Flag` | string | `nil` | Any unique string |
| `Save` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(Value) end` | Any function |

**Property / Свойство:** `Dropdown.Value` — string (username) or nil

**Methods / Методы:** `:Set(value)`, `:Refresh()`, `:ChangeVisibility(bool)`, `:SetColor(c)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTransparency(n)`

## Section — AddBind / Добавить бинд

```lua
Section:AddBind(Config)
```

**Example / Пример:**

```lua
Section:AddBind({
    Name = "Fly / Полёт",
    Default = Enum.KeyCode.F,
    Hold = false,
    Flag = "bind_fly",
    Save = true,
    Callback = function(holding) end,
})
```

**Bind Configuration / Настройки бинда**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Bind"` | Any / Любое |
| `Default` | string | `""` | Any key name |
| `Hold` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(holding) end` | Any function |
| `Flag` | string | `nil` | Any unique string |
| `Save` | bool | `false` | `true`, `false` |
| `UIBind` | bool | `false` | `true`, `false` |
| `Button` | bool | `false` | `true`, `false` |
| `ButtonIcon` | string | `"rbxassetid://3944703587"` | rbxassetid |
| `DoubleTap` | bool | `false` | `true`, `false` |
| `TapDelay` | number | `0.5` | Any positive |
| `Color` | Color3 | `Color3.fromRGB(50,50,50)` | Any Color3 |

**Property / Свойство:** `Bind.Value` (string, key name)

**Methods / Методы:** `:Set(key)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddTextbox / Добавить текстовое поле

```lua
Section:AddTextbox(Config)
```

**Example / Пример:**

```lua
Section:AddTextbox({
    Name = "Message / Сообщение",
    Default = "",
    TextDisappear = false,
    Callback = function(Text) end,
})
```

**Textbox Configuration / Настройки текстового поля**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Textbox"` | Any / Любое |
| `Default` | string | `""` | Any / Любое |
| `TextDisappear` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(Text) end` | Any function |

**Methods / Методы:** `:Set(text)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

## Section — AddColorpicker / Добавить колорпикер

```lua
Section:AddColorpicker(Config)
```

**Example / Пример:**

```lua
Section:AddColorpicker({
    Name = "ESP Color / Цвет ESP",
    Default = Color3.fromRGB(255, 80, 80),
    DefaultTransparency = 0,
    Flag = "esp_color",
    Save = true,
    Callback = function(Color, Transparency) end,
})
```

**Colorpicker Configuration / Настройки колорпикера**

| Property / Свойство | Value Type / Тип | Default / По умолч. | Possible Values / Возможные значения |
|---|---|---|---|
| `Name` | string | `"Colorpicker"` | Any / Любое |
| `Default` | Color3 | `Color3.fromRGB(255,255,255)` | Any Color3 |
| `DefaultTransparency` | number | `0` | `0` – `1` |
| `Flag` | string | `nil` | Any unique string |
| `Save` | bool | `false` | `true`, `false` |
| `Callback` | function | `function(Color, Transparency) end` | Any function |

**Properties / Свойства:** `Colorpicker.Value` (Color3), `Colorpicker.TransparencyValue` (number)

**Methods / Методы:** `:Set(Color3, Transparency, notCallback)`, `:SetColor(c)`, `:SetStrokeColor(c)`, `:SetStrokeTransparency(n)`, `:SetTextColor(c)`, `:SetTextTransparency(n)`, `:SetTransparency(n)`

---

## Config System / Конфиг-система

```lua
local Settings = Window:MakeTab({ Name = "Settings / Настройки", Icon = "settings" })
OrionLib:SetConfigTab("Settings / Настройки")
```

**Populates the tab with / Наполняет таб:**

- Edit Theme — Window / Elements / Stroke / Text, New UI, Corner Radius / Редактор темы — цвета окна, элементов, обводки, текста, New UI, скругление.
- Edit Background — background list, Custom Background, Transparency / Редактор фона — список фонов, кастомный фон, прозрачность.
- Save Backgrounds — link, name, Save / Delete / Сохранение фонов — ссылка, имя, сохранить / удалить.
- Save Config — list, name, Load / Save / Delete / Autoload / Remove Autoload / Refresh / Сохранение конфигов — список, имя, загрузить / сохранить / удалить / автозагрузка / отключить автозагрузку / обновить.
- Save Themes — list, name, Load / Save / Delete / Autoload / Remove Autoload / Refresh / Сохранение тем — то же самое.

**Requires executor file functions / Требует файловые функции исполнителя:** `writefile`, `isfile`, `listfiles`, `readfile`, `isfolder`, `makefolder`, `getcustomasset`.

### Save Paths / Пути сохранения

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

### Flags / Флаги

```lua
Section:AddToggle({ Name = "ESP", Flag = "esp_enabled", Save = true, Callback = function(v) end })
```

`Save Config` stores the flag's `Value` and `BindValue`. / `Save Config` сохраняет `Value` и `BindValue` флага.

`Load Config` restores them via `:Set(v.Value)` and `:SetBind(v.BindValue)`. / `Load Config` загружает их через `:Set(v.Value)` и `:SetBind(v.BindValue)`.

### Autoload / Автозагрузка

```lua
task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)
```

---

## Full Example / Полный пример

```lua
local OrionLib = loadstring(game:HttpGet("...betaorion"))()

local Window = OrionLib:MakeWindow({
    Name = "Demo / Демо",
    SubName = "v1.0",
    ToggleUIKey = Enum.KeyCode.RightShift,
    ShowIcon = true,
    Icon = "moon",
    FreeMouse = true,
})

local Tab = Window:MakeTab({ Name = "Main / Главная", Icon = "home" })
local Sec = Tab:AddSection({ Name = "Actions / Действия", Side = "Left" })

Sec:AddButton({
    Name = "Notify / Уведомить",
    Callback = function()
        OrionLib:MakeNotification({ Name = "Hi / Привет", Content = "It works! / Работает!", Time = 3 })
    end,
})

Sec:AddToggle({
    Name = "ESP",
    Default = false,
    Flag = "esp_enabled",
    Save = true,
    Callback = function(v) print("ESP:", v) end,
})

local Settings = Window:MakeTab({ Name = "Settings / Настройки", Icon = "settings" })
OrionLib:SetConfigTab("Settings / Настройки")

task.spawn(function()
    pcall(function()
        OrionLib:LoadAutoloadConfigs()
    end)
end)

OrionLib:Init()
```

## License / Лицензия

MIT
