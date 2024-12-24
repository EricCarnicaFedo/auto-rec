local replicatedStorage = game:GetService("ReplicatedStorage")

-- RemoteEvent para receber a mensagem do cliente
local sendChatMessageEvent = Instance.new("RemoteEvent")
sendChatMessageEvent.Name = "SendChatMessage"
sendChatMessageEvent.Parent = replicatedStorage

-- Quando o RemoteEvent for disparado, envia a mensagem para o chat
sendChatMessageEvent.OnServerEvent:Connect(function(player, message)
    -- Envia a mensagem para o chat no servidor
    game:GetService("Chat"):Chat(player.Character, message, Enum.ChatColor.Blue)
end)
