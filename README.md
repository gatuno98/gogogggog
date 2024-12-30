-- Script para mostrar os nomes dos jogadores em vermelho sobre as cabeças

-- Função para criar uma label acima da cabeça do jogador
local function criarNomeAcimaDaCabeça(player)
    -- Verifica se o jogador tem uma "Head" (cabeça)
    local personagem = player.Character
    if personagem and personagem:FindFirstChild("Head") then
        -- Cria a parte do texto acima da cabeça
        local head = personagem.Head
        local nomeTag = Instance.new("BillboardGui")
        nomeTag.Parent = head
        nomeTag.Adornee = head
        nomeTag.Size = UDim2.new(0, 200, 0, 50)
        nomeTag.StudsOffset = Vector3.new(0, 2, 0) -- Ajuste de altura
        nomeTag.AlwaysOnTop = true

        -- Cria o texto
        local texto = Instance.new("TextLabel")
        texto.Parent = nomeTag
        texto.Text = player.Name
        texto.TextColor3 = Color3.fromRGB(255, 0, 0) -- Cor vermelha
        texto.TextSize = 20
        texto.BackgroundTransparency = 1 -- Sem fundo
    end
end

-- Conectar a função para todos os jogadores
game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        criarNomeAcimaDaCabeça(player)
    end)
end)
