-- Variáveis
local player = game.Players.LocalPlayer
local character = player.Character
local nevoa = Instance.new("ParticleEmitter")
nevoa.Color = Color3.new(0.5, 0.5, 0.5) -- Cor cinza
nevoa.Transparency = NumberSequence.new(0, 1)
nevoa.Size = NumberSequence.new(0, 10)
nevoa.Velocity = NumberSequence.new(0, 10)
nevoa.Lifetime = NumberRange.new(1, 5)
nevoa.Rate = 10

-- Função que atualiza a posição da névoa
local function updateNevoa()
nevoa.Position = character.HumanoidRootPart.Position
end

-- Conecta a função ao evento de atualização do jogador
player.CharacterAdded:Connect(function()
character = player.Character
updateNevoa()
end)

-- Atualiza a posição da névoa a cada frame
game:GetService("RunService").RenderStepped:Connect(updateNevoa)

-- Adiciona a névoa ao jogo
character.HumanoidRootPart:Emit(nevoa)
