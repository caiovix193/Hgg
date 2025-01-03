-- Script de Otimização de Desempenho para Roblox

-- Função para desativar serviços desnecessários
local function disableUnnecessaryServices()
    local servicesToDisable = {
        "Chat",
        "Players",
        "Lighting",
        "ReplicatedFirst",
        "ReplicatedStorage",
        "StarterGui",
        "StarterPack",
        "StarterPlayer",
        "Teams",
        "SoundService"
    }
    
    for _, serviceName in ipairs(servicesToDisable) do
        local service = game:GetService(serviceName)
        if service then
            service:Destroy()
        end
    end
end

-- Função para ajustar configurações gráficas
local function optimizeGraphics()
    local settings = UserSettings():GetService("UserGameSettings")
    settings.SavedQualityLevel = Enum.SavedQualitySetting.QualityLevel1
    settings.MasterVolume = 0
end

-- Executar otimizações
disableUnnecessaryServices()
optimizeGraphics()

print("Otimização de desempenho aplicada com sucesso!")
