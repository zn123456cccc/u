-----------//GATTAI ZAMASU\\-----------
--[[Movelist
E = Blades of Judgement
R = Holy light
T = Taunt
Y = Lightning of Absolution
U = Divine wrath/Holy wrath
---------]]
 
--I'm starting my own youtube channel to showcase my private/best work, if you're interested, be sure to check it out! https://www.youtube.com/channel/UCN6i8M5gV1KgsGHLNQZGLgQ--
--It currently has no content as of 1/20/19, but in the near future i'll post some videos & scripting tutorials for the newbs out there.--
--Also subscribe to this d00d: https://www.youtube.com/channel/UC2hsp8ie2iYsJGK-zRD0sPg--
--And no, you cannot have my privates, however, over time i'll release one of my privates for 1 hour only--
--Also, check out my pastebin, it'll give you some handy information too--
--Enough frickin' around, enjoy the script lads--
 
Player=game:GetService("Players").LocalPlayer
Character=Player.Character
Character.Humanoid.Name = "gattaizamasu"
hum = Character.gattaizamasu
LeftArm=Character["Left Arm"]
LeftLeg=Character["Left Leg"]
RightArm=Character["Right Arm"]
RightLeg=Character["Right Leg"]
Root=Character["HumanoidRootPart"]
Head=Character["Head"]
Torso=Character["Torso"]
Neck=Torso["Neck"]
attacking = false
laughing = false
id = 2623171639
taim = nil
change = 0
ws = 90
hpheight = 5
dedlaff = false
appi = false
tauntdebounce = false
allowlev = true
position = nil
MseGuide = true
running = false
levitate = false
settime = 0
sine = 0
t = 0
dgs = 75
mouse = Player:GetMouse()
RunSrv = game:GetService("RunService")
RenderStepped = game:GetService("RunService").RenderStepped
removeuseless = game:GetService("Debris")
local soundtable = {2638719005,2638719700,2638743317,2638744272,2638751297,2638751506,2638769242,2638769810,2638770257,2638777924}
local holywrathcolors = {"Really red","Bright orange"}
rdnm = #soundtable
hwc = #holywrathcolors
 
screenGui = Instance.new("ScreenGui")
screenGui.Parent = script.Parent
 
local HEADLERP = Instance.new("ManualWeld")
HEADLERP.Parent = Head
HEADLERP.Part0 = Head
HEADLERP.Part1 = Head
HEADLERP.C0 = CFrame.new(0, -1.5, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local TORSOLERP = Instance.new("ManualWeld")
TORSOLERP.Parent = Root
TORSOLERP.Part0 = Torso
TORSOLERP.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local ROOTLERP = Instance.new("ManualWeld")
ROOTLERP.Parent = Root
ROOTLERP.Part0 = Root
ROOTLERP.Part1 = Torso
ROOTLERP.C0 = CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local RIGHTARMLERP = Instance.new("ManualWeld")
RIGHTARMLERP.Parent = RightArm
RIGHTARMLERP.Part0 = RightArm
RIGHTARMLERP.Part1 = Torso
RIGHTARMLERP.C0 = CFrame.new(-1.5, 0, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local LEFTARMLERP = Instance.new("ManualWeld")
LEFTARMLERP.Parent = LeftArm
LEFTARMLERP.Part0 = LeftArm
LEFTARMLERP.Part1 = Torso
LEFTARMLERP.C0 = CFrame.new(1.5, 0, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local RIGHTLEGLERP = Instance.new("ManualWeld")
RIGHTLEGLERP.Parent = RightLeg
RIGHTLEGLERP.Part0 = RightLeg
RIGHTLEGLERP.Part1 = Torso
RIGHTLEGLERP.C0 = CFrame.new(-0.5, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local LEFTLEGLERP = Instance.new("ManualWeld")
LEFTLEGLERP.Parent = LeftLeg
LEFTLEGLERP.Part0 = LeftLeg
LEFTLEGLERP.Part1 = Torso
LEFTLEGLERP.C0 = CFrame.new(0.5, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
 
local function weldBetween(a, b)
    local weld = Instance.new("ManualWeld", a)
    weld.Part0 = a
    weld.Part1 = b
    weld.C0 = a.CFrame:inverse() * b.CFrame
    return weld
end
 
function MAKETRAIL(PARENT,POSITION1,POSITION2,LIFETIME,COLOR)
A = Instance.new("Attachment", PARENT)
A.Position = POSITION1
A.Name = "A"
B = Instance.new("Attachment", PARENT)
B.Position = POSITION2
B.Name = "B"
tr1 = Instance.new("Trail", PARENT)
tr1.Attachment0 = A
tr1.Attachment1 = B
tr1.Enabled = true
tr1.Lifetime = LIFETIME
tr1.TextureMode = "Static"
tr1.LightInfluence = 0
tr1.Color = COLOR
tr1.Transparency = NumberSequence.new(0, 1)
end
 
coroutine.wrap(function()
while wait() do
hum.WalkSpeed = ws
Head.face.Texture = "rbxassetid://1322462890"
LeftArm.BrickColor = BrickColor.new("Olivine")
RightArm.BrickColor = BrickColor.new("Olivine")
Head.BrickColor = BrickColor.new("Olivine")
end
end)()
godmode = coroutine.wrap(function()
for i,v in pairs(Character:GetChildren()) do
if v:IsA("BasePart") and v ~= Root then
v.Anchored = false
end
end
while true do
hum.MaxHealth = math.huge
wait(0.0000001)
hum.Health = math.huge
wait()
end
end)
godmode()
ff = Instance.new("ForceField", Character)
ff.Visible = false
 
coroutine.wrap(function()
for i,v in pairs(Character:GetChildren()) do
if v.Name == "Animate" then v:Remove()
end
end
end)()
 
for _,n in pairs(Character:GetChildren()) do
if n:IsA("Accessory") then n:Remove() end
end
for _,x in pairs(Character:GetChildren()) do
if x:IsA("Decal") then x:Remove() end
end
 
hair = Instance.new("Part",Character)
hair.Size = Vector3.new(2,2,2)
hair.CFrame = hair.CFrame:inverse() * Head.CFrame * CFrame.new(0,-.85,0)
hair.Anchored = false
hair.Name = "hair"
hair.BrickColor = BrickColor.new("Lily white")
hairmesh = Instance.new("SpecialMesh", hair)
hairmesh.MeshType = "FileMesh"
hairmesh.Scale = Vector3.new(5.839, 5.737, 5.947)
hairmesh.MeshId = "rbxassetid://568050133"
hairweld = weldBetween(hair,Head)
hairweld.C0 = hair.CFrame:inverse() * Head.CFrame * CFrame.new(.055,-.9,-.4)
 
ears = Instance.new("Part",Character)
ears.Size = Vector3.new(2,2,2)
ears.CFrame = ears.CFrame:inverse() * Head.CFrame * CFrame.new(0,-.85,0)
ears.Anchored = false
ears.Name = "ears"
ears.BrickColor = BrickColor.new("Olivine")
earsmesh = Instance.new("SpecialMesh", ears)
earsmesh.MeshType = "FileMesh"
earsmesh.Scale = Vector3.new(1,1,1.1)
earsmesh.MeshId = "rbxassetid://19383407"
earsweld = weldBetween(ears,Head)
earsweld.C0 = ears.CFrame:inverse() * Head.CFrame * CFrame.new(0,0,0)
 
potara = Instance.new("Part",Character)
potara.Size = Vector3.new(2,2,2)
potara.CFrame = potara.CFrame:inverse() * Head.CFrame * CFrame.new(0,-.85,0)
potara.Anchored = false
potara.Name = "ears"
potara.BrickColor = BrickColor.new("Gold")
potaramesh = Instance.new("SpecialMesh", potara)
potaramesh.MeshType = "FileMesh"
potaramesh.Scale = Vector3.new(1,1,1)
potaramesh.MeshId = "rbxassetid://2623281326"
potaraweld = weldBetween(potara,Head)
potaraweld.C0 = potara.CFrame:inverse() * Head.CFrame * CFrame.new(0,.25,0)
 
halo = Instance.new("Part",Character)
halo.Size = Vector3.new(2,2,2)
halo.CFrame = Root.CFrame * CFrame.new(0,0,2)
halo.Anchored = false
halo.Name = "halo"
halo.Transparency = 1
halo.BrickColor = BrickColor.new("White")
halo.Material = "Neon"
halomesh = Instance.new("SpecialMesh", halo)
halomesh.MeshType = "FileMesh"
halomesh.Scale = Vector3.new(11,11,11)
halomesh.MeshId = "rbxassetid://2621604441"
haloweld = weldBetween(halo,Torso)
haloweld.C0 = CFrame.new(0,-4.5,-2)
 
shirt = Instance.new("Shirt", Character)
shirt.Name = "Shirt"
pants = Instance.new("Pants", Character)
pants.Name = "Pants"
Character.Shirt.ShirtTemplate = "http://www.roblox.com/asset/?id=715059748"
Character.Pants.PantsTemplate = "http://www.roblox.com/asset/?id=745414427"
 
function damagealll(Radius,Position)		
	local Returning = {}		
	for _,v in pairs(workspace:GetChildren()) do		
		if v~=Character and v:FindFirstChildOfClass('Humanoid') and v:FindFirstChild('Torso') or v:FindFirstChild('UpperTorso') then
if v:FindFirstChild("Torso") then		
			local Mag = (v.Torso.Position - Position).magnitude		
			if Mag < Radius then		
				table.insert(Returning,v)		
			end
elseif v:FindFirstChild("UpperTorso") then	
			local Mag = (v.UpperTorso.Position - Position).magnitude		
			if Mag < Radius then		
				table.insert(Returning,v)		
			end
end	
		end		
	end		
	return Returning		
end
 
ArtificialHB = Instance.new("BindableEvent", script)
ArtificialHB.Name = "Heartbeat"
script:WaitForChild("Heartbeat")
 
frame = 1 / 60
tf = 0
allowframeloss = false
tossremainder = false
 
 
lastframe = tick()
script.Heartbeat:Fire()
 
 
game:GetService("RunService").Heartbeat:connect(function(s, p)
	tf = tf + s
	if tf >= frame then
		if allowframeloss then
			script.Heartbeat:Fire()
			lastframe = tick()
		else
			for i = 1, math.floor(tf / frame) do
				script.Heartbeat:Fire()
			end
			lastframe = tick()
		end
		if tossremainder then
			tf = 0
		else
			tf = tf - frame * math.floor(tf / frame)
		end
	end
end)
 
function swait(num)
	if num == 0 or num == nil then
		game:service("RunService").Stepped:wait(0)
	else
		for i = 0, num do
			game:service("RunService").Stepped:wait(0)
		end
	end
end
 
doomtheme = Instance.new("Sound", Torso)
doomtheme.Volume = 3
doomtheme.Name = "doomtheme"
doomtheme.Looped = true
doomtheme.SoundId = "rbxassetid://"..id
doomtheme:Play()
 
Aura = Instance.new("Sound",Torso)
Aura.Volume = 3
Aura.Name = "aura"
Aura.Looped = true
Aura.SoundId = "rbxassetid://2643712818"
Aura:Play()
 
Powerup = Instance.new("Sound",Torso)
Powerup.Volume = powvol
Powerup.SoundId = "rbxassetid://2492215919"
Powerup.Name = "powerup"
Powerup:Play()
Powerup.Looped = true
 
Torso.ChildRemoved:connect(function(removed)
if removed.Name == "aura" then
Powerup = Instance.new("Sound",Torso)
Powerup.Volume = powvol
Powerup.SoundId = "rbxassetid://2492215919"
Powerup.Name = "powerup"
Powerup:Play()
Powerup.Looped = true
end
end)
 
Torso.ChildRemoved:connect(function(removed)
if removed.Name == "doomtheme" then
doomtheme = Instance.new("Sound",Torso)
doomtheme.Volume = 3
doomtheme.Name = "doomtheme"
doomtheme.Looped = true
doomtheme.SoundId = "rbxassetid://"..id
doomtheme:Play()
end
end)
 
coroutine.wrap(function()
while wait() do
pcall(function()
Powerup.Volume = powvol
end)
end
end)()
 
function SOUND(PARENT,ID,VOL,LOOP,REMOVE)
so = Instance.new("Sound")
so.Parent = PARENT
so.SoundId = "rbxassetid://"..ID
so.Volume = VOL
so.Looped = LOOP
so:Play()
removeuseless:AddItem(so,REMOVE)
end
 
particlecolor = ColorSequence.new(Color3.new(0, 5, 255))
 
goldpart = Instance.new("Part",RightArm)
goldpart.Size = Vector3.new(1.01,2.01,1.01)
goldpart.BrickColor = BrickColor.new("Gold")
goldpart.Material = "Neon"
goldpart.CanCollide = false
goldpart.Anchored = false
goldpartweld = weldBetween(goldpart,RightArm)
 
goldpart2 = Instance.new("Part",RightLeg)
goldpart2.Size = Vector3.new(1.01,2.01,1.01)
goldpart2.BrickColor = BrickColor.new("Gold")
goldpart2.Material = "Neon"
goldpart2.CanCollide = false
goldpart2.Anchored = false
goldpartweld2 = weldBetween(goldpart2,RightLeg)
 
goldpart3 = Instance.new("Part",LeftLeg)
goldpart3.Size = Vector3.new(1.01,2.01,1.01)
goldpart3.BrickColor = BrickColor.new("Gold")
goldpart3.Material = "Neon"
goldpart3.CanCollide = false
goldpart3.Anchored = false
goldpartweld3 = weldBetween(goldpart3,LeftLeg)
 
goldpart4 = Instance.new("Part",LeftArm)
goldpart4.Size = Vector3.new(1.01,2.01,1.01)
goldpart4.BrickColor = BrickColor.new("Gold")
goldpart4.Material = "Neon"
goldpart4.CanCollide = false
goldpart4.Anchored = false
goldpartweld4 = weldBetween(goldpart4,LeftArm)
 
goldpart5 = Instance.new("Part",Torso)
goldpart5.Size = Vector3.new(2.01,2.01,1.01)
goldpart5.BrickColor = BrickColor.new("Gold")
goldpart5.Material = "Neon"
goldpart5.CanCollide = false
goldpart5.Anchored = false
goldpartweld5 = weldBetween(goldpart5,Torso)
 
 
Root.CFrame = Root.CFrame * CFrame.new(0,15,0) --intro
hum.HipHeight = 14.5
spinny = 0
for i = 1, 400 do
spinny = spinny + 4
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,math.rad(0+spinny),0),.4)
hum.HipHeight = hum.HipHeight - .025
swait()
end
local zamasuintro = Instance.new("Sound",Head)
zamasuintro.SoundId = "rbxassetid://2623121645"
zamasuintro.Volume = 7
zamasuintro:Play()
removeuseless:AddItem(zamasuintro,10)
for i = 1, 50 do
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(math.rad(0),math.rad(12),math.rad(-40 - 6 * math.sin(sine/12))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.4)
swait()
end
for i = 1, 50 do
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("Gold")
sk.Name = "sk"
sk.CFrame = Torso.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.01,.001,.01)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(.04,0,.04)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
coroutine.wrap(function()
local wshockwave = Instance.new("Part", Torso)
wshockwave.Size = Vector3.new(1,1,1)
wshockwave.CanCollide = false
wshockwave.Anchored = true
wshockwave.Transparency = .45
wshockwave.BrickColor = BrickColor.new("Gold")
wshockwave.CFrame = CFrame.new(Torso.Position) * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local wshockwavemesh = Instance.new("SpecialMesh", wshockwave)
wshockwavemesh.Scale = Vector3.new(1,.05,1)
wshockwavemesh.Name = "wswm"
wshockwavemesh.MeshId = "rbxassetid://20329976"
removeuseless:AddItem(wshockwave,2)
for i = 1, 20 do
wshockwavemesh.Scale = wshockwavemesh.Scale + Vector3.new(4,0,4)
wshockwave.Transparency = wshockwave.Transparency + .05
swait()
end
wshockwave:Remove()
end)()
coroutine.wrap(function()
goldpart.Anchored = true
goldpart.Size = goldpart.Size + Vector3.new(.5,.5,.5)
goldpart.Transparency = goldpart.Transparency + .05
goldpart2.Anchored = true
goldpart2.Size = goldpart2.Size + Vector3.new(.5,.5,.5)
goldpart2.Transparency = goldpart2.Transparency + .05
goldpart3.Anchored = true
goldpart3.Size = goldpart3.Size + Vector3.new(.5,.5,.5)
goldpart3.Transparency = goldpart3.Transparency + .035
goldpart4.Anchored = true
goldpart4.Size = goldpart4.Size + Vector3.new(.5,.5,.5)
goldpart4.Transparency = goldpart4.Transparency + .05
goldpart5.Anchored = true
goldpart5.Size = goldpart5.Size + Vector3.new(.5,.5,.5)
goldpart5.Transparency = goldpart5.Transparency + .05
end)()
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(math.rad(0),math.rad(12),math.rad(-40 - 6 * math.sin(sine/12))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.4)
swait()
end
coroutine.wrap(function()
goldpart:Remove()
goldpart2:Remove()
goldpart3:Remove()
goldpart4:Remove()
goldpart5:Remove()
end)()
coroutine.wrap(function()
o1 = Instance.new("ParticleEmitter",Head)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.0099999997764826,0.0099999997764826)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://243740013"
o1.ZOffset = 1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 75
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",Torso)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.0099999997764826,0.0099999997764826)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://243740013"
o1.ZOffset = 1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 75
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",RightArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.0099999997764826,0.0099999997764826)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://243740013"
o1.ZOffset = 1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 75
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",LeftArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.0099999997764826,0.0099999997764826)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://243740013"
o1.ZOffset = 1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 75
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",LeftLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.0099999997764826,0.0099999997764826)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://243740013"
o1.ZOffset = 1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 75
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",RightLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.0099999997764826,0.0099999997764826)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://243740013"
o1.ZOffset = 1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 75
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",Head)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -2
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
 
o1 = Instance.new("ParticleEmitter",RightArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -2
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
 
o1 = Instance.new("ParticleEmitter",LeftArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -2
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
 
o1 = Instance.new("ParticleEmitter",Torso)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -2
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
 
o1 = Instance.new("ParticleEmitter",RightLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -2
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
 
o1 = Instance.new("ParticleEmitter",LeftLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -2
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
o1.Color = ColorSequence.new(Color3.new(1, 1, 1),Color3.new(0, 0.666667, 1),Color3.new(0, 1, 0),Color3.new(1, 0, 1),Color3.new(1, 1, 1))
 
o1 = Instance.new("ParticleEmitter",Head)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.80000001192093,0.80000001192093)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -3
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",Torso)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.80000001192093,0.80000001192093)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -3
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",RightArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.80000001192093,0.80000001192093)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -3
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",LeftArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.80000001192093,0.80000001192093)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -3
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",RightLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.80000001192093,0.80000001192093)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -3
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",LeftLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.80000001192093,0.80000001192093)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -3
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",Head)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.60000002384186,0.60000002384186)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",Torso)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.60000002384186,0.60000002384186)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",RightArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.60000002384186,0.60000002384186)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",LeftArm)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.60000002384186,0.60000002384186)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",RightLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.60000002384186,0.60000002384186)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
 
o1 = Instance.new("ParticleEmitter",LeftLeg)
o1.Transparency = NumberSequence.new(1,0.70491802692413,0.7322404384613,1)
o1.Size = NumberSequence.new(0.60000002384186,0.60000002384186)
o1.LightEmission = 0.30000001192093
o1.Texture = "rbxassetid://242102147"
o1.ZOffset = -1
o1.Lifetime = NumberRange.new(2,2)
o1.Rate = 50
o1.RotSpeed = NumberRange.new(-100,100)
o1.Speed = NumberRange.new(0,0)
o1.VelocitySpread = 15
end)()
for i = 1, 50 do
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(math.rad(0),math.rad(12),math.rad(-40 - 6 * math.sin(sine/12))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.4)
swait()
end
for i = 1, 20 do
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = halo.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.5,.001,.5)
for i = 1, 10 do
skmesh.Scale = skmesh.Scale - Vector3.new(.05,0,.05)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
coroutine.wrap(function()
local wshockwave = Instance.new("Part", Torso)
wshockwave.Size = Vector3.new(1,1,1)
wshockwave.CanCollide = false
wshockwave.Anchored = true
wshockwave.Transparency = .45
wshockwave.BrickColor = BrickColor.new("White")
wshockwave.CFrame = CFrame.new(halo.Position) * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local wshockwavemesh = Instance.new("SpecialMesh", wshockwave)
wshockwavemesh.Scale = Vector3.new(50,.05,50)
wshockwavemesh.Name = "wswm"
wshockwavemesh.MeshId = "rbxassetid://20329976"
removeuseless:AddItem(wshockwave,2)
for i = 1, 20 do
wshockwavemesh.Scale = wshockwavemesh.Scale - Vector3.new(5,0.05,5)
wshockwave.Transparency = wshockwave.Transparency + .05
swait()
end
wshockwave:Remove()
end)()
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(math.rad(0),math.rad(12),math.rad(-40 - 6 * math.sin(sine/12))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
halomesh.Scale = halomesh.Scale - Vector3.new(.5,.5,.5)
halo.Transparency = halo.Transparency - .05
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.4)
swait()
end
 
 
mouse.KeyDown:connect(function(Press)
Press=Press:lower()
if Press=='e' then
if debounce then return end
debounce = true 
attacking = true
SOUND(Torso,1229838347,8,false,3)
g1 = Instance.new("BodyGyro", Root)
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(9000000,9000000,9000000)
ws = 8
sooht = Instance.new("Sound")
sooht.SoundId = "rbxassetid://1146688617"
sooht.Volume = 8
coroutine.wrap(function()
for i = 1, 5 do
haloweld.C0 = haloweld.C0 * CFrame.new(0,-1,0)
halomesh.Scale = halomesh.Scale + Vector3.new(.25,.25,.25)
swait()
end
end)()
coroutine.wrap(function()
for i = 1, 15 do
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(5 * math.sin(sine/12)),math.rad(-40),math.rad(0)),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(.5,2,0) * CFrame.Angles(math.rad(0),math.rad(20),math.rad(-140)),.3)
swait()
end
for i = 1, 20 do
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(5 * math.sin(sine/12)),math.rad(-0 * math.sin(sine/12)),math.rad(0)),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1, 1.35, 0.4) * CFrame.Angles(math.rad(-90 - 2 * math.sin(sine/12)), math.rad(3), math.rad(4)), 0.4)
swait()
end
end)()
for i = 1, 30 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-9.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.2)
local bladeofjustice = Instance.new("Part",Torso)
bladeofjustice.Anchored = true
bladeofjustice.CanCollide = false
bladeofjustice.Name = "blad"
bladeofjustice.Transparency = 1
bladeofjustice.Size = Vector3.new(1,1,1)
bladeofjustice.BrickColor = BrickColor.new("Really red")
bladeofjustice.Material = "Neon"
bladeofjustice.CFrame = Root.CFrame * CFrame.new(math.random(-8,8),math.random(-5,5),math.random(-2,2))
local bladeofjusticemesh = Instance.new("SpecialMesh",bladeofjustice)
bladeofjusticemesh.MeshId = "rbxassetid://2624209310"
bladeofjusticemesh.Scale = Vector3.new(1,1,1)
coroutine.wrap(function()
local hitted = false
for i = 1, 20 do
bladeofjustice.Transparency = bladeofjustice.Transparency - .05
swait()
end
bladeofjustice.Anchored = false
sooht.Parent = bladeofjustice
sooht:Play()
coroutine.wrap(function()
for i = 1, 300 do
if hitted then break end
swait()
end
if not hitted then
bladeofjustice:Remove()
end
end)()
local bov = Instance.new("BodyVelocity",bladeofjustice)
bov.maxForce = Vector3.new(99999,99999,99999)
bladeofjustice.CFrame = CFrame.new(bladeofjustice.Position,mouse.Hit.p) 
bov.velocity = bladeofjustice.CFrame.lookVector*220
bladeofjustice.Touched:connect(function(hit)
if hit:IsA("Part") and hit.Parent ~= Character and hit.Name ~= "blad" and hit.Parent.Parent ~= Character then
if hitted then return end
hitted = true
bov:Remove()
bladeofjustice.Anchored = true
wait(2)
bladeofjustice.Transparency = 1
Hit = damagealll(14,bladeofjustice.Position)
for _,v in pairs(Hit) do
if v:FindFirstChildOfClass("Humanoid") and v:FindFirstChildOfClass("Humanoid").Health > 0 then
slachtoffer = v:FindFirstChildOfClass("Humanoid")
slachtoffer:TakeDamage(math.random(29,43))
vel = Instance.new("BodyVelocity",v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")) 
vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
torso = v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")
vel.velocity = CFrame.new(bladeofjustice.Position,torso.Position).lookVector*125
removeuseless:AddItem(vel,.1)
end
end
for i = 1, 3 do
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = bladeofjustice.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.01,.001,.01)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(.03,0,.03)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
coroutine.wrap(function()
local wshockwave = Instance.new("Part", Torso)
wshockwave.Size = Vector3.new(1,1,1)
wshockwave.CanCollide = false
wshockwave.Anchored = true
wshockwave.Transparency = .45
wshockwave.BrickColor = BrickColor.new("White")
wshockwave.CFrame = CFrame.new(bladeofjustice.Position) * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local wshockwavemesh = Instance.new("SpecialMesh", wshockwave)
wshockwavemesh.Scale = Vector3.new(.1,.005,.1)
wshockwavemesh.Name = "wswm"
wshockwavemesh.MeshId = "rbxassetid://20329976"
removeuseless:AddItem(wshockwave,2)
for i = 1, 20 do
wshockwavemesh.Scale = wshockwavemesh.Scale + Vector3.new(5.5,0,5.5)
wshockwave.Transparency = wshockwave.Transparency + .05
swait()
end
wshockwave:Remove()
end)()
coroutine.wrap(function()
local exploshap = Instance.new("Part",Torso)
exploshap.Size = Vector3.new(1,1,1)
exploshap.Shape = "Ball"
exploshap.Material = "Neon"
exploshap.CFrame = bladeofjustice.CFrame
exploshap.BrickColor = BrickColor.new("Really red")
exploshap.CanCollide = false
exploshap.Anchored = true
for i = 1, 20 do
exploshap.Size = exploshap.Size + Vector3.new(2,2,2)
exploshap.Transparency = exploshap.Transparency + .05
swait()
end
bladeofjustice:Remove()
exploshap:Remove()
end)()
swait()
end
end
end)
end)()
swait(.5)
end
for i = 1, 5 do
haloweld.C0 = haloweld.C0 * CFrame.new(0,1,0)
halomesh.Scale = halomesh.Scale - Vector3.new(.25,.25,.25)
swait()
end
removeuseless:AddItem(g1,.001)
ws = 90
debounce = false
attacking = false
elseif Press=='t' then
if dedlaff then return end
if tauntdebounce == true then return end
tauntdebounce = true
rdnm = soundtable[math.random(1,#soundtable)]
tauntsound = Instance.new("Sound", Head)
tauntsound.Volume = 10
tauntsound.SoundId = "http://www.roblox.com/asset/?id="..rdnm
tauntsound.Looped = false
tauntsound:Play()
wait(3)
wait(tauntsound.TimeLength)
tauntsound:Remove()
wait(1)
tauntdebounce = false
elseif Press=='u' then
if debounce then return end
debounce = true
attacking = true
g1 = Instance.new("BodyGyro", Root)
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(0,9000000,0)
ws = 0
local FACEMYDIVINEWRATH = Instance.new("Sound",Torso)
FACEMYDIVINEWRATH.SoundId = "rbxassetid://2638717446"
FACEMYDIVINEWRATH.Volume = 10
FACEMYDIVINEWRATH:Play()
removeuseless:AddItem(FACEMYDIVINEWRATH,5)
for i = 1, 20 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),math.rad(10),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.2, 1.5, .5) * CFrame.Angles(math.rad(-85 - 3 * math.sin(sine/12)), math.rad(40 + 5 * math.sin(sine/12)), math.rad(0)), 0.25)
swait()
end
local holywrath = Instance.new("Part",RightArm)
SOUND(holywrath,2644268083,10,false,6)
holywrath.Size = Vector3.new(.1,.1,.1)
holywrath.CanCollide = false
holywrath.Anchored = true
holywrath.BrickColor = BrickColor.new("Bright orange")
holywrath.Material = "Neon"
holywrath.Shape = "Ball"
holywrath.CFrame = rightlocation.CFrame * CFrame.new(0,0,-2)
local holywrathaura = Instance.new("Sound",holywrath)
holywrathaura.SoundId = "rbxassetid://2643712818"
holywrathaura.Looped = true
holywrathaura.Volume = 0
holywrathaura:Play()
local holywrath2 = Instance.new("Part",RightArm)
holywrath2.Size = Vector3.new(.3,.3,.3)
holywrath2.CanCollide = false
holywrath2.Anchored = true
holywrath2.Transparency = .7
holywrath2.BrickColor = BrickColor.new("Really red")
holywrath2.Material = "Neon"
holywrath2.Shape = "Ball"
holywrath2.CFrame = rightlocation.CFrame * CFrame.new(0,0,-2)
for i = 1, 30 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.2)
coroutine.wrap(function()
hwc = holywrathcolors[math.random(1,#holywrathcolors)]
local energyballs = Instance.new("Part",Torso)
energyballs.BrickColor = BrickColor.new(hwc)
energyballs.Anchored = true
energyballs.CanCollide = false
energyballs.CFrame = holywrath.CFrame * CFrame.new(math.random(-4,4),math.random(-4,4),math.random(-4,4))
energyballs.Shape = "Ball"
energyballs.Material = "Neon"
energyballs.Size = Vector3.new(.4,.4,.4)
for i = 1, 10 do
energyballs.CFrame = energyballs.CFrame:lerp(CFrame.new(holywrath.Position),.3)
swait()
end
energyballs:Remove()
end)()
end
for i = 1, 20 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
holywrath2.CFrame = rightlocation.CFrame * CFrame.new(0,0,-2)
holywrath2.Size = holywrath2.Size + Vector3.new(.1,.1,.1)
holywrath.CFrame = rightlocation.CFrame * CFrame.new(0,0,-2)
holywrath.Size = holywrath.Size + Vector3.new(.1,.1,.1)
swait()
end
for i = 1, 10 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
holywrath2.CFrame = rightlocation.CFrame * CFrame.new(0,0,-2)
holywrath.CFrame = rightlocation.CFrame * CFrame.new(0,0,-2)
swait()
end
enbig = 0
enbig2 = 0
enbigger = .25
SOUND(holywrath,2644340882,10,false,6)
for i = 1, 60 do
enbigger = enbigger + .02
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = holywrath.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.05,.005,.05)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(enbigger,0,enbigger)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
holywrathaura.Volume = holywrathaura.Volume + .2
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.2)
enbig = enbig + 2
enbig2 = enbig2 + 1
holywrath.Size = holywrath.Size + Vector3.new(4,4,4)
holywrath2.Size = holywrath2.Size + Vector3.new(4,4,4)
holywrath2.CFrame = rightlocation.CFrame * CFrame.new(0,-5 - enbig,-5 - enbig2)
holywrath.CFrame = rightlocation.CFrame * CFrame.new(0,-5 - enbig,-5 - enbig2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),math.rad(-40),math.rad(0)),.3)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(1.22, 1.32, .4) * CFrame.Angles(math.rad(40 + 1 * math.sin(sine/5)), math.rad(3 + 1 * math.sin(sine/4)), math.rad(-160 - 2 * math.sin(sine/9))), 0.25)
swait()
end
for i = 1, 30 do
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(.98,-.15,.5) * CFrame.Angles(math.rad(-70 - 5 * math.sin(sine/12)),math.rad(40 - 5 * math.sin(sine/12)),math.rad(-20)),.25)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(25),math.rad(-50),math.rad(0)),.3)
swait()
end
local hitboxwrath = Instance.new("Part",Torso)
hitboxwrath.Size = Vector3.new(1,1,1)
hitboxwrath.CanCollide = false
hitboxwrath.Transparency = 1
hitboxwrath.Anchored = false
hitboxwrath.Name = "hb"
hitboxwrath.CFrame = holywrath.CFrame
local bov = Instance.new("BodyVelocity",hitboxwrath)
bov.maxForce = Vector3.new(99999,99999,99999)
holywrath.CFrame = CFrame.new(holywrath.Position,mouse.Hit.p) 
bov.velocity = holywrath.CFrame.lookVector*60
local hitted = false
local function explo()
hitted = true
hitboxwrath.Anchored = true
SOUND(hitboxwrath,2011915907,10,false,6)
shock = holywrath:Clone() shock.Parent = Torso
coroutine.wrap(function()
for i = 1, 20 do
shock.Size = shock.Size + Vector3.new(5,5,5)
shock.Transparency = shock.Transparency + .05
swait()
end
shock:Remove()
end)()
local taks = 0
local wavebigger = true
coroutine.wrap(function()
local deadlyring = Instance.new("Part", Torso)
deadlyring.Size = Vector3.new(5, 5, 5)
deadlyring.Transparency = .5
deadlyring.BrickColor = BrickColor.new("White")
deadlyring.Anchored = true
deadlyring.CanCollide = false
deadlyring.CFrame = hitboxwrath.CFrame * CFrame.Angles(math.rad(math.random(-180,180)), math.rad(math.random(-180,180)), math.rad(math.random(-180,180)))
local deadlyringh = Instance.new("SpecialMesh", deadlyring) 
deadlyringh.MeshId = "http://www.roblox.com/asset/?id=3270017" 
deadlyringh.Scale = Vector3.new(330, 330, .1)
local deadlyring2 = Instance.new("Part", Torso)
deadlyring2.Size = Vector3.new(5, 5, 5)
deadlyring2.Transparency = .5
deadlyring2.BrickColor = BrickColor.new("White")
deadlyring2.Anchored = true
deadlyring2.CanCollide = false
deadlyring2.CFrame = hitboxwrath.CFrame * CFrame.Angles(math.rad(math.random(-180,180)), math.rad(math.random(-180,180)), math.rad(math.random(-180,180)))
local deadlyringh2 = Instance.new("SpecialMesh", deadlyring2) 
deadlyringh2.MeshId = "http://www.roblox.com/asset/?id=3270017" 
deadlyringh2.Scale = Vector3.new(360, 360, .1)
while wavebigger do
Hit = damagealll(187,hitboxwrath.Position)
for _,v in pairs(Hit) do
if v:FindFirstChildOfClass("Humanoid") and v:FindFirstChildOfClass("Humanoid").Health > 0 then
slachtoffer = v:FindFirstChildOfClass("Humanoid")
slachtoffer:TakeDamage(math.random(3,7))
vel = Instance.new("BodyVelocity",v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")) 
vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
torso = v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")
vel.velocity = CFrame.new(hitboxwrath.Position,torso.Position).lookVector*330
removeuseless:AddItem(vel,.1)
end
end
deadlyring.CFrame = deadlyring.CFrame * CFrame.Angles(math.rad(0+7),math.rad(0-7),math.rad(0+7))
deadlyring2.CFrame = deadlyring2.CFrame * CFrame.Angles(math.rad(0-7),math.rad(0+7),math.rad(0-7))
deadlyringh2.Scale = deadlyringh2.Scale + Vector3.new(2,2,0)
deadlyringh.Scale = deadlyringh.Scale + Vector3.new(2,2,0)
holywrath2.Size = holywrath2.Size + Vector3.new(.25,.25,.25)
holywrath.Size = holywrath.Size + Vector3.new(.25,.25,.25)
swait()
end
for i = 1, 50 do
holywrathaura.Volume = holywrathaura.Volume - .5
deadlyringh.Scale = deadlyringh.Scale + Vector3.new(5,5,0)
deadlyringh2.Scale = deadlyringh2.Scale + Vector3.new(5,5,0)
deadlyring.Transparency = deadlyring.Transparency + .025
deadlyring2.Transparency = deadlyring2.Transparency + .025
holywrath.Transparency = holywrath.Transparency + .025
holywrath2.Transparency = holywrath2.Transparency + .025
swait()
end
holywrathaura:Remove()
hitboxwrath:Remove()
holywrath:Remove()
holywrath2:Remove()
deadlyring:Remove()
deadlyring2:Remove()
end)()
for i = 1, 150 do
taks = taks + .1
coroutine.wrap(function()
local shockwave = Instance.new("Part", Torso)
shockwave.Size = Vector3.new(1,1,1)
shockwave.CanCollide = false
shockwave.Anchored = true
shockwave.Transparency = .5
shockwave.BrickColor = BrickColor.new("White")
shockwave.CFrame = CFrame.new(hitboxwrath.Position)
local shockwavemesh = Instance.new("SpecialMesh", shockwave)
shockwavemesh.Scale = Vector3.new(7,3,7)
shockwavemesh.MeshId = "rbxassetid://20329976"
local shockwave2 = Instance.new("Part", Torso)
shockwave2.Size = Vector3.new(1,1,1)
shockwave2.CanCollide = false
shockwave2.Anchored = true
shockwave2.Transparency = .5
shockwave2.BrickColor = BrickColor.new("White")
shockwave2.CFrame = CFrame.new(hitboxwrath.Position)
local shockwavemesh2 = Instance.new("SpecialMesh", shockwave2)
shockwavemesh2.Scale = Vector3.new(5,3,5)
shockwavemesh2.MeshId = "rbxassetid://20329976"
for i = 1, 40 do
shockwave.CFrame = shockwave.CFrame * CFrame.Angles(math.rad(0),math.rad(0+15),0)
shockwave2.CFrame = shockwave2.CFrame * CFrame.Angles(math.rad(0),math.rad(0-8),0)
shockwave.Transparency = shockwave.Transparency + 0.025
shockwave2.Transparency = shockwave2.Transparency + 0.025
shockwavemesh2.Scale = shockwavemesh2.Scale + Vector3.new(18 + taks,6 + taks/2,18 + taks)
shockwavemesh.Scale = shockwavemesh.Scale + Vector3.new(18+taks,3 + taks/2,18+taks)
swait()
end
shockwave:Remove()
shockwave2:Remove()
end)()
swait(2.4)
end
wavebigger = false
end
coroutine.wrap(function()
local hitted = false
hitboxwrath.Touched:connect(function(hit)
if hit:IsA("Part") and hit.Parent ~= Character and hit.Name ~= "blad" and hit.Parent.Parent ~= Character then
if hitted then return end
explo()
end
end)
while true do
if hitted then break end
holywrath2.CFrame = hitboxwrath.CFrame
holywrath.CFrame = hitboxwrath.CFrame
swait()
end
end)()
coroutine.wrap(function()
for i = 1, 1100 do
if hitted then break end
swait()
end
if not hitted then
explo()
end
end)()
for i = 1, 22 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.2)
RIGHTARMLERP.C1 = RIGHTARMLERP.C1:lerp(CFrame.new(.2,.2,.2) * CFrame.Angles(0,0,0),.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1, 1.1, 0.4) * CFrame.Angles(math.rad(-75), math.rad(-15), math.rad(4)), 0.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(-25),math.rad(50),math.rad(0)),.3)
swait()
end
RIGHTARMLERP.C1 = CFrame.new(0,0,0)
removeuseless:AddItem(g1,.001)
debounce = false
attacking = false
ws = 90
elseif Press=='y' then
if debounce then return end
debounce = true
attacking = true
local trev = true
change = .6
coroutine.wrap(function()
while true do
if trev == false then break end
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(5 * math.sin(sine/12)),math.rad(-0 * math.sin(sine/12)),math.rad(0)),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
swait()
end
end)()
ws = 0
local speech = Instance.new("Sound",Head)
speech.SoundId = "rbxassetid://2638520204"
speech.Volume = 10
speech:Play()
removeuseless:AddItem(speech,5)
coroutine.wrap(function()
for i = 1, 35 do
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(0.4, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(100)), 0.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-0.4, 2, 0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(-100)), 0.25)
swait()
end
end)()
coroutine.wrap(function()
local blwav = Instance.new("Part",Torso)
blwav.Size = Vector3.new(1,1,1)
blwav.Shape = "Ball"
blwav.BrickColor = BrickColor.new("Dark blue")
blwav.CanCollide = false
blwav.CFrame = Root.CFrame
blwav.Anchored = true
blwav.Material = "Neon"
for i = 1, 50 do
blwav.Size = blwav.Size + Vector3.new(4,4,4)
blwav.Transparency = blwav.Transparency + .05
swait()
end
blwav:Remove()
end)()
eagle = Instance.new("Part", Torso)
eagle.Size = Vector3.new(1,1,1)
eagle.CanCollide = false
eagle.Anchored = false
eagle.Material = "Neon"
eagle.Transparency = .58
eagle.BrickColor = BrickColor.new("Dark blue")
eagle.CFrame = CFrame.new(halo.Position) * CFrame.new(0,115,0) * CFrame.Angles(math.rad(90),0,0)
local eaglemesh = Instance.new("SpecialMesh", eagle)
eaglemesh.MeshId = "rbxassetid://120647529"
eaglemesh.Scale = Vector3.new(0,0,0)
eagleweld = weldBetween(eagle,Root)
eagleweld.C0 = CFrame.new(0,0,105) * CFrame.Angles(math.rad(-90),0,0)
local eagle2 = Instance.new("Part", Torso)
eagle2.Size = Vector3.new(1,1,1)
eagle2.CanCollide = false
eagle2.Anchored = false
eagle2.Material = "Neon"
eagle2.Transparency = .49
eagle2.BrickColor = BrickColor.new("Pastel violet")
eagle2.CFrame = CFrame.new(halo.Position) * CFrame.new(0,115,0) * CFrame.Angles(math.rad(90),0,0)
local eaglemesh2 = Instance.new("SpecialMesh", eagle2)
eaglemesh2.MeshId = "rbxassetid://120647529"
eaglemesh2.Scale = Vector3.new(0,0,0)
eagleweld2 = weldBetween(eagle2,Root)
eagleweld2.C0 = CFrame.new(0,0,105) * CFrame.Angles(math.rad(-90),0,0)
local eagle3 = Instance.new("Part", Torso)
eagle3.Size = Vector3.new(1,1,1)
eagle3.CanCollide = false
eagle3.Anchored = false
eagle3.Material = "Neon"
eagle3.Transparency = .65
eagle3.BrickColor = BrickColor.new("Mulberry")
eagle3.CFrame = CFrame.new(halo.Position) * CFrame.new(0,115,0) * CFrame.Angles(math.rad(90),0,0)
local eaglemesh3 = Instance.new("SpecialMesh", eagle3)
eaglemesh3.MeshId = "rbxassetid://120647529"
eaglemesh3.Scale = Vector3.new(0,0,0)
eagleweld3 = weldBetween(eagle3,Root)
eagleweld3.C0 = CFrame.new(0,0,105) * CFrame.Angles(math.rad(-90),0,0)
circlelocation = Instance.new("Part",Torso)
circlelocation.Size = Vector3.new(1,1,1)
circlelocation.CFrame = Root.CFrame
circlelocation.Anchored = false
circlelocation.Transparency = 1
circlelocation.CanCollide = false
circlelocationweld = weldBetween(circlelocation,Root)
circlelocationweld.C0 = CFrame.new(0,-56,-15)
lighttable = {}
val = 0
for i = 1, 250 do
val = val + 5
lightpart = Instance.new("Part",Torso)
lightpart.Anchored = false
lightpart.CanCollide = false
lightpart.Size = Vector3.new(2,.5,2.35)
lightpart.Material = "Neon"
lightpart.Transparency = 1
lightpart.BrickColor = BrickColor.new("Gold")
lightpartweld = weldBetween(lightpart,circlelocation)
lightpartweld.C0 = CFrame.new(25,0,0) * CFrame.Angles(0,math.rad(val),0)
table.insert(lighttable,lightpart)
end
coroutine.wrap(function()
wait(1.76)
for i = 1, 120 do
for i,v in pairs(lighttable) do
v.Transparency = v.Transparency - .01
end
swait()
end
end)()
introvog = true
coroutine.wrap(function()
for i = 1, 63 do
eaglemesh3.Scale = eaglemesh3.Scale + Vector3.new(0,1,1)
swait()
end
for i = 1, 32 do
eaglemesh3.Scale = eaglemesh3.Scale + Vector3.new(2,0,0)
swait()
end
for i = 1, 50 do
hum.CameraOffset = Vector3.new(math.random(-2,2),math.random(-2,2),math.random(-2,2))
coroutine.wrap(function()
local wshockwave = Instance.new("Part", Torso)
wshockwave.Size = Vector3.new(1,1,1)
wshockwave.CanCollide = false
wshockwave.Anchored = true
wshockwave.Transparency = .45
wshockwave.BrickColor = BrickColor.new("White")
wshockwave.CFrame = CFrame.new(eagle.Position) * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local wshockwavemesh = Instance.new("SpecialMesh", wshockwave)
wshockwavemesh.Scale = Vector3.new(1,.005,1)
wshockwavemesh.Name = "wswm"
wshockwavemesh.MeshId = "rbxassetid://20329976"
removeuseless:AddItem(wshockwave,2)
for i = 1, 20 do
wshockwavemesh.Scale = wshockwavemesh.Scale + Vector3.new(29.5,0,29.5)
wshockwave.Transparency = wshockwave.Transparency + .05
swait()
end
wshockwave:Remove()
end)()
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = eagle.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.05,.005,.05)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(.25,0,.25)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
swait()
end
introvog = false
hum.CameraOffset = Vector3.new(0,0,0)
end)()
coroutine.wrap(function()
for i = 1, 54 do
eaglemesh2.Scale = eaglemesh2.Scale + Vector3.new(0,1,1)
swait()
end
local eaglesound = Instance.new("Sound",eagle)
eaglesound.SoundId = "rbxassetid://923172614"
eaglesound.Volume = 10
eaglesound:Play()
removeuseless:AddItem(eaglesound,5)
for i = 1, 27 do
eaglemesh2.Scale = eaglemesh2.Scale + Vector3.new(2,0,0)
swait()
end
end)()
coroutine.wrap(function()
for i = 1, 59 do
eaglemesh.Scale = eaglemesh.Scale + Vector3.new(0,1,1)
swait()
end
for i = 1, 30 do
eaglemesh.Scale = eaglemesh.Scale + Vector3.new(2,0,0)
swait()
end
end)()
while wait() do
if introvog == false then break end
end
bleedattacking = true
g1 = Instance.new("BodyGyro", Root)
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(0,9000000,0)
coroutine.wrap(function()
while bleedattacking do
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,mouse.Hit.p),.155)
swait()
end
removeuseless:AddItem(g1,.001)
end)()
coroutine.wrap(function()
local lnt = Instance.new("Sound",eagle)
lnt.SoundId = "rbxassetid://224339201"
lnt.Volume = 10
lnt:Play()
removeuseless:AddItem(lnt,5)
wait(.3)
local lnt2 = Instance.new("Sound",eagle)
lnt2.SoundId = "rbxassetid://1539349118"
lnt2.Volume = 10
lnt2:Play()
removeuseless:AddItem(lnt2,5)
end)()
for i = 1, 10 do
local bladeofjustice = Instance.new("Part",Torso)
bladeofjustice.Anchored = true
bladeofjustice.CanCollide = false
bladeofjustice.Name = "blad"
bladeofjustice.Transparency = 1
bladeofjustice.Size = Vector3.new(2,2,2)
bladeofjustice.BrickColor = BrickColor.new("Pastel violet")
bladeofjustice.Material = "Neon"
bladeofjustice.CFrame = eagle.CFrame * CFrame.new(math.random(-139,139),math.random(-39,39),math.random(-15,15))
local bladeofjusticemesh = Instance.new("SpecialMesh",bladeofjustice)
bladeofjusticemesh.MeshId = "rbxassetid://2624209310"
bladeofjusticemesh.Scale = Vector3.new(10,10,10)
local particlecolor = ColorSequence.new(Color3.new(255, 255, 255))
local blwav = Instance.new("Part",Torso)
blwav.Size = Vector3.new(1,1,1)
blwav.Shape = "Ball"
blwav.BrickColor = BrickColor.new("Dark blue")
blwav.CanCollide = false
blwav.CFrame = bladeofjustice.CFrame
blwav.Anchored = true
blwav.Material = "Neon"
blwav.Size = blwav.Size + Vector3.new(4,4,4)
blwav.Transparency = blwav.Transparency + .05
coroutine.wrap(function()
for i = 1, 5 do
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = bladeofjustice.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.05,.005,.05)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(.05,0,.05)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end
end)()
coroutine.wrap(function()
for i = 1, 20 do
blwav.Size = blwav.Size + Vector3.new(10,10,10)
blwav.Transparency = blwav.Transparency + .05
bladeofjustice.Transparency = bladeofjustice.Transparency - .05
swait()
end
blwav:Remove()
end)()
local hitted = false
coroutine.wrap(function()
for i = 1, 300 do
if hitted then break end
swait()
end
if not hitted then
bladeofjustice:Remove()
end
end)()
bladeofjustice.Anchored = false
local bov = Instance.new("BodyVelocity",bladeofjustice)
bov.maxForce = Vector3.new(9999999,9999999,9999999)
bladeofjustice.CFrame = CFrame.new(bladeofjustice.Position,mouse.Hit.p) 
bov.velocity = bladeofjustice.CFrame.lookVector*350
bladeofjustice.Touched:connect(function(hit)
if hit:IsA("Part") and hit.Parent ~= Character and hit.Name ~= "blad" and hit.Parent.Parent ~= Character then
if hitted then return end
hitted = true
bov:Remove()
bladeofjustice.Anchored = true
wait(2)
removeuseless:AddItem(bladeofjustice,5)
coroutine.wrap(function()
for i = 1, 20 do
hum.CameraOffset = Vector3.new(math.random(-3,3),math.random(-3,3),math.random(-3,3))
swait()
end
hum.CameraOffset = Vector3.new(0,0,0)
end)()
Hit = damagealll(144,bladeofjustice.Position)
for _,v in pairs(Hit) do
if v:FindFirstChildOfClass("Humanoid") and v:FindFirstChildOfClass("Humanoid").Health > 0 then
slachtoffer = v:FindFirstChildOfClass("Humanoid")
slachtoffer:TakeDamage(math.random(47,78))
vel = Instance.new("BodyVelocity",v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")) 
vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
torso = v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")
vel.velocity = CFrame.new(bladeofjustice.Position,torso.Position).lookVector*330
removeuseless:AddItem(vel,.1)
end
end
local soundbox = Instance.new("Part",Torso)
soundbox.CFrame = bladeofjustice.CFrame
soundbox.Size = Vector3.new(1,1,1)
soundbox.Anchored = true
soundbox.CanCollide = false
soundbox.Transparency = 1
removeuseless:AddItem(soundbox,5)
wabam = Instance.new("Sound",soundbox)
wabam.SoundId = "rbxassetid://2444802791"
wabam.Volume = 8
wabam:Play()
bladeofjustice.Transparency = 1
pobox = Instance.new("Part",Torso)
pobox.Anchored = true
pobox.CanCollide = false
pobox.Size = Vector3.new(1,1,1)
pobox.CFrame = bladeofjustice.CFrame
pobox.Transparency = 1
for i = 1, 4 do
coroutine.wrap(function()
local shockwave = Instance.new("Part", Torso)
shockwave.Size = Vector3.new(1,1,1)
shockwave.CanCollide = false
shockwave.Anchored = true
shockwave.Transparency = .5
shockwave.BrickColor = BrickColor.new("White")
shockwave.CFrame = CFrame.new(pobox.Position)
local shockwavemesh = Instance.new("SpecialMesh", shockwave)
shockwavemesh.Scale = Vector3.new(7,3,7)
shockwavemesh.MeshId = "rbxassetid://20329976"
local shockwave2 = Instance.new("Part", Torso)
shockwave2.Size = Vector3.new(1,1,1)
shockwave2.CanCollide = false
shockwave2.Anchored = true
shockwave2.Transparency = .5
shockwave2.BrickColor = BrickColor.new("White")
shockwave2.CFrame = CFrame.new(pobox.Position)
local shockwavemesh2 = Instance.new("SpecialMesh", shockwave2)
shockwavemesh2.Scale = Vector3.new(5,3,5)
shockwavemesh2.MeshId = "rbxassetid://20329976"
for i = 1, 40 do
shockwave.CFrame = shockwave.CFrame * CFrame.Angles(math.rad(0),math.rad(0+15),0)
shockwave2.CFrame = shockwave2.CFrame * CFrame.Angles(math.rad(0),math.rad(0-8),0)
shockwave.Transparency = shockwave.Transparency + 0.025
shockwave2.Transparency = shockwave2.Transparency + 0.025
shockwavemesh2.Scale = shockwavemesh2.Scale + Vector3.new(18,6,18)
shockwavemesh.Scale = shockwavemesh.Scale + Vector3.new(18,3,18)
swait()
end
pobox:Remove()
shockwave:Remove()
shockwave2:Remove()
bladeofjustice:Remove()
end)()
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = bladeofjustice.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.06,.001,.06)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(.13,0,.13)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
coroutine.wrap(function()
local wshockwave = Instance.new("Part", Torso)
wshockwave.Size = Vector3.new(1,1,1)
wshockwave.CanCollide = false
wshockwave.Anchored = true
wshockwave.Transparency = .45
wshockwave.BrickColor = BrickColor.new("White")
wshockwave.CFrame = CFrame.new(bladeofjustice.Position) * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local wshockwavemesh = Instance.new("SpecialMesh", wshockwave)
wshockwavemesh.Scale = Vector3.new(10,.05,10)
wshockwavemesh.Name = "wswm"
wshockwavemesh.MeshId = "rbxassetid://20329976"
for i = 1, 20 do
wshockwavemesh.Scale = wshockwavemesh.Scale + Vector3.new(30,0,30)
wshockwave.Transparency = wshockwave.Transparency + .05
swait()
end
wshockwave:Remove()
end)()
coroutine.wrap(function()
local blwav = Instance.new("Part",Torso)
blwav.Size = Vector3.new(1,1,1)
blwav.Shape = "Ball"
blwav.BrickColor = BrickColor.new("Dark blue")
blwav.CanCollide = false
blwav.CFrame = bladeofjustice.CFrame
blwav.Anchored = true
blwav.Material = "Neon"
for i = 1, 20 do
blwav.Size = blwav.Size + Vector3.new(18,18,18)
blwav.Transparency = blwav.Transparency + .05
swait()
end
blwav:Remove()
end)()
swait()
end
end
end)
swait(10)
end
bleedattacking = false
eagleweld:Remove()
eagleweld2:Remove()
eagleweld3:Remove()
eagle.Anchored = true
eagle2.Anchored = true
eagle3.Anchored = true
coroutine.wrap(function()
for i = 1, 30 do
for i,v in pairs(lighttable) do
v.Transparency = v.Transparency + .05
end
swait()
end
for i,v in pairs(lighttable) do
v:Remove()
end
circlelocation:Remove()
lighttable = {}
end)()
for i = 1, 80 do
eagle.CFrame = eagle.CFrame * CFrame.new(0,0,-6) * CFrame.Angles(0,math.rad(0),math.rad(7))
eagle.Transparency = eagle.Transparency + .0125
eagle2.CFrame = eagle2.CFrame * CFrame.new(0,0,-4) * CFrame.Angles(0,math.rad(0),math.rad(-7))
eagle2.Transparency = eagle2.Transparency + .0125
eagle3.CFrame = eagle3.CFrame * CFrame.new(0,0,-3) * CFrame.Angles(0,math.rad(0),math.rad(7))
eagle3.Transparency = eagle3.Transparency + .0125
swait()
end
eagle:Remove()
eagle2:Remove()
eagle3:Remove()
ws = 90
trev = false
debounce = false
attacking = false
elseif Press=='r' then
if debounce then return end
debounce = true
attacking = true
ws = 8
coroutine.wrap(function()
g1 = Instance.new("BodyGyro", Root)
g1.D = 175
g1.P = 20000
g1.MaxTorque = Vector3.new(0,9000000,0)
for i = 1, 50 do
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(5 * math.sin(sine/12)),math.rad(-0 * math.sin(sine/12)),math.rad(0)),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(.5,2,0) * CFrame.Angles(math.rad(0),math.rad(20),math.rad(-140)),.3)
swait()
end
removeuseless:AddItem(g1,.001)
debounce = false
attacking = false
ws = 90
end)()
local lightofdeath = Instance.new("Part",Torso)
angelic = Instance.new("Sound",lightofdeath)
angelic.Pitch = 1
angelic.Volume = 10
angelic.SoundId = "rbxassetid://1837929946"
angelic:Play()
lightofdeath.Size = Vector3.new(1000000,25,25)
lightofdeath.CanCollide = false
lightofdeath.Material = "Neon"
lightofdeath.CFrame = CFrame.new(mouse.Hit.p) * CFrame.Angles(math.rad(0),math.rad(90),math.rad(90))
lightofdeath.Shape = "Cylinder"
lightofdeath.Transparency = 1
lightofdeath.Anchored = true
local lightofdeath2 = Instance.new("Part",Torso)
lightofdeath2.Size = Vector3.new(1000000,50,50)
lightofdeath2.CanCollide = false
lightofdeath2.Material = "Neon"
lightofdeath2.CFrame = CFrame.new(lightofdeath.Position) * CFrame.Angles(math.rad(0),math.rad(90),math.rad(90))
lightofdeath2.Shape = "Cylinder"
lightofdeath2.Transparency = 1
lightofdeath2.CanCollide = false
lightofdeath2.Anchored = true
local pobox = Instance.new("Part",Torso)
pobox.Size = Vector3.new(1,1,1)
pobox.Transparency = 1
pobox.Anchored = true
pobox.CanCollide = false
pobox.CFrame = CFrame.new(mouse.Hit.p)
coroutine.wrap(function()
for i = 1, 20 do
g1.CFrame = g1.CFrame:lerp(CFrame.new(Root.Position,lightofdeath.Position),.4)
lightofdeath.Transparency = lightofdeath.Transparency - .025
lightofdeath2.Transparency = lightofdeath2.Transparency - .0125
swait()
end
end)()
for i = 1, 100 do
lightofdeath.Size = lightofdeath.Size - Vector3.new(0,.25,.25)
lightofdeath2.Size = lightofdeath2.Size - Vector3.new(0,.5,.5)
swait()
end
local soundbrick = Instance.new("Part",Torso)
soundbrick.Anchored = true
soundbrick.Size = Vector3.new(1,1,1)
soundbrick.CanCollide = false
soundbrick.Transparency = 1
soundbrick.CFrame = pobox.CFrame
removeuseless:AddItem(soundbrick,10)
local bam = Instance.new("Sound",soundbrick)
bam.SoundId = "rbxassetid://1354014962"
bam.Volume = 10
bam:Play()
Hit = damagealll(44,pobox.Position)
for _,v in pairs(Hit) do
if v:FindFirstChildOfClass("Humanoid") and v:FindFirstChildOfClass("Humanoid").Health > 0 then
slachtoffer = v:FindFirstChildOfClass("Humanoid")
slachtoffer:TakeDamage(math.random(42,68))
vel = Instance.new("BodyVelocity",v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")) 
vel.maxForce = Vector3.new(9999999999999,9999999999999,9999999999999)
torso = v:FindFirstChild("Torso") or v:FindFirstChild("UpperTorso")
vel.velocity = CFrame.new(pobox.Position,torso.Position).lookVector*225
removeuseless:AddItem(vel,.1)
end
end
lightofdeath:Remove()
lightofdeath2:Remove()
for i = 1, 3 do
coroutine.wrap(function()
local shockwave = Instance.new("Part", Torso)
shockwave.Size = Vector3.new(1,1,1)
shockwave.CanCollide = false
shockwave.Anchored = true
shockwave.Transparency = .5
shockwave.BrickColor = BrickColor.new("White")
shockwave.CFrame = CFrame.new(pobox.Position)
local shockwavemesh = Instance.new("SpecialMesh", shockwave)
shockwavemesh.Scale = Vector3.new(7,3,7)
shockwavemesh.MeshId = "rbxassetid://20329976"
local shockwave2 = Instance.new("Part", Torso)
shockwave2.Size = Vector3.new(1,1,1)
shockwave2.CanCollide = false
shockwave2.Anchored = true
shockwave2.Transparency = .5
shockwave2.BrickColor = BrickColor.new("White")
shockwave2.CFrame = CFrame.new(pobox.Position)
local shockwavemesh2 = Instance.new("SpecialMesh", shockwave2)
shockwavemesh2.Scale = Vector3.new(5,3,5)
shockwavemesh2.MeshId = "rbxassetid://20329976"
for i = 1, 40 do
shockwave.CFrame = shockwave.CFrame * CFrame.Angles(math.rad(0),math.rad(0+15),0)
shockwave2.CFrame = shockwave2.CFrame * CFrame.Angles(math.rad(0),math.rad(0-8),0)
shockwave.Transparency = shockwave.Transparency + 0.025
shockwave2.Transparency = shockwave2.Transparency + 0.025
shockwavemesh2.Scale = shockwavemesh2.Scale + Vector3.new(9,1.5,9)
shockwavemesh.Scale = shockwavemesh.Scale + Vector3.new(9,1.5,9)
swait()
end
shockwave:Remove()
shockwave2:Remove()
end)()
coroutine.wrap(function()
local sk = Instance.new("Part",Torso)
sk.CanCollide = false
sk.Anchored = true
sk.BrickColor = BrickColor.new("White")
sk.Name = "sk"
sk.CFrame = pobox.CFrame * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local skmesh = Instance.new("SpecialMesh",sk)
skmesh.MeshId = "rbxassetid://662586858"
skmesh.Name = "wave"
skmesh.Scale = Vector3.new(.01,.001,.01)
for i = 1, 20 do
skmesh.Scale = skmesh.Scale + Vector3.new(.07,0,.07)
sk.Transparency = sk.Transparency + .05
swait()
end
sk:Remove()
end)()
coroutine.wrap(function()
local wshockwave = Instance.new("Part", Torso)
wshockwave.Size = Vector3.new(1,1,1)
wshockwave.CanCollide = false
wshockwave.Anchored = true
wshockwave.Transparency = .45
wshockwave.BrickColor = BrickColor.new("White")
wshockwave.CFrame = CFrame.new(pobox.Position) * CFrame.Angles(math.rad(math.random(-180,180)),0,math.rad(math.random(-180,180)))
local wshockwavemesh = Instance.new("SpecialMesh", wshockwave)
wshockwavemesh.Scale = Vector3.new(.1,.005,.1)
wshockwavemesh.Name = "wswm"
wshockwavemesh.MeshId = "rbxassetid://20329976"
removeuseless:AddItem(wshockwave,2)
for i = 1, 20 do
wshockwavemesh.Scale = wshockwavemesh.Scale + Vector3.new(9.5,0,9.5)
wshockwave.Transparency = wshockwave.Transparency + .05
swait()
end
wshockwave:Remove()
end)()
local boom = Instance.new("Part",Torso)
boom.Size = Vector3.new(6,6,6)
boom.Transparency = .1
boom.Shape = "Ball"
boom.BrickColor = BrickColor.new("White")
boom.CanCollide = false
boom.Anchored = true
boom.CFrame = CFrame.new(pobox.Position)
boom.Material = "Neon"
coroutine.wrap(function()
for i = 1, 20 do
boom.Size = boom.Size + Vector3.new(7,7,7)
boom.Transparency = boom.Transparency + .05
swait()
end
boom:Remove()
end)()
swait()
end
end
end)
 
checks1 = coroutine.wrap(function() -------Checks
while true do
if Root.Velocity.Magnitude < 5 and running == false then
position = "Idle"
elseif Root.Velocity.Magnitude > 5 and running == false then
position = "Walking"
else
end
wait()
end
end)
checks1()
 
function ray(POSITION, DIRECTION, RANGE, IGNOREDECENDANTS)
	return workspace:FindPartOnRay(Ray.new(POSITION, DIRECTION.unit * RANGE), IGNOREDECENDANTS)
end
 
function ray2(StartPos, EndPos, Distance, Ignore)
local DIRECTION = CFrame.new(StartPos,EndPos).lookVector
return ray(StartPos, DIRECTION, Distance, Ignore)
end
 
OrgnC0 = Neck.C0
local movelimbs = coroutine.wrap(function()
while RunSrv.RenderStepped:wait() do
TrsoLV = Torso.CFrame.lookVector
Dist = nil
Diff = nil
if not MseGuide then
print("Failed to recognize")
else
local _, Point = Workspace:FindPartOnRay(Ray.new(Head.CFrame.p, mouse.Hit.lookVector), Workspace, false, true)
Dist = (Head.CFrame.p-Point).magnitude
Diff = Head.CFrame.Y-Point.Y
local _, Point2 = Workspace:FindPartOnRay(Ray.new(LeftArm.CFrame.p, mouse.Hit.lookVector), Workspace, false, true)
Dist2 = (LeftArm.CFrame.p-Point).magnitude
Diff2 = LeftArm.CFrame.Y-Point.Y
HEADLERP.C0 = CFrame.new(0, -1.5, -0) * CFrame.Angles(math.rad(0), math.rad(0), math.rad(0))
Neck.C0 = Neck.C0:lerp(OrgnC0*CFrame.Angles((math.tan(Diff/Dist)*1), 0, (((Head.CFrame.p-Point).Unit):Cross(Torso.CFrame.lookVector)).Y*1), .1)
end
end
end)
movelimbs()
immortal = {}
for i,v in pairs(Character:GetDescendants()) do
	if v:IsA("BasePart") and v.Name ~= "lmagic" and v.Name ~= "rmagic" then
		if v ~= Root and v ~= Torso and v ~= Head and v ~= RightArm and v ~= LeftArm and v ~= RightLeg and v.Name ~= "lmagic" and v.Name ~= "rmagic" and v ~= LeftLeg then
			v.CustomPhysicalProperties = PhysicalProperties.new(0, 0, 0, 0, 0)
		end
		table.insert(immortal,{v,v.Parent,v.Material,v.Color,v.Transparency})
	elseif v:IsA("JointInstance") then
		table.insert(immortal,{v,v.Parent,nil,nil,nil})
	end
end
for e = 1, #immortal do
	if immortal[e] ~= nil then
		local STUFF = immortal[e]
		local PART = STUFF[1]
		local PARENT = STUFF[2]
		local MATERIAL = STUFF[3]
		local COLOR = STUFF[4]
		local TRANSPARENCY = STUFF[5]
if levitate then
		if PART.ClassName == "Part" and PART ~= Root and PART.Name ~= eyo1 and PART.Name ~= eyo2 and PART.Name ~= "lmagic" and PART.Name ~= "rmagic" then
			PART.Material = MATERIAL
			PART.Color = COLOR
			PART.Transparency = TRANSPARENCY
		end
		PART.AncestryChanged:connect(function()
			PART.Parent = PARENT
		end)
else
		if PART.ClassName == "Part" and PART ~= Root and PART.Name ~= "lmagic" and PART.Name ~= "rmagic" then
			PART.Material = MATERIAL
			PART.Color = COLOR
			PART.Transparency = TRANSPARENCY
		end
		PART.AncestryChanged:connect(function()
			PART.Parent = PARENT
		end)
end
	end
end
function immortality()
	for e = 1, #immortal do
		if immortal[e] ~= nil then
			local STUFF = immortal[e]
			local PART = STUFF[1]
			local PARENT = STUFF[2]
			local MATERIAL = STUFF[3]
			local COLOR = STUFF[4]
			local TRANSPARENCY = STUFF[5]
			if PART.ClassName == "Part" and PART == Root then
				PART.Material = MATERIAL
				PART.Color = COLOR
				PART.Transparency = TRANSPARENCY
			end
			if PART.Parent ~= PARENT then
				hum:Remove()
				PART.Parent = PARENT
				hum = Instance.new("Humanoid",Character)
if levitate then
eyo1:Remove()
eyo2:Remove()
end
                                hum.Name = "noneofurbusiness"
			end
		end
	end
end
coroutine.wrap(function()
while true do
if hum.Health < .1 then
immortality()
end
wait()
end
end)()
 
leftlocation = Instance.new("Part",LeftArm)
leftlocation.Size = Vector3.new(1,1,1)
leftlocation.Transparency = 1
leftlocationweld = weldBetween(leftlocation,LeftArm)
leftlocationweld.C0 = CFrame.new(0,1.2,0)
rightlocation = Instance.new("Part",RightArm)
rightlocation.Size = Vector3.new(1,1,1)
rightlocation.Transparency = 1
rightlocationweld = weldBetween(rightlocation,RightArm)
rightlocationweld.C0 = CFrame.new(0,1.2,0)
 
coroutine.wrap(function()
while true do
hpheight = 4 + 1 * math.sin(sine/12)
hum.HipHeight = hpheight
swait()
end
end)()
 
local anims = coroutine.wrap(function()
while true do
settime = 0.05
sine = sine + change
if position == "Walking" and attacking == false and running == false then
change = .5
walking = true
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
LEFTLEGLERP.C1 = LEFTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(0,0,0),.25)
RIGHTLEGLERP.C1 = RIGHTLEGLERP.C1:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(0),0,0),.25)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(.98,-.15,.5) * CFrame.Angles(math.rad(-70 - 5 * math.sin(sine/12)),math.rad(40 - 5 * math.sin(sine/12)),math.rad(-20)),.25)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.6, 0.5 - .1 * -math.sin(sine/12), 0) * CFrame.Angles(math.rad(35 - 2 * math.sin(sine/12)), math.rad(0), math.rad(-25 - 5 * math.sin(sine/12))), 0.25)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0, 0, 0) * CFrame.Angles(math.rad(-41 - 1 * math.sin(sine/9)), math.rad(0 + 0 * math.cos(sine/8)), math.rad(0) + Root.RotVelocity.Y / 9, math.cos(10 * math.cos(sine/10))), 0.25)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-0.54, 2 + .02 * math.sin(sine/12), 0.2 + .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(25 + 5 * math.sin(sine/12)), math.rad(-20), math.rad(0)), 0.25)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(0.54, 2 + .02 * math.sin(sine/12), 0.2 + .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(25 + 5 * math.sin(sine/12)), math.rad(20), math.rad(0)), 0.25)
elseif position == "Idle" and attacking == false and running == false then
change = .5
haloweld.C0 = haloweld.C0:lerp(CFrame.new(0,-4.5 + .5 * math.sin(sine/12),-2) * CFrame.Angles(math.rad(8 * math.sin(sine/12)),math.rad(11 * math.sin(sine/16)),0),.4)
ROOTLERP.C0 = ROOTLERP.C0:lerp(CFrame.new(0,0,0) * CFrame.Angles(math.rad(5 * math.sin(sine/12)),math.rad(2 * math.sin(sine/16)),math.rad(0)),.2)
RIGHTARMLERP.C0 = RIGHTARMLERP.C0:lerp(CFrame.new(-1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(math.rad(0),math.rad(12),math.rad(-40 - 6 * math.sin(sine/12))),.2)
LEFTARMLERP.C0 = LEFTARMLERP.C0:lerp(CFrame.new(1.3,1.05 + .15 * math.sin(sine/12),.2) * CFrame.Angles(0,math.rad(-12),math.rad(40 + 6 * math.sin(sine/12))),.2)
RIGHTLEGLERP.C0 = RIGHTLEGLERP.C0:lerp(CFrame.new(-.3 + .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9 - 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(-9 - 5 * math.sin(sine/12))),.2)
LEFTLEGLERP.C0 = LEFTLEGLERP.C0:lerp(CFrame.new(.3 - .1 * math.sin(sine/12), 1.95, .15 - .1 * math.sin(sine/12)) * CFrame.Angles(math.rad(9- 5 * math.sin(sine/12)),math.rad(2 + 1 * math.sin(sine/12)),math.rad(9 + 5 * math.sin(sine/12))),.2)
end
swait()
end
end)
anims()
warn("Justice given form. Made by Supr14")
