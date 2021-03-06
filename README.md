# RStore
A quick, simple caching DataStore wrapper for Roblox!

# Quick Start

First, you need to create a new RDataStore to save data.
```lua
local RStore = require("path.to.RStore")
local RDataStore = RStore.new("datakey")
```

Next, you probably have a variable or something you want to save, or you wouldn't be here.

```lua
local RStore = require("path.to.RStore")
local CashStore = RStore.new("datakey")

game.Players.PlayerAdded:Connect(function(plr)
	local cash = CashStore:Get(plr, 0) -- **plr** is who you're saving it for, **0** is the default value
end)
```

Obviously, something makes the player earn some cash. In this case, let's make it add 10 cash every time they say "I want cash!"

```lua
local RStore = require("path.to.RStore")
local CashStore = RStore.new("datakey")

game.Players.PlayerAdded:Connect(function(plr)
	local cash = CashStore:Get(plr, 0) -- **plr** is who you're saving it for, **0** is the default value
	
	plr.Chatted:Connect(function(msg)
		if msg == "I want cash!" then
			CashStore:Increment(plr, 10) -- here, you **increment** since you want to *add* to the current value. otherwise, if you wanted to directly overwrite, you'd use :Set()
		end
	end)
end)
```

`TIP: You can print the value of CashStore:Get(plr) to see it increase.`

Great! Now you have a basic understanding of how to use RStore in your Roblox game!

# Documentation

## RStore [CLASS]
### RStore.new(...)
#### Description:
* Creates a new RDataStore for you to use
#### Parameters:
* Datakey - A unique key for storing data in that specific RDataStore
#### Returns:
* RDataStore [CLASS]
## RDataStore [CLASS]
### RDataStore:Get(...)
#### Description:
* Gets the specified obj's value from the cache
#### Parameters:
* Obj - A unique key (can be an Instance, string, integer, etc.)
* DefaultValue - Default value to be cached if there is no saved value in the cache or DataStore API
#### Returns:
* Cached result
### RDataStore:Set(...)
#### Description:
* Sets the specified obj's value to the specified data in the cache
#### Parameters:
* Obj - A unique key (can be an Instance, string, integer, etc.)
* Data - Data to cache in RDataStore
#### Returns:
* Cached result
### RDataStore:Increment(...)
#### Description:
* Increments the specified obj's value by the specified amount in the cache
#### Parameters:
* Obj - A unique key (can be an Instance, string, integer, etc.)
* Amount - Amount to increase the current value by
#### Returns:
* Cached result
### RDataStore:OnUpdate(...)
#### Description:
* Executes callback when the RDataStore is updated
#### Parameters:
* Callback - A function to execute every time the RDataStore is updated; callback includes `newValue` as a function parameter
#### Returns:
* nil
### RDataStore:Save(...)
#### Description:
* Saves the specified obj's value to the Roblox Datastore API
#### Parameters:
* Obj - A unique key (can be an Instance, string, integer, etc.)
#### Returns:
* Cached result
### RDataStore:SaveAll()
#### Description:
* Calls :Save() on all objs in each RDataStore

# Credit
* Creator & Maintainer - @R0bl0x10501050 ([DevForum](https://devforum.roblox.com/u/r0bl0x10501050/summary))
* Class.lua - Antonio6643 ([DevForum](https://devforum.roblox.com/u/antonio6643/summary))
