local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local player = Players.LocalPlayer

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 300, 0, 150)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -75)
mainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

local toggleButton = Instance.new("TextButton")
toggleButton.Size = UDim2.new(0, 250, 0, 60)
toggleButton.Position = UDim2.new(0.5, -125, 0.3, 0)
toggleButton.Text = "🔴 Recrutamento Desativado"
toggleButton.TextColor3 = Color3.fromRGB(255, 255, 255)
toggleButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
toggleButton.Parent = mainFrame

local poweredByLabel = Instance.new("TextLabel")
poweredByLabel.Size = UDim2.new(0, 250, 0, 30)
poweredByLabel.Position = UDim2.new(0.5, -125, 1, -35)
poweredByLabel.Text = "Powered by Erigcc2"
poweredByLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
poweredByLabel.BackgroundTransparency = 1
poweredByLabel.Parent = mainFrame

local recruiting = false

local function sendRecruitmentMessage()
    while recruiting do
        local A_1 = "Alguém gostaria de se juntar a uma comunidade de entrenched? Temos treinos todos os dias e batalhas no final de semana, sem contar os eventos valendo robux. (fale: 'Eu quero')"
        local A_2 = "All"
        ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(A_1, A_2)
        wait(60)  -- espera 1 minuto entre as mensagens
    end
end

local function onPlayerMessage(message, speaker)
    if string.lower(message) == "eu quero" then
        ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(
            "@" .. speaker .. ", adicione Zlx0 no Discord para ser recrutado!", "All")
    end
end

toggleButton.MouseButton1Click:Connect(function()
    recruiting = not recruiting
    
    if recruiting then
        toggleButton.Text = "🟢 Recrutamento Ativado"
        toggleButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
        sendRecruitmentMessage()
    else
        toggleButton.Text = "🔴 Recrutamento Desativado"
        toggleButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
    end
end)

ReplicatedStorage.DefaultChatSystemChatEvents.OnMessageDoneFiltering.OnClientEvent:Connect(function(msgData)
    onPlayerMessage(msgData.Message, msgData.FromSpeaker)
end)
