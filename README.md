local KeyGuardLibrary = loadstring(game:HttpGet("https://cdn.keyguardian.org/library/v1.0.0.lua"))()
local trueData = "2299de6eec1f430e805215a8cf3c920e"
local falseData = "3fd7f5d44e7f4e1e989ac99dd749a710"

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
		Title = "Enter Key Fremium/Premium",
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
		Title = "Check Key For Freemium",
		Description = "Enter Key before pressing this button",
		Callback = function()
				local response = KeyGuardLibrary.validateDefaultKey(key)
				if response == trueData then
						loadstring(game:HttpGet("https://raw.githubusercontent.com/alieegemn/statviewguyme/refs/heads/main/freemium"))()
						
				else
						print("Key is invalid try to use premium")
				end
		end
})

local Checkkey = Tabs.KeySys:AddButton({
		Title = "Check Key For Premium",
		Description = "Enter Key before pressing this button",
		Callback = function()
				local response = KeyGuardLibrary.validatePremiumKey(key)
				if response == trueData then
						loadstring(game:HttpGet("https://raw.githubusercontent.com/alieegemn/statviewguyme/refs/heads/main/premium"))()
						
				else
						print("Key is invalid try to use freemium or your key got broken or get expired")
				end
		end
})

local Getkey = Tabs.KeySys:AddButton({
		Title = "Get Key For Freemium",
		Description = "Get Key here paste in to your browser it tooks 3 steps its keysystem",
		Callback = function()
				setclipboard(KeyGuardLibrary.getLink())
   	Fluent:Notify({
    	Title = "HackManHub",
  	Content = "Coped On Clipboard",
   	Duration = 8
	})
		end
})

local Getkey = Tabs.KeySys:AddButton({
		Title = "Get Key For Premium",
		Description = "Get Key here paste in to your browser it worth bec it will be more paid scripts and it will took longer to do checkpoints in future",
		Callback = function()
				setclipboard("hackmanhub.pages.dev")
       	Fluent:Notify({
    	Title = "HackManHub",
  	Content = "Coped On Clipboard",
   	Duration = 8
	})
		end
})

Window:SelectTab(1)
