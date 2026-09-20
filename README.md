# Roblox Luau Scripting Basics

A practical beginner guide to Roblox scripting with Luau.

This is meant to take someone from basically knowing nothing about scripting to being able to read, write, and understand normal Roblox scripts.

---

# Table of Contents

1. [What Is Scripting?](#1-what-is-scripting)
2. [What Is Luau?](#2-what-is-luau)
3. [Your First Script](#3-your-first-script)
4. [Comments](#4-comments)
5. [Variables](#5-variables)
6. [The `local` Keyword](#6-the-local-keyword)
7. [Data Types](#7-data-types)
8. [Strings](#8-strings)
9. [Numbers](#9-numbers)
10. [Booleans](#10-booleans)
11. [`nil`](#11-nil)
12. [Math](#12-math)
13. [Changing Values](#13-changing-values)
14. [If Statements](#14-if-statements)
15. [`else` and `elseif`](#15-else-and-elseif)
16. [Comparison Operators](#16-comparison-operators)
17. [`and`, `or`, and `not`](#17-and-or-and-not)
18. [Functions](#18-functions)
19. [Function Parameters](#19-function-parameters)
20. [`return`](#20-return)
21. [Tables](#21-tables)
22. [Dictionaries](#22-dictionaries)
23. [Loops](#23-loops)
24. [Roblox Services](#24-roblox-services)
25. [Instances](#25-instances)
26. [Properties](#26-properties)
27. [Methods](#27-methods)
28. [The Roblox Hierarchy](#28-the-roblox-hierarchy)
29. [`FindFirstChild`](#29-findfirstchild)
30. [`WaitForChild`](#30-waitforchild)
31. [Events](#31-events)
32. [`Connect`](#32-connect)
33. [Players](#33-players)
34. [Player vs Character](#34-player-vs-character)
35. [Humanoid](#35-humanoid)
36. [`leaderstats`](#36-leaderstats)
37. [Value Objects](#37-value-objects)
38. [Script vs LocalScript](#38-script-vs-localscript)
39. [Server vs Client](#39-server-vs-client)
40. [RemoteEvents](#40-remoteevents)
41. [RemoteFunctions](#41-remotefunctions)
42. [Security](#42-security)
43. [ModuleScripts](#43-modulescripts)
44. [`require`](#44-require)
45. [Scope](#45-scope)
46. [`pairs` and `ipairs`](#46-pairs-and-ipairs)
47. [Type Checking](#47-type-checking)
48. [Attributes](#48-attributes)
49. [Tags](#49-tags)
50. [Cloning](#50-cloning)
51. [Destroying Objects](#51-destroying-objects)
52. [`task.wait`](#52-taskwait)
53. [`task.spawn`](#53-taskspawn)
54. [TweenService](#54-tweenservice)
55. [RunService](#55-runservice)
56. [BindableEvents](#56-bindableevents)
57. [BindableFunctions](#57-bindablefunctions)
58. [Threads and Coroutines](#58-threads-and-coroutines)
59. [Metatables](#59-metatables)
60. [Object-Oriented Programming](#60-object-oriented-programming)
61. [Debugging](#61-debugging)
62. [How to Read Roblox Code](#62-how-to-read-roblox-code)
63. [Using AI for Scripting](#63-using-ai-for-scripting)
64. [Common Mistakes](#64-common-mistakes)
65. [Practice Challenges](#65-practice-challenges)
66. [Beginner Project](#66-beginner-project)
67. [What to Learn Next](#67-what-to-learn-next)

---

# 1. What Is Scripting?

Scripting is writing instructions that a computer executes.

In Roblox, scripts control things like:

- Giving players items
- Changing someone's speed
- Making abilities work
- Opening doors
- Creating enemies
- Giving coins
- Handling damage
- Creating UI
- Teleporting players
- Playing animations
- Spawning objects
- Saving data
- Handling rounds
- Creating abilities
- Making shops work

Example:

```lua
print("Hello world!")
```

When Roblox runs the script, it executes that instruction.

---

# 2. What Is Luau?

Roblox uses a programming language called **Luau**.

Luau is based on Lua, but Roblox added features specifically for game development.

A Roblox script might look like:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	print(player.Name .. " joined the game")
end)
```

There are two things to understand here:

```lua
local Players = game:GetService("Players")
```

This gets the Roblox `Players` service and stores it in a variable called `Players`.

It does **not** directly get every player.

To get the current players:

```lua
local Players = game:GetService("Players")

local players = Players:GetPlayers()
```

---

# 3. Your First Script

Create a normal `Script` inside `ServerScriptService`.

Put this inside:

```lua
print("Hello world!")
```

Run the game.

Open:

**View → Output**

You should see:

```text
Hello world!
```

`print()` is mainly used for testing and debugging.

Another example:

```lua
local coins = 100

print(coins)
```

Output:

```text
100
```

---

# 4. Comments

Comments are notes inside your code.

Roblox ignores them.

Single-line comment:

```lua
-- This is a comment
```

Example:

```lua
local coins = 100 -- Starting coins
```

Multi-line comment:

```lua
--[[
This is a
multi-line comment.
]]
```

Comments are useful for explaining complicated code.

Don't comment every obvious line.

Bad:

```lua
-- Create a variable called coins
local coins = 100
```

Better:

```lua
-- Starting amount for the player's first spawn
local coins = 100
```

---

# 5. Variables

A variable stores information.

Example:

```lua
local coins = 100
```

This means:

- `local` = create a local variable
- `coins` = variable name
- `100` = value

You can then use the variable:

```lua
local coins = 100

print(coins)
```

Output:

```text
100
```

Another example:

```lua
local playerName = "Allie"
local level = 25
local isAdmin = true
```

Variables can store different types of data.

---

# 6. The `local` Keyword

You will use `local` constantly in Roblox scripting.

Example:

```lua
local speed = 16
```

This creates a local variable.

Usually, you should use `local` unless you have a specific reason not to.

For example:

```lua
local damage = 25
local cooldown = 5
local abilityName = "Dash"
```

You can also create local variables inside functions:

```lua
local function test()
	local message = "Hello"

	print(message)
end

test()
```

`message` only exists inside that function.

---

# 7. Data Types

Common Luau data types include:

- `string`
- `number`
- `boolean`
- `nil`
- `table`
- `Instance`
- `Vector3`
- `CFrame`
- `Color3`
- `Enum`

Example:

```lua
local name = "Allie" -- string
local coins = 100 -- number
local alive = true -- boolean
local item = nil -- nil
```

You can check a value's type with `typeof()`:

```lua
local coins = 100

print(typeof(coins))
```

Output:

```text
number
```

For Roblox objects:

```lua
local part = workspace.Part

print(typeof(part))
```

Output:

```text
Instance
```

---

# 8. Strings

A string is text.

```lua
local name = "Allie"
```

Strings can use single or double quotes:

```lua
local message = "Hello"
local message2 = 'Hello'
```

You can combine strings using `..`:

```lua
local firstName = "Allie"
local lastName = "Dev"

local fullName = firstName .. " " .. lastName

print(fullName)
```

Output:

```text
Allie Dev
```

You can also use string interpolation:

```lua
local coins = 100

print(`You have {coins} coins`)
```

This is often easier to read.

---

# 9. Numbers

Numbers are used for values such as:

```lua
local coins = 100
local speed = 16
local damage = 25
local cooldown = 3.5
```

You can perform math:

```lua
local result = 10 + 5

print(result)
```

Output:

```text
15
```

Operators:

```text
+   addition
-   subtraction
*   multiplication
/   division
%   remainder
^   exponent
```

Example:

```lua
local damage = 20
local multiplier = 2

local finalDamage = damage * multiplier

print(finalDamage)
```

Output:

```text
40
```

---

# 10. Booleans

A boolean can only be:

```lua
true
```

or:

```lua
false
```

Example:

```lua
local isAlive = true
local isAdmin = false
```

Booleans are commonly used in conditions:

```lua
local isAlive = true

if isAlive then
	print("Player is alive")
end
```

---

# 11. `nil`

`nil` means there is no value.

Example:

```lua
local item = nil
```

You will often see it when checking whether something exists:

```lua
local part = workspace:FindFirstChild("Part")

if part == nil then
	print("Part does not exist")
end
```

You can also write:

```lua
if not part then
	print("Part does not exist")
end
```

---

# 12. Math

Basic math:

```lua
local a = 10
local b = 5

print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

Useful math functions:

```lua
math.random(1, 10)
```

Returns a random integer between 1 and 10.

Example:

```lua
local number = math.random(1, 100)

print(number)
```

Rounding:

```lua
print(math.floor(5.9))
print(math.ceil(5.1))
print(math.round(5.5))
```

Absolute value:

```lua
print(math.abs(-10))
```

Maximum and minimum:

```lua
print(math.max(10, 20, 5))
print(math.min(10, 20, 5))
```

---

# 13. Changing Values

Variables can change.

```lua
local coins = 100

coins = 150

print(coins)
```

Output:

```text
150
```

You can also change them using the old value:

```lua
local coins = 100

coins = coins + 50

print(coins)
```

Output:

```text
150
```

Common shorthand:

```lua
coins += 50
coins -= 20
coins *= 2
coins /= 2
```

Example:

```lua
local coins = 100

coins += 50

print(coins)
```

---

# 14. If Statements

`if` lets your code make decisions.

Example:

```lua
local coins = 100

if coins >= 50 then
	print("You can buy the item")
end
```

The code inside the `if` only runs if the condition is true.

Structure:

```lua
if condition then
	-- code
end
```

Example:

```lua
local level = 10

if level >= 10 then
	print("Unlocked")
end
```

---

# 15. `else` and `elseif`

`else` runs when the `if` condition is false.

```lua
local coins = 20

if coins >= 50 then
	print("You can buy it")
else
	print("You cannot afford it")
end
```

`elseif` lets you check another condition:

```lua
local level = 15

if level >= 50 then
	print("Very high level")
elseif level >= 20 then
	print("High level")
elseif level >= 10 then
	print("Medium level")
else
	print("Low level")
end
```

Conditions are checked from top to bottom.

---

# 16. Comparison Operators

Common comparison operators:

```text
==    equal to
~=    not equal to
>     greater than
<     less than
>=    greater than or equal to
<=    less than or equal to
```

Examples:

```lua
local coins = 100

if coins == 100 then
	print("Exactly 100")
end

if coins >= 50 then
	print("At least 50")
end

if coins ~= 0 then
	print("Has coins")
end
```

Be careful:

```lua
=
```

assigns a value.

```lua
==
```

checks whether two values are equal.

Example:

```lua
local coins = 100
```

means:

> Set coins to 100.

But:

```lua
if coins == 100 then
```

means:

> Is coins equal to 100?

---

# 17. `and`, `or`, and `not`

These combine conditions.

## `and`

Both conditions must be true.

```lua
local level = 20
local coins = 100

if level >= 10 and coins >= 50 then
	print("Can buy the item")
end
```

## `or`

At least one condition must be true.

```lua
local isAdmin = false
local isOwner = true

if isAdmin or isOwner then
	print("Has permission")
end
```

## `not`

Flips a boolean.

```lua
local isDead = false

if not isDead then
	print("Player is alive")
end
```

---

# 18. Functions

A function is a reusable piece of code.

Example:

```lua
local function sayHello()
	print("Hello!")
end
```

The function doesn't run just because you created it.

Call it:

```lua
sayHello()
```

Complete example:

```lua
local function sayHello()
	print("Hello!")
end

sayHello()
sayHello()
sayHello()
```

Output:

```text
Hello!
Hello!
Hello!
```

Functions are useful when you need to run the same logic multiple times.

---

# 19. Function Parameters

Functions can accept information.

```lua
local function greet(name)
	print("Hello " .. name)
end

greet("Allie")
greet("Xqr")
```

Output:

```text
Hello Allie
Hello Xqr
```

`name` is a parameter.

Another example:

```lua
local function dealDamage(target, damage)
	target.Humanoid:TakeDamage(damage)
end
```

You could call:

```lua
dealDamage(enemy, 25)
```

---

# 20. `return`

A function can give a value back using `return`.

```lua
local function add(a, b)
	return a + b
end

local result = add(10, 5)

print(result)
```

Output:

```text
15
```

Without `return`, the function doesn't give the result back.

Example:

```lua
local function getPlayerName(player)
	return player.Name
end

local name = getPlayerName(player)

print(name)
```

---

# 21. Tables

Tables are one of the most important parts of Luau.

They can store multiple values.

Example:

```lua
local weapons = {
	"Sword",
	"Bow",
	"Gun"
}
```

You can access them using indexes:

```lua
print(weapons[1])
print(weapons[2])
print(weapons[3])
```

Output:

```text
Sword
Bow
Gun
```

Luau starts normal array indexes at `1`, not `0`.

You can add something:

```lua
table.insert(weapons, "Axe")
```

Remove something:

```lua
table.remove(weapons, 1)
```

Get the amount of items:

```lua
print(#weapons)
```

---

# 22. Dictionaries

Tables can also store named values.

```lua
local playerData = {
	Coins = 100,
	Level = 10,
	Deaths = 2
}
```

Access them:

```lua
print(playerData.Coins)
print(playerData.Level)
```

You can also use brackets:

```lua
print(playerData["Coins"])
```

Change them:

```lua
playerData.Coins = 200
```

Add something:

```lua
playerData.Kills = 50
```

A table can also contain other tables:

```lua
local playerData = {
	Coins = 100,

	Stats = {
		Kills = 50,
		Deaths = 10
	}
}

print(playerData.Stats.Kills)
```

---

# 23. Loops

Loops repeat code.

## Numeric `for`

```lua
for i = 1, 5 do
	print(i)
end
```

Output:

```text
1
2
3
4
5
```

You can use the number for other things:

```lua
for i = 1, 10 do
	print("Wave " .. i)
end
```

## `while`

```lua
local count = 0

while count < 5 do
	count += 1
	print(count)
	task.wait(1)
end
```

## `repeat`

```lua
local count = 0

repeat
	count += 1
	print(count)
	task.wait(1)
until count >= 5
```

A `repeat` loop always runs at least once.

---

# 24. Roblox Services

Roblox has services that handle different parts of the engine.

You normally access them with:

```lua
game:GetService("ServiceName")
```

Example:

```lua
local Players = game:GetService("Players")
```

Some important services:

```text
Players
ReplicatedStorage
ServerStorage
ServerScriptService
StarterGui
StarterPlayer
TweenService
RunService
CollectionService
DataStoreService
MarketplaceService
Lighting
SoundService
UserInputService
ContextActionService
```

Example:

```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")
```

---

# 25. Instances

Almost everything you see in Roblox is an `Instance`.

Examples:

- Part
- Model
- Folder
- Script
- LocalScript
- RemoteEvent
- ScreenGui
- TextLabel
- Tool

You can create an Instance with:

```lua
local part = Instance.new("Part")
```

Set its parent:

```lua
part.Parent = workspace
```

Complete example:

```lua
local part = Instance.new("Part")

part.Name = "MyPart"
part.Size = Vector3.new(5, 5, 5)
part.Position = Vector3.new(0, 5, 0)
part.Parent = workspace
```

---

# 26. Properties

Properties describe an Instance.

For a Part:

```lua
part.Name
part.Size
part.Position
part.Transparency
part.CanCollide
part.Anchored
```

You can read a property:

```lua
local transparency = part.Transparency

print(transparency)
```

You can change it:

```lua
part.Transparency = 0.5
```

Another example:

```lua
part.Anchored = true
part.CanCollide = false
```

---

# 27. Methods

Methods are functions attached to objects.

Example:

```lua
part:Destroy()
```

`Destroy()` is a method.

Another example:

```lua
local clone = part:Clone()
```

The colon:

```lua
:
```

is commonly used when calling methods.

Examples:

```lua
part:Destroy()
part:Clone()
part:FindFirstChild("Something")
```

Compare:

```lua
object.Method()
```

and:

```lua
object:Method()
```

Roblox APIs commonly use the second form for methods.

---

# 28. The Roblox Hierarchy

Roblox games have a hierarchy.

Example:

```text
Workspace
├── Map
│   ├── Spawn
│   ├── Enemies
│   └── Towers
│       ├── Tower1
│       └── Tower2
│
ReplicatedStorage
├── Remotes
│   └── Attack
│
ServerScriptService
├── GameManager
│
StarterGui
└── MainGui
```

You can navigate through it using:

```lua
workspace.Map.Towers.Tower1
```

or:

```lua
game.ReplicatedStorage.Remotes.Attack
```

You can also use:

```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local attackEvent = ReplicatedStorage.Remotes.Attack
```

---

# 29. `FindFirstChild`

`FindFirstChild()` searches for an object.

```lua
local part = workspace:FindFirstChild("Part")
```

If it exists, you get the Instance.

If it doesn't exist, you get `nil`.

Example:

```lua
local part = workspace:FindFirstChild("Part")

if part then
	print("Found the part")
else
	print("Part does not exist")
end
```

You can also search recursively:

```lua
local part = workspace:FindFirstChild("Part", true)
```

The second argument tells Roblox to search descendants too.

---

# 30. `WaitForChild`

`WaitForChild()` waits until an object exists.

```lua
local Players = game:GetService("Players")

local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")
```

This is extremely common in Roblox.

Example:

```lua
local ReplicatedStorage = game:GetService("ReplicatedStorage")

local Remotes = ReplicatedStorage:WaitForChild("Remotes")
local AttackEvent = Remotes:WaitForChild("Attack")
```

Difference:

```lua
FindFirstChild()
```

checks immediately.

```lua
WaitForChild()
```

waits for it to appear.

Don't blindly use `WaitForChild()` everywhere if the object should already exist and you actually need to detect a missing object.

---

# 31. Events

Roblox uses events to tell your script that something happened.

Examples:

```text
PlayerAdded
PlayerRemoving
Touched
MouseButton1Click
InputBegan
Changed
AncestryChanged
Heartbeat
RenderStepped
```

Example:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	print(player.Name .. " joined")
end)
```

The function runs whenever the event happens.

---

# 32. `Connect`

`Connect()` connects a function to an event.

Example:

```lua
part.Touched:Connect(function(hit)
	print(hit.Name)
end)
```

When the part is touched, the function runs.

You can also define the function separately:

```lua
local function onTouched(hit)
	print(hit.Name)
end

part.Touched:Connect(onTouched)
```

Both work.

---

# 33. Players

Get the Players service:

```lua
local Players = game:GetService("Players")
```

Get all current players:

```lua
local players = Players:GetPlayers()
```

Loop through them:

```lua
for _, player in Players:GetPlayers() do
	print(player.Name)
end
```

Get a player when they join:

```lua
Players.PlayerAdded:Connect(function(player)
	print(player.Name .. " joined")
end)
```

Detect when they leave:

```lua
Players.PlayerRemoving:Connect(function(player)
	print(player.Name .. " left")
end)
```

---

# 34. Player vs Character

This is important.

A `Player` represents the actual player/account.

A `Character` is the physical character model inside the game.

Example:

```text
Players
└── Allie

Workspace
└── Allie's Character
    ├── Humanoid
    ├── HumanoidRootPart
    ├── Head
    └── ...
```

Get the character:

```lua
local character = player.Character
```

Sometimes the character has not loaded yet.

Use:

```lua
local character = player.Character or player.CharacterAdded:Wait()
```

---

# 35. Humanoid

A `Humanoid` controls many character-related things.

Examples:

```lua
local humanoid = character:WaitForChild("Humanoid")
```

Change walkspeed:

```lua
humanoid.WalkSpeed = 25
```

Change jump power:

```lua
humanoid.JumpPower = 75
```

Damage:

```lua
humanoid:TakeDamage(25)
```

Health:

```lua
print(humanoid.Health)
```

Max health:

```lua
humanoid.MaxHealth = 150
humanoid.Health = 150
```

You can detect death:

```lua
humanoid.Died:Connect(function()
	print("Character died")
end)
```

---

# 36. `leaderstats`

`leaderstats` is a special folder name that Roblox recognizes for displaying values on the default player list.

Example:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	local leaderstats = Instance.new("Folder")
	leaderstats.Name = "leaderstats"
	leaderstats.Parent = player

	local coins = Instance.new("IntValue")
	coins.Name = "Coins"
	coins.Value = 100
	coins.Parent = leaderstats
end)
```

The hierarchy becomes:

```text
Player
└── leaderstats
    └── Coins
```

Then you can change the value:

```lua
local leaderstats = player:WaitForChild("leaderstats")
local coins = leaderstats:WaitForChild("Coins")

coins.Value += 50
```

`leaderstats` is not the actual leaderboard object.

It is a specially named folder that Roblox uses to know which values should appear on the default player list.

---

# 37. Value Objects

Roblox provides Instances for storing values.

Examples:

```text
IntValue
NumberValue
StringValue
BoolValue
ObjectValue
Vector3Value
CFrameValue
```

Example:

```lua
local coins = Instance.new("IntValue")

coins.Name = "Coins"
coins.Value = 100
coins.Parent = player
```

Read it:

```lua
print(coins.Value)
```

Change it:

```lua
coins.Value += 50
```

Value objects also have a `Changed` event:

```lua
coins.Changed:Connect(function(value)
	print("Coins changed to", value)
end)
```

---

# 38. Script vs LocalScript

There are different types of scripts.

## Script

Runs on the server when placed in valid server locations.

Common location:

```text
ServerScriptService
```

Used for things like:

- Damage
- Currency
- Enemy AI
- Round systems
- Data
- Important game logic

## LocalScript

Runs on the player's client.

Common locations:

```text
StarterPlayerScripts
StarterCharacterScripts
StarterGui
Backpack
Tool
```

Used for things like:

- UI
- Camera
- Input
- Local visual effects
- Client-side animations
- Client-side controls

Example:

```lua
local UserInputService = game:GetService("UserInputService")

UserInputService.InputBegan:Connect(function(input, gameProcessed)
	if gameProcessed then
		return
	end

	print(input.KeyCode)
end)
```

---

# 39. Server vs Client

Roblox multiplayer games have a server and clients.

The server is responsible for authoritative game state.

Clients are individual players' game sessions.

A simplified setup:

```text
                 SERVER
                   |
        -----------------------
        |          |          |
      Client     Client     Client
      Player A   Player B   Player C
```

The server should handle important things such as:

- Damage
- Currency
- Inventory
- Rewards
- Purchases
- Important game state
- Enemy spawning
- Match state

The client can handle:

- UI
- Camera
- Input
- Local effects
- Local animation handling

Never assume the client can be trusted.

---

# 40. RemoteEvents

A `RemoteEvent` lets the client and server communicate without returning a value.

Typical setup:

```text
ReplicatedStorage
└── Remotes
    └── Attack
```

The client fires it:

```lua
AttackEvent:FireServer()
```

The server listens:

```lua
AttackEvent.OnServerEvent:Connect(function(player)
	print(player.Name .. " attacked")
end)
```

You can send arguments:

Client:

```lua
AttackEvent:FireServer("Fireball", 25)
```

Server:

```lua
AttackEvent.OnServerEvent:Connect(function(player, abilityName, damage)
	print(player.Name)
	print(abilityName)
	print(damage)
end)
```

Important:

The server should validate the arguments.

Don't do this:

```lua
AttackEvent.OnServerEvent:Connect(function(player, damage)
	player.Character.Humanoid:TakeDamage(damage)
end)
```

because a malicious client could try:

```lua
AttackEvent:FireServer(999999999)
```

The server should decide whether that damage is actually allowed.

---

# 41. RemoteFunctions

`RemoteFunction` is used when you need a response.

Client:

```lua
local result = RemoteFunction:InvokeServer()
```

Server:

```lua
RemoteFunction.OnServerInvoke = function(player)
	return 100
end
```

The client receives:

```lua
result == 100
```

You can send arguments:

```lua
local result = RemoteFunction:InvokeServer("GetCoins")
```

Server:

```lua
RemoteFunction.OnServerInvoke = function(player, request)
	if request == "GetCoins" then
		return 100
	end
end
```

RemoteFunctions can yield while waiting for the response, so don't use them for everything.

---

# 42. Security

Anything important should be controlled by the server.

Bad:

```lua
RemoteEvent.OnServerEvent:Connect(function(player, coins)
	player.leaderstats.Coins.Value += coins
end)
```

A client could request:

```lua
RemoteEvent:FireServer(1000000000)
```

Instead:

```lua
RemoteEvent.OnServerEvent:Connect(function(player)
	local leaderstats = player:FindFirstChild("leaderstats")

	if not leaderstats then
		return
	end

	local coins = leaderstats:FindFirstChild("Coins")

	if not coins then
		return
	end

	coins.Value += 10
end)
```

The client requests the action.

The server decides whether the action is allowed.

This applies to:

- Currency
- Damage
- Items
- Trading
- Purchases
- Rewards
- Teleports
- Abilities
- Inventory
- XP
- Match results

A useful rule:

> The client can ask. The server decides.

---

# 43. ModuleScripts

A `ModuleScript` is a reusable piece of code.

Example:

```lua
local module = {}

function module.Add(a, b)
	return a + b
end

return module
```

You can store it in:

```text
ReplicatedStorage
```

Then another script can use it.

---

# 44. `require`

`require()` loads a ModuleScript.

Example:

```lua
local MathModule = require(game.ReplicatedStorage.MathModule)

local result = MathModule.Add(10, 5)

print(result)
```

You can create modules for:

- Weapons
- Towers
- Abilities
- Utilities
- Configuration
- UI systems
- Enemy data
- Player systems

Example module:

```lua
local WeaponData = {
	Sword = {
		Damage = 25,
		Cooldown = 1
	},

	Bow = {
		Damage = 40,
		Cooldown = 2
	}
}

return WeaponData
```

Then:

```lua
local WeaponData = require(game.ReplicatedStorage.WeaponData)

print(WeaponData.Sword.Damage)
```

---

# 45. Scope

Scope determines where a variable can be accessed.

Example:

```lua
local outside = "Hello"

local function test()
	local inside = "World"

	print(outside)
	print(inside)
end

test()

print(outside)
```

This works because `outside` exists outside the function.

This would not work:

```lua
local function test()
	local inside = "World"
end

print(inside)
```

`inside` only exists inside the function.

A good rule is to keep variables as local as possible.

---

# 46. `pairs` and `ipairs`

You will often loop through tables.

Example:

```lua
local weapons = {
	"Sword",
	"Bow",
	"Gun"
}

for index, weapon in ipairs(weapons) do
	print(index, weapon)
end
```

For dictionaries:

```lua
local playerData = {
	Coins = 100,
	Level = 20,
	Kills = 50
}

for key, value in pairs(playerData) do
	print(key, value)
end
```

`ipairs` is commonly used for array-like tables.

`pairs` is commonly used for dictionaries.

Modern Luau also supports:

```lua
for key, value in weapons do
	print(key, value)
end
```

---

# 47. Type Checking

You can check values using `typeof()`.

```lua
local value = 100

print(typeof(value))
```

You can also use Luau type annotations.

Example:

```lua
local coins: number = 100
local playerName: string = "Allie"
local isAlive: boolean = true
```

Functions can have typed parameters:

```lua
local function add(a: number, b: number): number
	return a + b
end
```

This helps catch mistakes while developing.

Example:

```lua
local function damageEnemy(enemy: Model, damage: number)
	local humanoid = enemy:FindFirstChildOfClass("Humanoid")

	if humanoid then
		humanoid:TakeDamage(damage)
	end
end
```

---

# 48. Attributes

Attributes are custom values you can attach to Instances.

Example:

```lua
local part = workspace.Part

part:SetAttribute("Damage", 25)
part:SetAttribute("IsBoss", true)
```

Read them:

```lua
local damage = part:GetAttribute("Damage")
local isBoss = part:GetAttribute("IsBoss")
```

Check if it exists:

```lua
if part:GetAttribute("IsBoss") then
	print("This is a boss")
end
```

You can detect changes:

```lua
part:GetAttributeChangedSignal("Damage"):Connect(function()
	print("Damage changed")
end)
```

Attributes are useful for storing configuration directly on objects.

---

# 49. Tags

Roblox has `CollectionService` for tagging objects.

Get the service:

```lua
local CollectionService = game:GetService("CollectionService")
```

Add a tag:

```lua
CollectionService:AddTag(part, "Enemy")
```

Check a tag:

```lua
if CollectionService:HasTag(part, "Enemy") then
	print("This is an enemy")
end
```

Get every object with a tag:

```lua
local enemies = CollectionService:GetTagged("Enemy")

for _, enemy in enemies do
	print(enemy.Name)
end
```

This is useful when you have many objects that need the same behavior.

---

# 50. Cloning

You can copy an Instance using:

```lua
local clone = object:Clone()
```

Example:

```lua
local template = game.ServerStorage.Enemy

local enemy = template:Clone()

enemy.Parent = workspace
```

The original stays in `ServerStorage`.

This is commonly used for:

- Enemies
- Towers
- Tools
- Effects
- Maps
- UI
- Projectiles

---

# 51. Destroying Objects

Use:

```lua
object:Destroy()
```

Example:

```lua
local part = workspace.Part

part:Destroy()
```

After destroying an Instance, don't keep trying to use it as though it still exists.

You can also destroy something after a delay:

```lua
task.delay(5, function()
	if part then
		part:Destroy()
	end
end)
```

---

# 52. `task.wait`

Use `task.wait()` instead of the old `wait()` function.

Example:

```lua
task.wait(2)

print("Two seconds passed")
```

Loop:

```lua
while true do
	print("Hello")
	task.wait(1)
end
```

This prints approximately once per second.

Do not make extremely fast infinite loops for no reason.

Bad:

```lua
while true do
	print("Hello")
end
```

This can waste resources.

---

# 53. `task.spawn`

`task.spawn()` starts a function without making the current code wait for it to finish.

Example:

```lua
task.spawn(function()
	task.wait(5)
	print("Finished")
end)

print("This prints immediately")
```

This is useful when you want another piece of work to run separately.

Don't use `task.spawn()` everywhere just because it exists.

---

# 54. TweenService

`TweenService` smoothly changes properties over time.

Example:

```lua
local TweenService = game:GetService("TweenService")

local part = workspace.Part

local info = TweenInfo.new(2)

local goal = {
	Position = Vector3.new(0, 10, 0)
}

local tween = TweenService:Create(part, info, goal)

tween:Play()
```

The part moves smoothly to the new position.

You can tween properties such as:

```text
Position
Size
Transparency
Color
CFrame
Rotation
UI properties
```

Example with transparency:

```lua
local TweenService = game:GetService("TweenService")

local info = TweenInfo.new(1)

local goal = {
	Transparency = 1
}

local tween = TweenService:Create(part, info, goal)

tween:Play()
```

---

# 55. RunService

`RunService` gives you events related to Roblox's update loop.

```lua
local RunService = game:GetService("RunService")
```

Common events:

```text
Heartbeat
Stepped
RenderStepped
```

Example:

```lua
RunService.Heartbeat:Connect(function(deltaTime)
	print(deltaTime)
end)
```

`deltaTime` is the amount of time since the previous update.

`RenderStepped` is client-side and is commonly used for things that need to update with rendering, such as camera effects.

Don't put expensive code into a frame event unless it actually needs to run every frame.

---

# 56. BindableEvents

A `BindableEvent` allows scripts on the same side of the client/server boundary to communicate.

Example:

```text
ServerScriptService
└── Events
    └── RoundStarted
```

Fire:

```lua
RoundStarted:Fire()
```

Listen:

```lua
RoundStarted.Event:Connect(function()
	print("Round started")
end)
```

A BindableEvent does not communicate between server and client.

For server/client communication, use `RemoteEvent`.

---

# 57. BindableFunctions

`BindableFunction` is similar to a `BindableEvent`, but it returns a value.

Example:

```lua
BindableFunction.OnInvoke = function(value)
	return value * 2
end
```

Call it:

```lua
local result = BindableFunction:Invoke(10)

print(result)
```

Output:

```text
20
```

Use this when code on the same side needs a response.

---

# 58. Threads and Coroutines

Luau can run different pieces of code independently.

A simple example:

```lua
task.spawn(function()
	for i = 1, 5 do
		print(i)
		task.wait(1)
	end
end)

print("Main code continues")
```

The spawned function runs separately.

You generally don't need to worry about advanced coroutine usage when you're starting out.

Understand:

- Functions
- Events
- `task.spawn`
- `task.delay`
- `task.wait`

first.

---

# 59. Metatables

Metatables are an advanced Luau feature.

They can change how tables behave.

Example:

```lua
local object = {}

local meta = {
	__index = {
		Health = 100
	}
}

setmetatable(object, meta)

print(object.Health)
```

Output:

```text
100
```

Metatables are commonly used for advanced systems and OOP-style code.

You do not need them for basic Roblox scripting.

---

# 60. Object-Oriented Programming

OOP is a way of organizing code around objects.

A simple Luau pattern:

```lua
local Enemy = {}
Enemy.__index = Enemy

function Enemy.new(name, health)
	local self = setmetatable({}, Enemy)

	self.Name = name
	self.Health = health

	return self
end

function Enemy:TakeDamage(amount)
	self.Health -= amount
end

return Enemy
```

Then:

```lua
local Enemy = require(path.To.Enemy)

local zombie = Enemy.new("Zombie", 100)

zombie:TakeDamage(25)

print(zombie.Health)
```

Output:

```text
75
```

The important ideas are:

```text
class-like table
constructor
object
methods
metatable
```

Don't worry about mastering OOP before understanding normal functions and tables.

---

# 61. Debugging

Debugging means finding and fixing problems in your code.

The Output window is one of your main tools.

Use:

```lua
print("Reached here")
```

Example:

```lua
print("Starting attack")

local target = workspace:FindFirstChild("Enemy")

print("Target:", target)

if target then
	print("Found target")
end
```

You can print multiple values:

```lua
print("Player:", player.Name, "Coins:", coins.Value)
```

Warnings:

```lua
warn("Something went wrong")
```

Errors:

```lua
error("Something went wrong")
```

You can also use:

```lua
assert(value, "Value was missing")
```

Example:

```lua
local part = workspace:FindFirstChild("Part")

assert(part, "Part was not found")
```

When debugging, don't randomly change ten things at once.

Find where the code stops working.

---

# 62. How to Read Roblox Code

Don't try to understand a huge script all at once.

Break it down.

Example:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	local leaderstats = Instance.new("Folder")
	leaderstats.Name = "leaderstats"
	leaderstats.Parent = player

	local coins = Instance.new("IntValue")
	coins.Name = "Coins"
	coins.Value = 100
	coins.Parent = leaderstats
end)
```

Read it from top to bottom.

First:

```lua
local Players = game:GetService("Players")
```

This gets the Players service.

Then:

```lua
Players.PlayerAdded
```

This is the event that fires when a player joins.

Then:

```lua
:Connect(function(player)
```

This connects a function to that event.

Then:

```lua
local leaderstats = Instance.new("Folder")
```

Creates a Folder.

Then:

```lua
leaderstats.Name = "leaderstats"
```

Changes its name.

Then:

```lua
leaderstats.Parent = player
```

Places the folder inside the player.

Then:

```lua
local coins = Instance.new("IntValue")
```

Creates an IntValue.

Then:

```lua
coins.Name = "Coins"
coins.Value = 100
coins.Parent = leaderstats
```

Creates the Coins value and puts it inside leaderstats.

This is how you should approach unfamiliar code:

1. Find what is being created.
2. Find what is being stored in variables.
3. Find what events are being connected.
4. Find what functions are being called.
5. Find what conditions exist.
6. Find what values are being changed.
7. Follow the hierarchy.

---

# 63. Using AI for Scripting

AI can be useful for Roblox scripting, but blindly pasting code makes it harder to learn.

A better way to use AI:

### Ask for explanations

Instead of:

```text
Make me a tower defense system.
```

Try:

```text
Explain this Roblox script line by line.
Assume I am a beginner.
Do not rewrite it.
```

Or:

```text
Explain what this line does and why it is needed:

local Players = game:GetService("Players")
```

You can also ask:

```text
Give me a small Roblox scripting exercise.
Don't give me the answer until I try it.
```

When code doesn't work, give the AI:

- The script
- The error
- Where the script is located
- What you expected to happen
- What actually happened

Example:

```text
This is a ServerScriptService Script.

I expected the door to open when touched.

Instead, nothing happens.

Here is the code:

[paste code]

Here is the Output error:

[paste error]
```

Don't just say:

```text
it doesn't work
```

because there isn't enough information.

---

# 64. Common Mistakes

## Mistake 1: Using `=` instead of `==`

Wrong:

```lua
if coins = 100 then
```

Correct:

```lua
if coins == 100 then
```

---

## Mistake 2: Forgetting `end`

Wrong:

```lua
if coins > 10 then
	print("Enough")
```

Correct:

```lua
if coins > 10 then
	print("Enough")
end
```

---

## Mistake 3: Using a variable before creating it

Wrong:

```lua
print(coins)

local coins = 100
```

Correct:

```lua
local coins = 100

print(coins)
```

---

## Mistake 4: Confusing Player and Character

Wrong idea:

```lua
player.Humanoid
```

The Humanoid is normally inside the character:

```lua
player.Character.Humanoid
```

Better:

```lua
local character = player.Character or player.CharacterAdded:Wait()
local humanoid = character:WaitForChild("Humanoid")
```

---

## Mistake 5: Trusting the client

Never let the client decide important values such as:

```text
Coins = 999999999
Damage = 999999999
Level = 100000
```

The server should validate important actions.

---

## Mistake 6: Not checking if something exists

This can error:

```lua
local part = workspace:FindFirstChild("Part")

print(part.Position)
```

If `part` doesn't exist, this fails.

Safer:

```lua
local part = workspace:FindFirstChild("Part")

if part then
	print(part.Position)
end
```

---

## Mistake 7: Wrong script type

If you're trying to detect keyboard input in a normal server Script, that's usually the wrong place.

Input is normally handled by a `LocalScript`.

---

## Mistake 8: Wrong location

A LocalScript won't run everywhere.

A normal Script also won't run everywhere.

Always check where the script is placed.

---

## Mistake 9: Infinite loops with no wait

Bad:

```lua
while true do
	print("Hello")
end
```

Better:

```lua
while true do
	print("Hello")
	task.wait(1)
end
```

---

## Mistake 10: Huge scripts

If one script is doing:

```text
UI
Combat
Inventory
Data
Enemies
Round system
Shop
Trading
```

all at once, it becomes difficult to maintain.

Split systems into separate scripts and ModuleScripts.

---

# 65. Practice Challenges

Do these without looking up the answer immediately.

## Challenge 1

Create a variable called `coins` with a value of `100`.

Print it.

---

## Challenge 2

Create a variable called `speed`.

If speed is greater than or equal to `20`, print:

```text
Fast
```

Otherwise print:

```text
Slow
```

---

## Challenge 3

Create a function called:

```lua
giveCoins
```

It should accept an amount and print:

```text
Giving X coins
```

---

## Challenge 4

Create a table containing:

```text
Sword
Bow
Gun
```

Loop through the table and print every weapon.

---

## Challenge 5

Create a Part through a script.

Give it:

```text
Name = TestPart
Size = 5, 5, 5
Anchored = true
```

Parent it to Workspace.

---

## Challenge 6

Create a script that detects when a player joins.

Print:

```text
PLAYERNAME joined
```

---

## Challenge 7

Create a `leaderstats` folder with:

```text
Coins
```

Give the player 100 coins when they join.

---

## Challenge 8

Create a Part.

When the Part is touched, print:

```text
Touched!
```

---

## Challenge 9

Create a Part that changes to:

```text
Transparency = 1
```

when touched.

---

## Challenge 10

Create a RemoteEvent.

When the client fires it, the server prints:

```text
PLAYERNAME fired the event
```

---

# 66. Beginner Project

Build a simple coin collection system.

The player should:

1. Join the game.
2. Receive a Coins value.
3. Find a coin.
4. Touch the coin.
5. Gain 10 coins.
6. The coin disappears.
7. After a few seconds, the coin comes back.

---

## Step 1: Create leaderstats

Create a Script in:

```text
ServerScriptService
```

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	local leaderstats = Instance.new("Folder")
	leaderstats.Name = "leaderstats"
	leaderstats.Parent = player

	local coins = Instance.new("IntValue")
	coins.Name = "Coins"
	coins.Value = 0
	coins.Parent = leaderstats
end)
```

---

## Step 2: Create the Coin

Create a Part in Workspace.

Name it:

```text
Coin
```

Set:

```text
Anchored = true
CanCollide = false
```

---

## Step 3: Add the Coin Script

Put a Script inside the Coin.

```lua
local Players = game:GetService("Players")

local coin = script.Parent
local debounce = false

coin.Touched:Connect(function(hit)
	if debounce then
		return
	end

	local character = hit.Parent

	if not character then
		return
	end

	local player = Players:GetPlayerFromCharacter(character)

	if not player then
		return
	end

	local leaderstats = player:FindFirstChild("leaderstats")

	if not leaderstats then
		return
	end

	local coins = leaderstats:FindFirstChild("Coins")

	if not coins then
		return
	end

	debounce = true

	coins.Value += 10

	coin.Transparency = 1

	task.wait(3)

	coin.Transparency = 0

	debounce = false
end)
```

---

## What this script is doing

First:

```lua
local Players = game:GetService("Players")
```

Gets the Players service.

Then:

```lua
local coin = script.Parent
```

Gets the Part containing the script.

Then:

```lua
local debounce = false
```

Creates a variable used to stop the coin from being collected multiple times at once.

Then:

```lua
coin.Touched:Connect(function(hit)
```

Runs when something touches the coin.

Then:

```lua
local character = hit.Parent
```

Gets the model containing whatever touched the coin.

Then:

```lua
local player = Players:GetPlayerFromCharacter(character)
```

Checks whether that character belongs to a player.

Then:

```lua
coins.Value += 10
```

Adds 10 coins.

Then:

```lua
coin.Transparency = 1
```

Makes the coin invisible.

Then:

```lua
task.wait(3)
```

Waits three seconds.

Then:

```lua
coin.Transparency = 0
```

Makes the coin visible again.

---

# 67. What to Learn Next

After the basics, move into these topics.

## Roblox Gameplay

Learn:

- Tools
- Raycasting
- Damage systems
- Hit detection
- Weapons
- Abilities
- Cooldowns
- NPCs
- Pathfinding
- Animations
- ProximityPrompts

## UI

Learn:

- ScreenGui
- Frames
- TextLabels
- TextButtons
- ImageLabels
- UIListLayout
- UIGridLayout
- UIStroke
- UICorner
- TweenService
- UI scaling
- ViewportFrames

## Multiplayer

Learn:

- RemoteEvents
- RemoteFunctions
- Server validation
- Client/server architecture
- Replication
- Network ownership

## Data

Learn:

- DataStoreService
- Saving
- Loading
- Data validation
- Session locking
- Profile/data libraries

## Advanced Luau

Learn:

- Type annotations
- Module architecture
- Metatables
- OOP patterns
- Generics
- Strict typing
- Advanced table operations

## Performance

Learn:

- Avoiding unnecessary loops
- Connection cleanup
- Memory leaks
- Client/server workload
- StreamingEnabled
- Profiling
- MicroProfiler

---

# Basic Roblox Scripting Cheat Sheet

## Get a service

```lua
local Players = game:GetService("Players")
```

## Get the current players

```lua
local players = Players:GetPlayers()
```

## Detect player joining

```lua
Players.PlayerAdded:Connect(function(player)
	print(player.Name)
end)
```

## Get a character

```lua
local character = player.Character or player.CharacterAdded:Wait()
```

## Get a Humanoid

```lua
local humanoid = character:WaitForChild("Humanoid")
```

## Change WalkSpeed

```lua
humanoid.WalkSpeed = 25
```

## Damage a Humanoid

```lua
humanoid:TakeDamage(25)
```

## Find something

```lua
local object = workspace:FindFirstChild("Object")
```

## Wait for something

```lua
local object = workspace:WaitForChild("Object")
```

## Create an Instance

```lua
local part = Instance.new("Part")
```

## Parent an Instance

```lua
part.Parent = workspace
```

## Clone an Instance

```lua
local clone = part:Clone()
```

## Destroy an Instance

```lua
part:Destroy()
```

## Connect an event

```lua
part.Touched:Connect(function(hit)
	print(hit.Name)
end)
```

## Create a function

```lua
local function test()
	print("Hello")
end
```

## Call a function

```lua
test()
```

## Return a value

```lua
local function add(a, b)
	return a + b
end
```

## Create a table

```lua
local items = {
	"Sword",
	"Bow",
	"Gun"
}
```

## Loop through a table

```lua
for _, item in items do
	print(item)
end
```

## Create a condition

```lua
if coins >= 100 then
	print("Enough coins")
end
```

## Create an else

```lua
if coins >= 100 then
	print("Enough")
else
	print("Not enough")
end
```

## Wait

```lua
task.wait(1)
```

## Spawn a task

```lua
task.spawn(function()
	print("Running separately")
end)
```

## Print debugging information

```lua
print("Value:", value)
```

## Warning

```lua
warn("Something went wrong")
```

---

# How to Teach Someone Roblox Scripting

If you're teaching someone else, don't immediately explain every line for them.

A useful way to teach is:

1. Show a small piece of code.
2. Ask what they think it does.
3. Let them explain it.
4. Correct anything that's wrong.
5. Add the missing details.
6. Give them a slightly different example.
7. Ask them to explain that one too.
8. Eventually make them write it themselves.

Example:

Show:

```lua
local Players = game:GetService("Players")
```

Ask:

> What do you think this does?

If they say:

> It gets all the players.

Correct it:

> Close. It gets the Players service. To get the players currently in the game, you would use `Players:GetPlayers()`.

Then:

```lua
local players = Players:GetPlayers()
```

Ask again what they think it does.

This helps them learn how to read code instead of memorizing random lines.

---

# Important Things to Understand

You don't need to memorize every Roblox API.

You should understand the basic ideas behind the code.

For example:

```lua
local Players = game:GetService("Players")

Players.PlayerAdded:Connect(function(player)
	print(player.Name)
end)
```

You should eventually be able to recognize:

```text
local
variable
service
event
Connect
function
parameter
property
method
```

Once you understand what those pieces mean, you can start reading much larger scripts.

---

# Final Reference

When you see:

```lua
local Players = game:GetService("Players")
```

Think:

> Get the Players service and store it in a variable.

When you see:

```lua
Players.PlayerAdded:Connect(function(player)
```

Think:

> When a player joins, run this function.

When you see:

```lua
player.Character
```

Think:

> The player's character model.

When you see:

```lua
character:WaitForChild("Humanoid")
```

Think:

> Wait until the character has a Humanoid, then get it.

When you see:

```lua
humanoid.WalkSpeed = 25
```

Think:

> Change the Humanoid's WalkSpeed property.

When you see:

```lua
RemoteEvent:FireServer()
```

Think:

> The client is sending a request to the server.

When you see:

```lua
RemoteEvent.OnServerEvent:Connect(function(player)
```

Think:

> The server is receiving that request.

When you see:

```lua
Instance.new("Part")
```

Think:

> Create a new Roblox Instance.

When you see:

```lua
object:Clone()
```

Think:

> Make a copy of this Instance.

When you see:

```lua
object:Destroy()
```

Think:

> Remove this Instance.

When you see:

```lua
if condition then
```

Think:

> Only run this code if the condition is true.

When you see:

```lua
local function test()
```

Think:

> Define a reusable function.

When you see:

```lua
return value
```

Think:

> Give a value back to whatever called this function.

When you see:

```lua
for _, item in items do
```

Think:

> Repeat this code for each item in the table.

When you see:

```lua
task.wait(1)
```

Think:

> Pause this thread for approximately one second.

The main thing to practice is reading code and figuring out what each part is doing. Once that becomes familiar, writing the code becomes much easier.
