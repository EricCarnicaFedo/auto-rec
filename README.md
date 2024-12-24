local replicatedStorage = game:GetService("ReplicatedStorage")

-- Cria o RemoteEvent para receber a mensagem do cliente
local sendChatMessageEvent = Instance.new("RemoteEvent")
sendChatMessageEvent.Name = "SendChatMessage"
sendChatMessageEvent.Parent = replicatedStorage

-- Quando o RemoteEvent for disparado, envia a mensagem para o chat
sendChatMessageEvent.OnServerEvent:Connect(function(player, message)
    -- Envia a mensagem para todos os jogadores no chat
    game:GetService("Chat"):Chat(game.Workspace, message, Enum.ChatColor.Blue)
end)
