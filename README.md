local KeyGuardLibrary = loadstring(game:HttpGet("https://cdn.keyguardian.org/library/v1.0.0.lua"))()
local trueData = "c2b3f77225414994a10515d675be54c7"
local falseData = "ae0f8d6a808343c997e238178373c59d"

KeyGuardLibrary.Set({
	publicToken = "86b13899139841ce8ffca6b7aca4b739",
	privateToken = "733bc206af3844d18377d660ab57d24e",
	trueData = trueData,
	falseData = falseData,
})

local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local key = ""

local Window = Fluent:CreateWindow({
		Title = "Key System",
		SubTitle = "HackManHub",
		TabWidth = 160,
		Size = UDim2.fromOffset(580, 340),
		Acrylic = false,
		Theme = "Dark",
		MinimizeKey = Enum.KeyCode.LeftControl
})

local Tabs = {
		KeySys = Window:AddTab({ Title = "Key System", Icon = "key" }),
}

local Entkey = Tabs.KeySys:AddInput("Input", {
		Title = "Enter Key",
		Description = "Enter Key Here",
		Default = "",
		Placeholder = "Enter key…",
		Numeric = false,
		Finished = false,
		Callback = function(Value)
				key = Value
		end
})

local Checkkey = Tabs.KeySys:AddButton({
		Title = "Check Key",
		Description = "Enter Key before pressing this button",
		Callback = function()
				local response = KeyGuardLibrary.validatePremiumKey(key)
				if response == trueData then
				loadstring(game:HttpGet("https://raw.githubusercontent.com/alieegemn/statviewguyme/refs/heads/main/v2"))()
				else
						print("Key is invalid")
				end
		end
})

local Getkey = Tabs.KeySys:AddButton({
		Title = "Get Key Premium",
		Description = "Get Key here for premuim",
		Callback = function()
				setclipboard(discord.gg/JaPpBufYVW)
		end
})

Window:SelectTab(1)
