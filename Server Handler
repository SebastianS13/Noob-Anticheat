local EventsFolder = script.Parent.Parent.Events
local ScriptsFolder = script.Parent.Parent.Scripts

local DataStoreService = game:GetService("DataStoreService")
local DataStore = DataStoreService:GetDataStore("BannedPlayers")

game.Players.PlayerAdded:Connect(function(Player)
	local Banned = Instance.new("BoolValue")
	Banned.Name = "Banned"
	Banned.Value = false
	
	local BannedData
	
	local success, errormessage = pcall(function()
		BannedData = DataStore:GetAsync(Player.UserId.."-Banned")
	end)
	
	if success then
		Banned.Value = BannedData
	else
		Player:Kick("Falied to load banned data: "..errormessage)
	end
	
	if Banned.Value == true then
		Player:Kick("You have been banned for hacking.")
	end
end)

EventsFolder.SpeedHack.OnServerEvent:Connect(function(Player, Perm)
	print(Player.Name.." is hacking")
	
	if Perm == true then
		Player.Banned = true
	end
	
	Player:Kick("Anticheat has detected speed hacks.")
end)

EventsFolder.JumpHack.OnServerEvent:Connect(function(Player, Perm)
	print(Player.Name.." is hacking")

	if Perm == true then
		Player.Banned = true
	end

	Player:Kick("Anticheat has detected jump hacks.")
end)

EventsFolder.SpeedHack.OnServerEvent:Connect(function(Player, Perm)
	print(Player.Name.." is hacking")

	if Perm == true then
		Player.Banned = true
	end

	Player:Kick("Anticheat has detected teleport hacks.")
end)
