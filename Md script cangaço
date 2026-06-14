local Players = game:GetService("Players")
local UserInputService = game:GetService("UserInputService")
local RunService = game:GetService("RunService")
local player = Players.LocalPlayer

-- [CONFIGURAÇÃO DA TELA]
local screen = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
screen.Name = "MD_HUB_OFICIAL"
screen.IgnoreGuiInset = true

-- [BOLINHA DE TOGGLE]
local toggleBtn = Instance.new("TextButton", screen)
toggleBtn.Size = UDim2.new(0, 50, 0, 50); toggleBtn.Position = UDim2.new(0.05, 0, 0.5, 0)
toggleBtn.Text = "🩸"; toggleBtn.BackgroundColor3 = Color3.fromRGB(0,0,0)
Instance.new("UICorner", toggleBtn).CornerRadius = UDim.new(1,0)

-- [PAINEL PRINCIPAL]
local main = Instance.new("Frame", screen)
main.Size = UDim2.new(0, 240, 0, 440); main.Position = UDim2.new(0.5, -120, 0.5, -220)
main.BackgroundColor3 = Color3.fromRGB(15, 15, 15); main.Visible = true
Instance.new("UICorner", main).CornerRadius = UDim.new(0, 10)
Instance.new("UIStroke", main).Color = Color3.fromRGB(255, 0, 0)

toggleBtn.MouseButton1Click:Connect(function() main.Visible = not main.Visible end)

-- [ASSINATURA DO TOPO]
local topTitle = Instance.new("TextLabel", main)
topTitle.Size = UDim2.new(1, 0, 0, 35); topTitle.Position = UDim2.new(0, 0, 0, 5)
topTitle.Text = "Cangaço até o fim! 🤝"; topTitle.TextColor3 = Color3.new(1, 1, 1)
topTitle.BackgroundTransparency = 1; topTitle.Font = Enum.Font.GothamBold; topTitle.TextScaled = true

-- [SCROLL E LAYOUT]
local scroll = Instance.new("ScrollingFrame", main)
scroll.Size = UDim2.new(1, 0, 1, -110); scroll.Position = UDim2.new(0, 0, 0, 40)
scroll.BackgroundTransparency = 1; scroll.ScrollBarThickness = 4
scroll.CanvasSize = UDim2.new(0, 0, 0, 1000)

local layout = Instance.new("UIListLayout", scroll)
layout.Padding = UDim.new(0, 6); layout.HorizontalAlignment = Enum.HorizontalAlignment.Center

-- [CONTROLE DE TAMANHO]
local escala = 1
local function mudarTamanho(soma)
    escala = math.clamp(escala + soma, 0.4, 2.5)
    main.Size = UDim2.new(0, 240 * escala, 0, 440 * escala)
end

-- [BOTÕES DE RODAPÉ (AJUSTES DE TAMANHO)]
local frameControle = Instance.new("Frame", main)
frameControle.Size = UDim2.new(1, 0, 0, 30); frameControle.Position = UDim2.new(0, 0, 1, -65); frameControle.BackgroundTransparency = 1
local btnMais = Instance.new("TextButton", frameControle); btnMais.Text = "Aumentar (+)"; btnMais.Size = UDim2.new(0.5, 0, 1, 0); btnMais.MouseButton1Click:Connect(function() mudarTamanho(0.1) end)
local btnMenos = Instance.new("TextButton", frameControle); btnMenos.Text = "Diminuir (-)"; btnMenos.Position = UDim2.new(0.5, 0, 0, 0); btnMenos.Size = UDim2.new(0.5, 0, 1, 0); btnMenos.MouseButton1Click:Connect(function() mudarTamanho(-0.1) end)

-- [ASSINATURA DE BAIXO]
local bottomTitle = Instance.new("TextLabel", main)
bottomTitle.Size = UDim2.new(1, 0, 0, 30); bottomTitle.Position = UDim2.new(0, 0, 1, -35)
bottomTitle.Text = "By: md"; bottomTitle.TextColor3 = Color3.fromRGB(200, 200, 200)
bottomTitle.BackgroundTransparency = 1; bottomTitle.Font = Enum.Font.GothamMedium; bottomTitle.TextSize = 14

-- [FUNÇÕES BÁSICAS]
local function criarBotao(txt, cor, acao)
    local b = Instance.new("TextButton", scroll)
    b.Size = UDim2.new(0.9, 0, 0, 38); b.Text = txt; b.BackgroundColor3 = cor; b.TextColor3 = Color3.new(1,1,1); b.TextScaled = true
    Instance.new("UICorner", b); b.MouseButton1Click:Connect(acao)
end

local function enviar(txt) 
    local chat = game:GetService("TextChatService")
    if chat:FindFirstChild("TextChannels") then chat.TextChannels.RBXGeneral:SendAsync(txt) 
    else game.ReplicatedStorage.DefaultChatSystemChatEvents.SayMessageRequest:FireServer(txt, "All") end
end

-- [BOTÕES]
criarBotao("❌ FECHAR PAINEL", Color3.fromRGB(150,0,0), function() main.Visible = false end)
criarBotao("// 🎉 Mat", Color3.fromRGB(35,35,35), function() enviar("// 🎉 Mat") end)
criarBotao("// 🥳 Render", Color3.fromRGB(35,35,35), function() enviar("// 🥳 Render") end)
criarBotao("// ⛓️ Amarrar", Color3.fromRGB(35,35,35), function() enviar("// ⛓️ Amarrar") end)
criarBotao("// 🔇 Cortar comunicação", Color3.fromRGB(35,35,35), function() enviar("// 🔇 Cortar comunicação") end)
criarBotao("// 🫴 Pegar", Color3.fromRGB(35,35,35), function() enviar("// 🫴 Pegar") end)
criarBotao("// 🛞 Furar pneus (x1)", Color3.fromRGB(35,35,35), function() enviar("// 🛞 Furar pneus (x1)") end)
criarBotao("// 🚁 Rajar helicóptero", Color3.fromRGB(35,35,35), function() enviar("// 🚁 Rajar helicóptero") end)
criarBotao("// 💣 Implantar C4 (x1)", Color3.fromRGB(35,35,35), function() enviar("// 💣 Implantar C4 (x1)") end)
criarBotao("🚀 Anti Lag", Color3.fromRGB(0,80,0), function() for _,o in pairs(workspace:GetDescendants()) do if o:IsA("BasePart") then o.Material = Enum.Material.Plastic; o.Reflectance = 0 end end end)

-- [ESP ROBUSTO]
local espAtivo = false
local btnEsp = Instance.new("TextButton", scroll); btnEsp.Size = UDim2.new(0.9, 0, 0, 38); btnEsp.Text = "🎾 Ativar ESP"; btnEsp.BackgroundColor3 = Color3.fromRGB(0,0,100); btnEsp.TextScaled = true
Instance.new("UICorner", btnEsp); btnEsp.MouseButton1Click:Connect(function() espAtivo = not espAtivo; btnEsp.Text = espAtivo and "🎾 Desativar ESP" or "🎾 Ativar ESP" end)

RunService.RenderStepped:Connect(function()
    if espAtivo then
        for _, p in pairs(Players:GetPlayers()) do
            if p ~= player and p.Character and not p.Character:FindFirstChild("MD_ESP") then
                local h = Instance.new("Highlight", p.Character); h.Name = "MD_ESP"; h.FillColor = Color3.new(1,0,0); h.FillTransparency = 0.5
            end
        end
    else
        for _, p in pairs(Players:GetPlayers()) do if p.Character and p.Character:FindFirstChild("MD_ESP") then p.Character.MD_ESP:Destroy() end end
    end
end)

-- [DRAGIFY]
local function dragify(obj)
    local dragStart, startPos, dragging
    obj.InputBegan:Connect(function(i) if i.UserInputType == Enum.UserInputType.MouseButton1 or i.UserInputType == Enum.UserInputType.Touch then dragging = true; dragStart = i.Position; startPos = obj.Position end end)
    UserInputService.InputChanged:Connect(function(i) if dragging then obj.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + (i.Position.X - dragStart.X), startPos.Y.Scale, startPos.Y.Offset + (i.Position.Y - dragStart.Y)) end end)
    UserInputService.InputEnded:Connect(function() dragging = false end)
end
dragify(main); dragify(toggleBtn)
