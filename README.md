-- xiteyy hub
local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Window = Rayfield:CreateWindow({
   Name = "xiteyy Hub | Roube um Ovo",
   LoadingTitle = "Carregando xiteyy...",
   LoadingSubtitle = "Tempo Real & Performance",
   ConfigurationSaving = { Enabled = false }
})

local MainTab = Window:CreateTab("Funções", 4483362458)

-- Velocidade de 10 Trilhões
MainTab:CreateButton({
   Name = "Ativar Velocidade Ultra (10 Trilhões)",
   Callback = function()
       local player = game.Players.LocalPlayer
       if player.Character and player.Character:FindFirstChild("Humanoid") then
           player.Character.Humanoid.WalkSpeed = 10000000000000
       end
   end,
})

-- Anti Lag (Otimização)
MainTab:CreateToggle({
   Name = "Anti Lag (Otimização)",
   CurrentValue = false,
   Flag = "AntiLagToggle",
   Callback = function(Value)
       if Value then
           game:GetService("Lighting").GlobalShadows = false
           for _, v in pairs(workspace:GetDescendants()) do
               if v:IsA("BasePart") then
                   v.Material = Enum.Material.SmoothPlastic
               elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                   v.Enabled = false
               end
           end
       end
   end,
})

-- Anti Hit (Proteção)
MainTab:CreateToggle({
   Name = "Anti Hit (Proteção)",
   CurrentValue = false,
   Flag = "AntiHitToggle",
   Callback = function(Value)
       local player = game.Players.LocalPlayer
       if player.Character and player.Character:FindFirstChild("Humanoid") then
           if Value then
               player.Character.Humanoid.MaxHealth = math.huge
               player.Character.Humanoid.Health = math.huge
           else
               player.Character.Humanoid.MaxHealth = 100
               player.Character.Humanoid.Health = 100
           end
       end
   end,
})

Rayfield:Notify({
   Title = "xiteyy Painel",
   Content = "Painel carregado com sucesso!",
   Duration = 5,
})
