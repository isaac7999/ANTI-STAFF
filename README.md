-- ✅ Anti Staff Roblox - Por Nick e Team
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- Lista de nomes de Staff conhecidos
local StaffNicks = {
    "xxxjoaoxxxg", "CleitinDoGrau_Eb", "Jonas_411", "Lucalarte", "SPTmatheus123",
    "GuilhermeDRTgg", "Briessxz", "hardstyless", "Mundaka", "Isabelaaaaafofs",
    "HANRLLEY25", "kaleb_iaee", "brunizoraa", "rip_propleyfran", "pepezicador",
    "Jjhgul", "Dariosantos21048", "JEKER_2009", "Qqueqaco", "MZPlug14k",
    "GregoriusKhronos", "Sargento_admOficial", "Cassiopia84un", "Hakplays", "Cleo_ptr"
}

-- Função que verifica se o jogador é Staff
local function isStaff(player)
    -- Checa se o nick está na lista
    for _, name in ipairs(StaffNicks) do
        if string.lower(player.Name) == string.lower(name) then
            return true
        end
    end

    -- Checa se o Team tem "staff" no nome
    if player.Team and string.find(string.lower(player.Team.Name), "staff") then
        return true
    end

    return false
end

-- Função para verificar todos os players no servidor
local function checkAllPlayers()
    for _, player in ipairs(Players:GetPlayers()) do
        if player ~= LocalPlayer and isStaff(player) then
            LocalPlayer:Kick("🚨 Anti Staff: Detecção de Staff no servidor!")
        end
    end
end

-- Checa imediatamente ao executar
checkAllPlayers()

-- Monitora entrada de novos jogadores
Players.PlayerAdded:Connect(function(player)
    if isStaff(player) then
        LocalPlayer:Kick("🚨 Anti Staff: Um Staff acabou de entrar no servidor!")
    end
end)
