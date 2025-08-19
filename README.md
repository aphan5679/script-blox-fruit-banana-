local player = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.Name = "BananaHubLite"

-- Tab Menu Frame
local main = Instance.new("Frame", gui)
main.Size = UDim2.new(0, 400, 0, 300)
main.Position = UDim2.new(0.05, 0, 0.2, 0)
main.BackgroundColor3 = Color3.fromRGB(20, 20, 20)

-- Tab Buttons
local tabs = {"Auto Farm", "Teleport"}
local pages = {}

for i, name in pairs(tabs) do
	local button = Instance.new("TextButton", main)
	button.Size = UDim2.new(0, 100, 0, 30)
	button.Position = UDim2.new(0, (i - 1) * 100, 0, 0)
	button.Text = name
	button.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
	button.TextColor3 = Color3.fromRGB(255, 255, 0)
	
	local page = Instance.new("Frame", main)
	page.Name = name.."Page"
	page.Size = UDim2.new(1, 0, 1, -30)
	page.Position = UDim2.new(0, 0, 0, 30)
	page.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
	page.Visible = (i == 1)
	pages[name] = page
	
	button.MouseButton1Click:Connect(function()
		for _, p in pairs(pages) do p.Visible = false end
		page.Visible = true
	end)
end

-- Auto Farm Page UI
local afBtn = Instance.new("TextButton", pages["Auto Farm"])
afBtn.Text = "Start Auto Farm"
afBtn.Size = UDim2.new(0, 200, 0, 40)
afBtn.Position = UDim2.new(0.5, -100, 0.3, 0)
afBtn.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
afBtn.TextColor3 = Color3.fromRGB(255, 255, 255)

afBtn.MouseButton1Click:Connect(function()
	print("Auto Farm (demo) started...")
	-- Viết auto farm thật phải có NPC + logic server
end)

-- Teleport Page UI
local dropdown = Instance.new("TextButton", pages["Teleport"])
dropdown.Text = "Choose Island"
dropdown.Size = UDim2.new(0, 200, 0, 40)
dropdown.Position = UDim2.new(0.5, -100, 0.2, 0)
dropdown.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
dropdown.TextColor3 = Color3.fromRGB(255, 255, 255)

local islandList = {"Starter Island", "Jungle", "Desert", "Sky Island"}

for i, island in pairs(islandList) do
	local option = Instance.new("TextButton", pages["Teleport"])
	option.Text = island
	option.Size = UDim2.new(0, 200, 0, 30)
	option.Position = UDim2.new(0.5, -100, 0.3 + (i * 0.07), 0)
	option.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
	option.TextColor3 = Color3.fromRGB(255, 255, 255)

	
