local UIS = game:GetService("UserInputService")
local plr = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", plr:WaitForChild("PlayerGui"))
gui.Name = "BladeBallAutoParry"

local toggle = false
local main = Instance.new("ImageButton")
main.Parent = gui
main.Position = UDim2.new(0, 20, 0.5, -25)
main.Size = UDim2.new(0, 50, 0, 50)
main.Image = "rbxassetid://14497723819" -- شكل الزر
main.BackgroundTransparency = 1

local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 200, 0, 100)
frame.Position = UDim2.new(0, 80, 0.5, -50)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0
frame.Visible = false
frame.Parent = gui

local uicorner = Instance.new("UICorner", frame)
uicorner.CornerRadius = UDim.new(0, 8)

local title = Instance.new("TextLabel", frame)
title.Text = "Auto Parry"
title.Size = UDim2.new(1, 0, 0, 30)
title.BackgroundTransparency = 1
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.GothamSemibold
title.TextSize = 20

local autoParry = false

local button = Instance.new("TextButton", frame)
button.Text = "Auto Parry: OFF"
button.Size = UDim2.new(1, -20, 0, 40)
button.Position = UDim2.new(0, 10, 0, 40)
button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
button.TextColor3 = Color3.fromRGB(255, 255, 255)
button.Font = Enum.Font.GothamBold
button.TextSize = 16

local corner = Instance.new("UICorner", button)
corner.CornerRadius = UDim.new(0, 6)

button.MouseButton1Click:Connect(function()
	autoParry = not autoParry
	button.Text = "Auto Parry: " .. (autoParry and "ON" or "OFF")
end)

main.MouseButton1Click:Connect(function()
	toggle = not toggle
	frame.Visible = toggle
end)

-- Auto Parry Logic
game:GetService("RunService").RenderStepped:Connect(function()
	if not autoParry then return end
	local char = plr.Character
	if not char or not char:FindFirstChild("Highlight") then return end

	for _, v in pairs(workspace.Balls:GetChildren()) do
		if v:IsA("BasePart") and (v.Position - char.Position).Magnitude < 15 then
			game:GetService("ReplicatedStorage").Remotes.ParryButtonPress:Fire()
		end
	end
end)
