local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local player = Players.LocalPlayer

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 300, 0, 200)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -100)
mainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

local startButton = Instance.new("TextButton")
startButton.Size = UDim2.new(0, 250, 0, 50)
startButton.Position = UDim2.new(0.5, -125, 0.3, 0)
startButton.Text = "Começar Recrutamento"
startButton.TextColor3 = Color3.fromRGB(255, 255, 255)
startButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
startButton.Parent = mainFrame

local poweredByLabel = Instance.new("TextLabel")
poweredByLabel.Size = UDim2.new(0, 250, 0, 30)
poweredByLabel.Position = UDim2.new(0.5, -125, 1, -35)
poweredByLabel.Text = "Powered by Erigcc2"
poweredByLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
poweredByLabel.BackgroundTransparency = 1
poweredByLabel.Parent = mainFrame

local function sendRecruitmentMessage()
    local message = "Alguém gostaria de se juntar a uma comunidade de entrenched? Temos treinos todos os dias e batalhas no final de semana, sem contar o eventos valendo robux. (fale: 'Eu quero')"
    for i = 1, 3 do
        ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(message, "All")
        wait(60) -- 1 minuto entre as mensagens
    end
end

local function onPlayerMessage(message, player)
    if string.lower(message) == "eu quero" then
        ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(
            "@" .. player.Name .. ", adicione Zlx0 no Discord para ser recrutado!", "All")
    end
end

startButton.MouseButton1Click:Connect(sendRecruitmentMessage)

ReplicatedStorage.DefaultChatSystemChatEvents.OnMessageDoneFiltering.OnClientEvent:Connect(function(msgData)
    onPlayerMessage(msgData.Message, msgData.FromSpeaker)
end)
