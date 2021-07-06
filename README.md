-- Made by Lynx._.x#3236 aka RedFireAPI Owner
local RedFire = Instance.new("ScreenGui")
local Main = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local Walkspeed = Instance.new("TextButton")
local JumpPower = Instance.new("TextButton")
local Respawn = Instance.new("TextButton")
local Rejoin = Instance.new("TextButton")
local Close = Instance.new("TextButton")
local Fly = Instance.new("TextButton")
local Reload = Instance.new("TextButton")

--Properties:

RedFire.Name = "RedFire"
RedFire.Parent = game.CoreGui
RedFire.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Main.Name = "Main"
Main.Parent = RedFire
Main.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Main.Position = UDim2.new(0.749075234, 0, 0.520245373, 0)
Main.Size = UDim2.new(0, 407, 0, 391)
Main.Active = true
Main.Draggable = true

Title.Name = "Title"
Title.Parent = Main
Title.BackgroundColor3 = Color3.fromRGB(217, 0, 0)
Title.BorderSizePixel = 0
Title.Size = UDim2.new(0, 407, 0, 30)
Title.Font = Enum.Font.SourceSans
Title.Text = "RedFire"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextScaled = true
Title.TextSize = 14.000
Title.TextWrapped = true

Walkspeed.Name = "Walkspeed"
Walkspeed.Parent = Main
Walkspeed.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Walkspeed.Position = UDim2.new(0.0319410302, 0, 0.10485933, 0)
Walkspeed.Size = UDim2.new(0, 167, 0, 52)
Walkspeed.Font = Enum.Font.SourceSansBold
Walkspeed.Text = "Walkspeed + 100"
Walkspeed.TextColor3 = Color3.fromRGB(255, 255, 255)
Walkspeed.TextScaled = true
Walkspeed.TextSize = 14.000
Walkspeed.TextWrapped = true
Walkspeed.MouseButton1Down:connect(function()
	local plr = game.Players.LocalPlayer
	
	plr.Character.Humanoid.WalkSpeed = 100
end)

JumpPower.Name = "JumpPower"
JumpPower.Parent = Main
JumpPower.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
JumpPower.Position = UDim2.new(0.525798559, 0, 0.10485933, 0)
JumpPower.Size = UDim2.new(0, 167, 0, 52)
JumpPower.Font = Enum.Font.SourceSansBold
JumpPower.Text = "Jumppower + 50"
JumpPower.TextColor3 = Color3.fromRGB(255, 255, 255)
JumpPower.TextScaled = true
JumpPower.TextSize = 14.000
JumpPower.TextWrapped = true
JumpPower.MouseButton1Down:connect(function()
	local plr = game.Players.LocalPlayer

	plr.Character.Humanoid.JumpPower = 50
end)

Respawn.Name = "Respawn"
Respawn.Parent = Main
Respawn.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Respawn.Position = UDim2.new(0.0319410563, 0, 0.278772384, 0)
Respawn.Size = UDim2.new(0, 167, 0, 52)
Respawn.Font = Enum.Font.SourceSansBold
Respawn.Text = "Respawn"
Respawn.TextColor3 = Color3.fromRGB(255, 255, 255)
Respawn.TextScaled = true
Respawn.TextSize = 14.000
Respawn.TextWrapped = true
Respawn.MouseButton1Down:connect(function()
	local plr = game.Players.LocalPlayer

	plr.Character.Humanoid.Health = 0
end)

Rejoin.Name = "Rejoin"
Rejoin.Parent = Main
Rejoin.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Rejoin.Position = UDim2.new(0.525798559, 0, 0.278772384, 0)
Rejoin.Size = UDim2.new(0, 167, 0, 52)
Rejoin.Font = Enum.Font.SourceSansBold
Rejoin.Text = "Rejoin"
Rejoin.TextColor3 = Color3.fromRGB(255, 255, 255)
Rejoin.TextScaled = true
Rejoin.TextSize = 14.000
Rejoin.TextWrapped = true
Rejoin.MouseButton1Down:connect(function()
	local plr = game.Players.LocalPlayer

	plr:Kick("You Wanted To Rejoin!")
end)

Close.Name = "Close"
Close.Parent = Main
Close.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Close.Position = UDim2.new(0.525798559, 0, 0.4501279, 0)
Close.Size = UDim2.new(0, 167, 0, 52)
Close.Font = Enum.Font.SourceSansBold
Close.Text = "Close RedFire"
Close.TextColor3 = Color3.fromRGB(255, 255, 255)
Close.TextScaled = true
Close.TextSize = 14.000
Close.TextWrapped = true
Close.MouseButton1Down:connect(function()
	game.Workspace.RedFire:Destroy()
end)

Fly.Name = "Fly"
Fly.Parent = Main
Fly.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Fly.Position = UDim2.new(0.0319410563, 0, 0.4501279, 0)
Fly.Size = UDim2.new(0, 167, 0, 52)
Fly.Font = Enum.Font.SourceSansBold
Fly.Text = "Fly"
Fly.TextColor3 = Color3.fromRGB(255, 255, 255)
Fly.TextScaled = true
Fly.TextSize = 14.000
Fly.TextWrapped = true
Fly.MouseButton1Down:connect(function()
	repeat wait()
	until game.Players.LocalPlayer and game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:findFirstChild("Torso") and game.Players.LocalPlayer.Character:findFirstChild("Humanoid")
	local mouse = game.Players.LocalPlayer:GetMouse()
	repeat wait() until mouse
	local plr = game.Players.LocalPlayer
	local torso = plr.Character.Torso
	local flying = true
	local deb = true
	local ctrl = {f = 0, b = 0, l = 0, r = 0}
	local lastctrl = {f = 0, b = 0, l = 0, r = 0}
	local maxspeed = 50
	local speed = 0

	function Fly()
		local bg = Instance.new("BodyGyro", torso)
		bg.P = 9e4
		bg.maxTorque = Vector3.new(9e9, 9e9, 9e9)
		bg.cframe = torso.CFrame
		local bv = Instance.new("BodyVelocity", torso)
		bv.velocity = Vector3.new(0,0.1,0)
		bv.maxForce = Vector3.new(9e9, 9e9, 9e9)
		repeat wait()
			plr.Character.Humanoid.PlatformStand = true
			if ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0 then
				speed = speed+.5+(speed/maxspeed)
				if speed > maxspeed then
					speed = maxspeed
				end
			elseif not (ctrl.l + ctrl.r ~= 0 or ctrl.f + ctrl.b ~= 0) and speed ~= 0 then
				speed = speed-1
				if speed < 0 then
					speed = 0
				end
			end
			if (ctrl.l + ctrl.r) ~= 0 or (ctrl.f + ctrl.b) ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (ctrl.f+ctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(ctrl.l+ctrl.r,(ctrl.f+ctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
				lastctrl = {f = ctrl.f, b = ctrl.b, l = ctrl.l, r = ctrl.r}
			elseif (ctrl.l + ctrl.r) == 0 and (ctrl.f + ctrl.b) == 0 and speed ~= 0 then
				bv.velocity = ((game.Workspace.CurrentCamera.CoordinateFrame.lookVector * (lastctrl.f+lastctrl.b)) + ((game.Workspace.CurrentCamera.CoordinateFrame * CFrame.new(lastctrl.l+lastctrl.r,(lastctrl.f+lastctrl.b)*.2,0).p) - game.Workspace.CurrentCamera.CoordinateFrame.p))*speed
			else
				bv.velocity = Vector3.new(0,0.1,0)
			end
			bg.cframe = game.Workspace.CurrentCamera.CoordinateFrame * CFrame.Angles(-math.rad((ctrl.f+ctrl.b)*50*speed/maxspeed),0,0)
		until not flying
		ctrl = {f = 0, b = 0, l = 0, r = 0}
		lastctrl = {f = 0, b = 0, l = 0, r = 0}
		speed = 0
		bg:Destroy()
		bv:Destroy()
		plr.Character.Humanoid.PlatformStand = false
	end
	mouse.KeyDown:connect(function(key)
		if key:lower() == "e" then
			if flying then flying = false
			else
				flying = true
				Fly()
			end
		elseif key:lower() == "w" then
			ctrl.f = 1
		elseif key:lower() == "s" then
			ctrl.b = -1
		elseif key:lower() == "a" then
			ctrl.l = -1
		elseif key:lower() == "d" then
			ctrl.r = 1
		end
	end)
	mouse.KeyUp:connect(function(key)
		if key:lower() == "w" then
			ctrl.f = 0
		elseif key:lower() == "s" then
			ctrl.b = 0
		elseif key:lower() == "a" then
			ctrl.l = 0
		elseif key:lower() == "d" then
			ctrl.r = 0
		end
	end)
	Fly()
end)

Reload.Name = "Reload"
Reload.Parent = Main
Reload.BackgroundColor3 = Color3.fromRGB(35, 35, 35)
Reload.Position = UDim2.new(0.0319410563, 0, 0.636828661, 0)
Reload.Size = UDim2.new(0, 167, 0, 52)
Reload.Font = Enum.Font.SourceSansBold
Reload.Text = "ReLoad RedFire"
Reload.TextColor3 = Color3.fromRGB(255, 255, 255)
Reload.TextScaled = true
Reload.TextSize = 14.000
Reload.TextWrapped = true
Close.MouseButton1Down:connect(function()
	game.Workspace.RedFire:Clone()
end)
