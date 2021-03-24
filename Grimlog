--// Made by Ch4mpus, Converted through Gui to Lua
--// Open source on github
--// :nodes to warn all passed instances, :refresh to refresh the list
--// It does take some time before it gets all remotes.

--// Instances

local Spactress = Instance.new("ScreenGui")
local FrameMain = Instance.new("Frame")
local UIGradient = Instance.new("UIGradient")
local UICorner = Instance.new("UICorner")
local TextLabel = Instance.new("TextLabel")
local UICorner_2 = Instance.new("UICorner")
local ScrollingFrame = Instance.new("ScrollingFrame")
local UIListLayout = Instance.new("UIListLayout")
local Frame = Instance.new("Frame")
local TextLabel_4 = Instance.new("TextLabel")

--// Properties

Spactress.Name = "Spactress"
Spactress.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
Spactress.Enabled = true
Spactress.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

FrameMain.Name = "FrameMain"
FrameMain.Parent = Spactress
FrameMain.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
FrameMain.BorderSizePixel = 0
FrameMain.Position = UDim2.new(0.307904422, 0, 0.364661664, 0)
FrameMain.Size = UDim2.new(0, 488, 0, 281)

UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(0, 0, 0)), ColorSequenceKeypoint.new(0.01, Color3.fromRGB(9, 9, 9)), ColorSequenceKeypoint.new(0.36, Color3.fromRGB(15, 15, 15)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(24, 24, 24))}
UIGradient.Parent = FrameMain

UICorner.Parent = FrameMain

TextLabel.Parent = FrameMain
TextLabel.BackgroundColor3 = Color3.fromRGB(33, 33, 33)
TextLabel.BackgroundTransparency = 0.500
TextLabel.Size = UDim2.new(0, 488, 0, 14)
TextLabel.Font = Enum.Font.Gotham
TextLabel.Text = "vGrimlog - by Ch4mpus"
TextLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel.TextSize = 14.000
TextLabel.TextStrokeTransparency = 0.000

UICorner_2.Parent = TextLabel

ScrollingFrame.Parent = FrameMain
ScrollingFrame.Active = true
ScrollingFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
ScrollingFrame.BackgroundTransparency = 0.500
ScrollingFrame.BorderSizePixel = 0
ScrollingFrame.Position = UDim2.new(0.489754111, 0, 0.0782918185, 0)
ScrollingFrame.Size = UDim2.new(0, 229, 0, 252)
ScrollingFrame.CanvasSize = UDim2.new(0, 0, 100, 0)
ScrollingFrame.ScrollBarThickness = 1

UIListLayout.Parent = ScrollingFrame
UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder
UIListLayout.Padding = UDim.new(0.00100000005, 0)


Frame.Parent = FrameMain
Frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
Frame.BackgroundTransparency = 0.500
Frame.BorderSizePixel = 0
Frame.Position = UDim2.new(0.0286885239, 0, 0.0782918185, 0)
Frame.Size = UDim2.new(0, 213, 0, 252)

TextLabel_4.Parent = Frame
TextLabel_4.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_4.BackgroundTransparency = 1.000
TextLabel_4.Position = UDim2.new(0.0281690136, 0, 0.0753968284, 0)
TextLabel_4.Size = UDim2.new(0, 200, 0, 50)
TextLabel_4.Font = Enum.Font.Gotham
TextLabel_4.Text = "Remote Events Found : "
TextLabel_4.TextColor3 = Color3.fromRGB(255, 255, 255)
TextLabel_4.TextSize = 15.000
TextLabel_4.TextStrokeTransparency = 0.000

--// Scripts

local function clientside()
	local script = Instance.new('LocalScript', Spactress)
	
	local function drag(obj)
		local UserInputService = game:GetService("UserInputService")
		
		local function updateDrag(ui, udim)
			ui:TweenPosition(udim, Enum.EasingDirection.Out, Enum.EasingStyle.Quad, .3, true)
		end

		obj.InputBegan:Connect(function(input)
			local ms = game.Players.LocalPlayer:GetMouse()
			if input.UserInputType == Enum.UserInputType.MouseButton1 then
				repeat
					wait(.01)
					local x = ms.X
					local y = ms.Y
					updateDrag(obj, UDim2.new(0,x, 0,y))
				until not UserInputService:IsMouseButtonPressed(Enum.UserInputType.MouseButton1)
			end
		end)

	end
	
	drag(script.Parent.FrameMain)

	--// Services
	local Workspace_UDM = game:GetService("Workspace")
	local ReplicatedStorage_UDM = game:GetService("ReplicatedStorage")
	local StarterGui_UDM = game:GetService("StarterGui")
	local Lighting_UDM = game:GetService("Lighting")
	local Players_UDM = game:GetService("Players")
	local RunService = game:GetService("RunService")
	
	--// Variables
	local player = Players_UDM.LocalPlayer
	--local drag = require(script.Parent.FrameMain.Drag)
	local amountFound = 0	
	--// Set
	local nodes = {}

	
	--// Functions
	local function getLog(service)
	
		local desc = service:GetDescendants()
		script.Parent.FrameMain.Frame.TextLabel.Text = "Started Up.."
		for x, value in pairs(desc) do
			RunService.Heartbeat:Wait()
			table.insert(nodes, #nodes + 1, value.ClassName)
			local strng = ""
			local spec = "/"
			local part = value
			if value:IsA("RemoteEvent") or value:IsA("RemoteFunction") then
				warn("Found one! Name is "..value.Name)
				RunService.Heartbeat:Wait()
				strng = value.Name..spec
				amountFound = amountFound + 1
				repeat
					script.Parent.FrameMain.Frame.TextLabel.Text = "Getting Remotes.."
					RunService.Heartbeat:Wait()
					local parent = part.Parent	
	
					if parent == game then
						break
					else
						strng = strng..parent.Name..spec
					end
	
					part = parent
	
				until (parent == game)
	
				local remoteTxt = Instance.new("TextLabel", script.Parent.FrameMain.ScrollingFrame)
				remoteTxt.Text = strng
				remoteTxt.Font = Enum.Font.Gotham
				remoteTxt.BackgroundTransparency = 1
				remoteTxt.TextStrokeTransparency = 0
	
				if string.len(strng) > 18 then
					remoteTxt.TextScaled = true
				else
					remoteTxt.TextScaled = false
					remoteTxt.TextSize = 18
				end
	
				remoteTxt.Size = UDim2.new(0, 200,0, 50)
				remoteTxt.TextColor3 = Color3.new(255,255,255)
	
				script.Parent.FrameMain.Frame.TextLabel.Text = "Remote Events Found : "..tostring(amountFound)
			end
		end
	end
	
	local function getNodes()
		for x, node in pairs(nodes) do
			RunService.Heartbeat:Wait()
			warn(node)
		end
	end
	
	local function refresh()
		for x, value in pairs(script.Parent.FrameMain.ScrollingFrame:GetChildren()) do
			RunService.Heartbeat:Wait()
			if value:IsA("TextLabel") then
				value:Remove()
			end
		end
		
		getLog(Workspace_UDM)
		getLog(Lighting_UDM)
		getLog(StarterGui_UDM)
		getLog(ReplicatedStorage_UDM)
	end
	
	local function chatted(c)
		if c == ":nodes" then
			getNodes()
		elseif c == ":refresh" then
			refresh()
		end
	end
	
	--// Events & Code
	wait(5)
	getLog(Workspace_UDM)
	getLog(Lighting_UDM)
	getLog(StarterGui_UDM)
	getLog(ReplicatedStorage_UDM)
	
	--// Commands
	
	Players_UDM.LocalPlayer.Chatted:Connect(chatted)
	
	
	--// End
	
end
coroutine.wrap(clientside)()
