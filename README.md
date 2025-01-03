-- Aumenta a hitbox do jogador e pega a bola quando ela toca na hitbox
local player = game.Players.LocalPlayer
local character = player.Character or player.CharacterAdded:Wait()
local hitbox = Instance.new("Part")

hitbox.Size = Vector3.new(100, 100, 100) -- Tamanho da hitbox
hitbox.Transparency = 0.5
hitbox.Anchored = true
hitbox.CanCollide = false
hitbox.Parent = character

-- Atualiza a posição da hitbox para seguir o jogador
game:GetService("RunService").RenderStepped:Connect(function()
    hitbox.Position = character.HumanoidRootPart.Position
end)

-- Detecta quando a bola toca na hitbox
hitbox.Touched:Connect(function(hit)
    if hit.Name == "Bola" then
        -- Código para pegar a bola
        hit.CFrame = character.HumanoidRootPart.CFrame
    end
end)
