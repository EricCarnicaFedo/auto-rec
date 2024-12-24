-- Criando ScreenGui para interface
local screenGui = Instance.new("ScreenGui")
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")

-- Criando o quadro principal
local mainFrame = Instance.new("Frame")
mainFrame.Size = UDim2.new(0, 250, 0, 150)
mainFrame.Position = UDim2.new(0.5, -125, 0.5, -75)
mainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
mainFrame.Active = true
mainFrame.Draggable = true
mainFrame.Parent = screenGui

-- Criando botão de minimizar
local minimizeButton = Instance.new("TextButton")
minimizeButton.Size = UDim2.new(0, 25, 0, 25)
minimizeButton.Position = UDim2.new(1, -30, 0, 5)
minimizeButton.Text = "_"
minimizeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
minimizeButton.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
minimizeButton.Parent = mainFrame

-- Criando botão para começar recrutamento
local startButton = Instance.new("TextButton")
startButton.Size = UDim2.new(0, 200, 0, 50)
startButton.Position = UDim2.new(0.5, -100, 0.3, 0)
startButton.Text = "Começar Recrutamento"
startButton.TextColor3 = Color3.fromRGB(255, 255, 255)
startButton.BackgroundColor3 = Color3.fromRGB(0, 170, 0)
startButton.Parent = mainFrame

-- Criando botão para parar recrutamento
local stopButton = Instance.new("TextButton")
stopButton.Size = UDim2.new(0, 200, 0, 50)
stopButton.Position = UDim2.new(0.5, -100, 0.6, 0)
stopButton.Text = "Parar Recrutamento"
stopButton.TextColor3 = Color3.fromRGB(255, 255, 255)
stopButton.BackgroundColor3 = Color3.fromRGB(170, 0, 0)
stopButton.Parent = mainFrame

-- Texto de Powered by
local poweredByLabel = Instance.new("TextLabel")
poweredByLabel.Size = UDim2.new(0, 200, 0, 30)
poweredByLabel.Position = UDim2.new(0.5, -100, 1, -40)
poweredByLabel.Text = "Powered by Erigcc2"
poweredByLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
poweredByLabel.BackgroundTransparency = 1
poweredByLabel.Parent = mainFrame

-- Função de minimizar
local minimized = false
minimizeButton.MouseButton1Click:Connect(function()
    if minimized then
        mainFrame.Size = UDim2.new(0, 250, 0, 150)
        minimized = false
    else
        mainFrame.Size = UDim2.new(0, 250, 0, 30)
        minimized = true
    end
end)

-- Funções para iniciar e parar recrutamento
startButton.MouseButton1Click:Connect(function()
    print("Recrutamento iniciado!")
    -- Adicione a lógica para começar o recrutamento aqui
end)

stopButton.MouseButton1Click:Connect(function()
    print("Recrutamento parado!")
    -- Adicione a lógica para parar o recrutamento aqui
end)
