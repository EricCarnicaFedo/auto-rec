-- Criando ScreenGui para interface
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criando o quadro principal
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 300, 0, 200)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
mainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

-- Cantos arredondados
local uiCorner = Instance.new("UICorner")
uiCorner.CornerRadius = UDim.new(0, 12)
uiCorner.Parent = mainFrame

-- Criando botão de minimizar
local minimizeButton = Instance.new("TextButton")
minimizeButton.Size = UDim2.new(0, 30, 0, 30)
minimizeButton.Position = UDim2.new(1, -35, 0, 5)
minimizeButton.Text = "_"
minimizeButton.TextScaled = true
minimizeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
minimizeButton.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
minimizeButton.Parent = mainFrame

local uiCornerMinimize = Instance.new("UICorner")
uiCornerMinimize.CornerRadius = UDim.new(0, 6)
uiCornerMinimize.Parent = minimizeButton

-- Criando botão para começar recrutamento
local startButton = Instance.new("TextButton")
startButton.Size = UDim2.new(0, 250, 0, 50)
startButton.Position = UDim2.new(0.5, -125, 0.3, 0)
startButton.Text = "Começar Recrutamento"
startButton.TextScaled = true
startButton.TextColor3 = Color3.fromRGB(255, 255, 255)
startButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
startButton.Parent = mainFrame

local uiCornerStart = Instance.new("UICorner")
uiCornerStart.CornerRadius = UDim.new(0, 8)
uiCornerStart.Parent = startButton

-- Criando botão para parar recrutamento
local stopButton = Instance.new("TextButton")
stopButton.Size = UDim2.new(0, 250, 0, 50)
stopButton.Position = UDim2.new(0.5, -125, 0.6, 0)
stopButton.Text = "Parar Recrutamento"
stopButton.TextScaled = true
stopButton.TextColor3 = Color3.fromRGB(255, 255, 255)
stopButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
stopButton.Parent = mainFrame

local uiCornerStop = Instance.new("UICorner")
uiCornerStop.CornerRadius = UDim.new(0, 8)
uiCornerStop.Parent = stopButton

-- Texto de Powered by
local poweredByLabel = Instance.new("TextLabel")
poweredByLabel.Size = UDim2.new(0, 250, 0, 30)
poweredByLabel.Position = UDim2.new(0.5, -125, 1, -35)
poweredByLabel.Text = "Powered by Erigcc2"
poweredByLabel.TextScaled = true
poweredByLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
poweredByLabel.BackgroundTransparency = 1
poweredByLabel.Parent = mainFrame

-- Função de minimizar
local minimized = false
minimizeButton.MouseButton1Click:Connect(function()
    if minimized then
        mainFrame.Size = UDim2.new(0, 300, 0, 200)
        minimized = false
    else
        mainFrame.Size = UDim2.new(0, 300, 0, 30)
        minimized = true
    end
end)

-- Funções para iniciar e parar recrutamento
startButton.MouseButton1Click:Connect(function()
    print("Recrutamento iniciado!")
    for i = 1, 3 do
        game.ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(
            "Alguém gostaria de se juntar a uma comunidade de entrenched? Temos treinos todos os dias e batalhas no final de semana, sem contar o eventos valendo robux. (fale: 'Eu quero')", "All")
        wait(60)  -- Espera de 1 minuto entre mensagens
    end
end)

stopButton.MouseButton1Click:Connect(function()
    print("Recrutamento parado!")
end)

-- Escutando respostas no chat
game.ReplicatedStorage.DefaultChatSystemChatEvents.OnMessageDoneFiltering.OnClientEvent:Connect(function(message, player)
    if string.lower(message.Message) == "eu quero" then
        game.ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(
            "@" .. player.Name .. ", adicione Zlx0 no Discord para ser recrutado!", "All")
    end
end)
