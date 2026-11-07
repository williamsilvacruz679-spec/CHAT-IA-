# CHAT-IA-

Interface de conversa em Roblox com visual inspirado no ChatGPT. O script cria uma janela de chat e exibe uma mensagem informativa; para obter respostas reais, conecte-o a um serviço de IA por meio de um backend seguro.

```lua
-- CHATGPT AI | DELTA EXECUTOR
-- Interface de conversa

local Players = game:GetService("Players")
local CoreGui = game:GetService("CoreGui")

local player = Players.LocalPlayer

local old = CoreGui:FindFirstChild("ChatGPT_AI")
if old then
    old:Destroy()
end

local gui = Instance.new("ScreenGui")
gui.Name = "ChatGPT_AI"
gui.Parent = CoreGui
gui.ResetOnSpawn = false

local main = Instance.new("Frame")
main.Size = UDim2.new(0, 430, 0, 330)
main.Position = UDim2.new(0.5, -215, 0.5, -165)
main.BackgroundColor3 = Color3.fromRGB(32, 33, 35)
main.Parent = gui

Instance.new("UICorner", main).CornerRadius =
    UDim.new(0, 12)

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 45)
title.BackgroundColor3 = Color3.fromRGB(25, 26, 28)
title.Text = "ChatGPT AI"
title.TextColor3 = Color3.new(1,1,1)
title.TextSize = 22
title.Font = Enum.Font.GothamBold
title.Parent = main

local chat = Instance.new("ScrollingFrame")
chat.Size = UDim2.new(1, -20, 1, -115)
chat.Position = UDim2.new(0, 10, 0, 55)
chat.BackgroundColor3 = Color3.fromRGB(40, 41, 43)
chat.BorderSizePixel = 0
chat.CanvasSize = UDim2.new(0,0,0,0)
chat.Parent = main

local layout = Instance.new("UIListLayout")
layout.Padding = UDim.new(0, 8)
layout.Parent = chat

local input = Instance.new("TextBox")
input.Size = UDim2.new(1, -100, 0, 40)
input.Position = UDim2.new(0, 10, 1, -50)
input.PlaceholderText = "Pergunte alguma coisa..."
input.Text = ""
input.TextColor3 = Color3.new(1,1,1)
input.BackgroundColor3 = Color3.fromRGB(55,56,58)
input.Parent = main

local send = Instance.new("TextButton")
send.Size = UDim2.new(0, 75, 0, 40)
send.Position = UDim2.new(1, -85, 1, -50)
send.Text = "ENVIAR"
send.TextColor3 = Color3.new(1,1,1)
send.BackgroundColor3 = Color3.fromRGB(16,163,127)
send.Parent = main

local function message(text, color)
    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, -15, 0, 45)
    label.BackgroundTransparency = 1
    label.Text = text
    label.TextColor3 = color
    label.TextSize = 14
    label.TextWrapped = true
    label.Font = Enum.Font.Gotham
    label.Parent = chat

    chat.CanvasSize = UDim2.new(0,0,0,layout.AbsoluteContentSize.Y + 10)
    chat.CanvasPosition = Vector2.new(0, chat.AbsoluteCanvasSize.Y)
end

send.MouseButton1Click:Connect(function()
    local question = input.Text

    if question == "" then return end

    message("Você: " .. question, Color3.new(1,1,1))
    input.Text = ""

    message("IA: Interface criada! Conecte uma API de inteligência artificial para receber respostas reais.", Color3.fromRGB(16,200,150))
end)

message("Olá! Bem-vindo ao ChatGPT AI.", Color3.fromRGB(16,200,150))
```
