-- NOOB ANTI-CHEAT
-- SCRIPTED BY IMANOOB

local Admins = {
	-- (You can add more than 10 admins)
	-- Change 00 to the user id of the admin (Can be found in the url of their profile)
	[1] = 00;
	[2] = 00;
	[3] = 00;
	[4] = 00;
	[5] = 00;
	[6] = 00;
	[7] = 00;
	[8] = 00;
	[9] = 00;
	[10] = 00;
}

local Settings = {
	["PermBanHackers"] = true;
	-- Setting to true means all hackers will be permanantly banned
	-- Setting to flase means all hackers will be only be kicked from the game
	
	-- Change these to your liking
	["SpeedHackCheck"] = true;
	["JumpHackCheck"] = true;
	["TeleportCheck"] = true;
}

-- Get the allowed speeds
local InitialSpeed = game.StarterPlayer.CharacterWalkSpeed
local InitialJump = game.StarterPlayer.CharacterJumpPower

-- Get ranges so that you can add Double Speed Gamepasses and Double Jump Height Gamepasses
local MinimumSpeedAllowed = InitialSpeed - 15
local MaximumSpeedAllowed = InitialSpeed * 2

local MinimumJumpAllowed = InitialSpeed - 3
local MaximumJumpAllowed = InitialSpeed * 2

-- Loop is always running
-- Loop checks player for any possible hacks

local Player = game.Players.LocalPlayer
local Character = Player.Character or Player.CharacterAdded:Wait()
local Humanoid = Character:WaitForChild("Humanoid")

local EventsFolder = script.Parent.Parent.Events
local ScriptsFolder = script.Parent.Parent.Scripts

local PreviousPosition

while wait(0.1) do
	
	-- Testing for jump and speed hacks
	
	if Humanoid.WalkSpeed ~= InitialSpeed and Settings.SpeedHackCheck == true and not Admins[Player.UserId] then
		-- Player possible has hacks
		if Humanoid.WalkSpeed > MaximumSpeedAllowed or Humanoid.WalkSpeed < MinimumSpeedAllowed then
			-- Player is definatly Hacking
			EventsFolder.SpeedHack:FireServer(false)
		end
	end
	
	if Humanoid.JumpHeight ~= InitialJump and Settings.JumpHackCheck == true and not Admins[Player.UserId] then
		-- Player possible has hacks
		if Humanoid.JumpHeight > MaximumJumpAllowed or Humanoid.JumpHeight < MinimumJumpAllowed then
			-- Player is definatly Hacking
			EventsFolder.JumpHack:FireServer(false)
		end
	end
	
	-- Testing for teleport hacks
	
	PreviousPosition = Character.PrimaryPart.Position
	
	local NewPos = PreviousPosition + Vector3.new(5,5,5)
	
	if Character.PrimaryPart.Position.Magnitude > NewPos.Magnitude and not Admins[Player.UserId] and Settings.TeleportCheck == true then
		-- Player has traveled over 5 studs in less than 0.1 seconds
		
		EventsFolder.TeleportHack:FireServer(false)
	end
end
