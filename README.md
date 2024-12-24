local player = game.Players.LocalPlayer
local chatService = game:GetService("Chat")
local virtualUser = game:GetService("VirtualInputManager")

local screenGui = Instance.new("ScreenGui")
screenGui.Parent = player:WaitForChild("PlayerGui")

local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 300, 0, 100)
mainFrame.Position = UDim2.new(0.5, -150, 0.5, -50)
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
poweredByLabel.Size = UDim2.new(0, 250, 0, 20)
poweredByLabel.Position = UDim2.new(0.5, -125, 1, -25)
poweredByLabel.Text = "Powered by Erigcc2"
poweredByLabel.TextColor3 = Color3.fromRGB(200, 200, 200)
poweredByLabel.BackgroundTransparency = 1
poweredByLabel.Parent = mainFrame

local recruiting = false

local function sendChatMessage(message)
    -- Ação para abrir o chat
    virtualUser:SendKeyEvent(true, Enum.KeyCode.Slash, false, nil)  -- Abre o chat
    wait(0.2)
    
    -- Digitar a mensagem
    virtualUser:SendTextInput(message)
    wait(0.1)
    
    -- Enviar a mensagem
    virtualUser:SendKeyEvent(true, Enum.KeyCode.Return, false, nil)
end

local function startRecruitment()
    while recruiting do
        sendChatMessage("Alguém gostaria de se juntar a uma comunidade de entrenched? Temos treinos todos os dias e batalhas no final de semana, sem contar eventos valendo robux. (fale: 'Eu quero')")
        wait(60)  -- Espera 1 minuto para enviar novamente
    end
end

toggleButton.MouseButton1Click:Connect(function()
    recruiting = not recruiting
    
    if recruiting then
        toggleButton.Text = "🟢 Recrutamento Ativado"
        toggleButton.BackgroundColor3 = Color3.fromRGB(0, 200, 0)
        startRecruitment()
    else
        toggleButton.Text = "🔴 Recrutamento Desativado"
        toggleButton.BackgroundColor3 = Color3.fromRGB(200, 0, 0)
    end
end)
