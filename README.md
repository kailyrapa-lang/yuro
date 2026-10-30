# yuro
shiny shader
--// ALL PARTS GLASS + BALANCED GLOSSY
--// No Lighting Changes

local Workspace = game:GetService("Workspace")
local Players = game:GetService("Players")

-- SETTINGS
local GLASS_REFLECTANCE = 0.40
local GLOSSY_REFLECTANCE = 0.15

-- Save original materials for balanced glossy
local function ApplyGlass(part)
    if not part:IsA("BasePart") then
        return
    end

    -- Keep glass-like appearance on all parts
    part.Material = Enum.Material.Glass
    part.Reflectance = GLASS_REFLECTANCE
end

-- APPLY TO ALL MAP PARTS
for _, obj in ipairs(Workspace:GetDescendants()) do
    if obj:IsA("BasePart") then
        ApplyGlass(obj)
    end
end

-- APPLY TO NEW PARTS
Workspace.DescendantAdded:Connect(function(obj)
    if obj:IsA("BasePart") then
        ApplyGlass(obj)
    end
end)

print("ALL PARTS GLASS + SMOOTH REFLECTION ENABLED")
