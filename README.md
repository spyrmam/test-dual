
if game:GetService("RunService"):IsClient()then error("Please run as a server script. Use h/ instead of hl/.")end;print("FE Compatibility: by WaverlyCole");InternalData = {}
do
	script.Parent = owner.Character
	local Event = Instance.new("RemoteEvent");Event.Name = "UserInput"
	local function NewFakeEvent()
		local Bind = Instance.new("BindableEvent")
		local Fake;Fake = {Connections = {},
		fakeEvent=true;
		Connect=function(self,Func)
			Bind.Event:connect(Func)
			self.Connections[Bind] = true
			return setmetatable({Connected = true},{
			__index = function (self,Index)
				if Index:lower() == "disconnect" then
					return function() Fake.Connections[Bind] = false;self.Connected = false end
				end
				return Fake[Index]
			end;
			__tostring = function() return "Connection" end;
		})
		end}
		Fake.connect = Fake.Connect;return Fake;
	end
	local Mouse = {Target=nil,Hit=CFrame.new(),KeyUp=NewFakeEvent(),KeyDown=NewFakeEvent(),Button1Up=NewFakeEvent(),Button1Down=NewFakeEvent()}
	local UserInputService = {InputBegan=NewFakeEvent(),InputEnded=NewFakeEvent()}
	local ContextActionService = {Actions={},BindAction = function(self,actionName,Func,touch,...)
		self.Actions[actionName] = Func and {Name=actionName,Function=Func,Keys={...}} or nil
	end};ContextActionService.UnBindAction = ContextActionService.BindAction
	local function TriggerEvent(self,Event,...)
		local Trigger = Mouse[Event]
		if Trigger and Trigger.fakeEvent and Trigger.Connections then
			for Connection,Active in pairs(Trigger.Connections) do if Active then Connection:Fire(...) end end
		end
	end
	Mouse.TrigEvent = TriggerEvent;UserInputService.TrigEvent = TriggerEvent
	Event.OnServerEvent:Connect(function(FiredBy,Input)
		if FiredBy.Name ~= owner.Name then return end
		if Input.MouseEvent then
			Mouse.Target = Input.Target;Mouse.Hit = Input.Hit
		else
			local Begin = Input.UserInputState == Enum.UserInputState.Begin
			if Input.UserInputType == Enum.UserInputType.MouseButton1 then return Mouse:TrigEvent(Begin and "Button1Down" or "Button1Up") end
			for _,Action in pairs(ContextActionService.Actions) do
				for _,Key in pairs(Action.Keys) do if Key==Input.KeyCode then Action.Function(Action.Name,Input.UserInputState,Input) end end
			end
			Mouse:TrigEvent(Begin and "KeyDown" or "KeyUp",Input.KeyCode.Name:lower())
			UserInputService:TrigEvent(Begin and "InputBegan" or "InputEnded",Input,false)
		end
	end)
	InternalData["Mouse"] = Mouse;InternalData["ContextActionService"] = ContextActionService;InternalData["UserInputService"] = UserInputService
	Event.Parent = NLS([[
		local Player = owner;local Event = script:WaitForChild("UserInput");local UserInputService = game:GetService("UserInputService");local Mouse = Player:GetMouse()
		local Input = function(Input,gameProcessedEvent)
			if gameProcessedEvent then return end
			Event:FireServer({KeyCode=Input.KeyCode,UserInputType=Input.UserInputType,UserInputState=Input.UserInputState})
		end
		UserInputService.InputBegan:Connect(Input);UserInputService.InputEnded:Connect(Input)
		local Hit,Target
		while wait(1/30) do
			if Hit ~= Mouse.Hit or Target ~= Mouse.Target then
				Hit,Target = Mouse.Hit,Mouse.Target;Event:FireServer({["MouseEvent"]=true,["Target"]=Target,["Hit"]=Hit})
			end
		end
	]],owner.Character)
end
RealGame = game;game = setmetatable({},{
	__index = function (self,Index)
		local Sandbox = function (Thing)
			if Thing:IsA("Player") then
				local RealPlayer = Thing
				return setmetatable({},{
					__index = function (self,Index)
						local Type = type(RealPlayer[Index])
						if Type == "function" then
							if Index:lower() == "getmouse" or Index:lower() == "mouse" then
								return function (self)return InternalData["Mouse"] end
							end
							return function (self,...)return RealPlayer[Index](RealPlayer,...) end
						end
						return RealPlayer[Index]
					end;
					__tostring = function(self) return RealPlayer.Name end
				})
			end
		end
		if RealGame[Index] then
			local Type = type(RealGame[Index])
			if Type == "function" then
				if Index:lower() == "getservice" or Index:lower() == "service" then
					return function (self,Service)
						local FakeServices = {
							["players"] = function()
								return setmetatable({},{
									__index = function (self2,Index2)
										local RealService = RealGame:GetService(Service)
										local Type2 = type(Index2)
										if Type2 == "function" then
											return function (self,...) return RealService[Index2](RealService,...)end
										else
											if Index2:lower() == "localplayer" then return Sandbox(owner) end
											return RealService[Index2]
										end
									end;
									__tostring = function(self) return RealGame:GetService(Service).Name end
								})
							end;
							["contextactionservice"] = function() return InternalData["ContextActionService"] end;
							["userinputservice"] = function() return InternalData["UserInputService"] end;
							["runservice"] = function()
								return setmetatable({},{
									__index = function(self2,Index2)
										local RealService = RealGame:GetService(Service)
										local Type2 = type(Index2)
										if Type2 == "function" then
											return function (self,...) return RealService[Index2](RealService,...) end
										else
											local RunServices = {
												["bindtorenderstep"] = function() return function (self,Name,Priority,Function) return RealGame:GetService("RunService").Stepped:Connect(Function) end end;
												["renderstepped"] = function() return RealService["Stepped"] end
											}
											if RunServices[Index2:lower()] then return RunServices[Index2:lower()]() end
											return RealService[Index2]
										end
									end
								})
							end
						}
						if FakeServices[Service:lower()] then return FakeServices[Service:lower()]() end
						return RealGame:GetService(Service)
					end
				end
				return function (self,...) return RealGame[Index](RealGame,...) end
			else
				if game:GetService(Index) then return game:GetService(Index) end
				return RealGame[Index]
			end
		end

-- DUALIECIDER
--[[
Genocider by Salvo_Starly
Remade by Nebula_Zorua

Credit to CKbackup's and idk..
             B
          U     R
         N  I N  H
          E     L
             L
]]--


wait(1 / 60)
Effects = { }
local Player = game.Players.localPlayer
local Character = Player.Character
local Humanoid = Character.Humanoid
local Mouse = Player:GetMouse()
local LeftArm = Character["Left Arm"]
local RightArm = Character["Right Arm"]
local LeftLeg = Character["Left Leg"]
local RightLeg = Character["Right Leg"]
local Head = Character.Head
local Torso = Character.Torso
local Camera = game.Workspace.CurrentCamera
local RootPart = Character.HumanoidRootPart
local RootJoint = RootPart.RootJoint
local attack = false
local Anim = 'Idle'
local attacktype = 1
local delays = false
local play = true
local targetted = nil
local Torsovelocity = (RootPart.Velocity * Vector3.new(1, 0, 1)).magnitude 
local velocity = RootPart.Velocity.y
local sine = 0
local change = 1
local doe = 0
local Create = LoadLibrary("RbxUtility").Create
Humanoid.WalkSpeed = 8
local m = Create("Model"){
	Parent = Character,
	Name = "WeaponModel",
}

Humanoid.Animator.Parent = nil
Character.Animate.Parent = nil

local newMotor = function(part0, part1, c0, c1)
	local w = Create('Motor'){
		Parent = part0,
		Part0 = part0,
		Part1 = part1,
		C0 = c0,
		C1 = c1,
	}
	return w
end

function clerp(a, b, t)
	return a:lerp(b, t)
end

RootCF = CFrame.fromEulerAnglesXYZ(-1.57, 0, 3.14)
NeckCF = CFrame.new(0, 1, 0, -1, -0, -0, 0, 0, 1, 0, 1, 0)

local RW = newMotor(Torso, RightArm, CFrame.new(1.5, 0, 0), CFrame.new(0, 0, 0)) 
local LW = newMotor(Torso, LeftArm, CFrame.new(-1.5, 0, 0), CFrame.new(0, 0, 0))
local RH = newMotor(Torso, RightLeg, CFrame.new(.5, -2, 0), CFrame.new(0, 0, 0))
local LH = newMotor(Torso, LeftLeg, CFrame.new(-.5, -2, 0), CFrame.new(0, 0, 0))
RootJoint.C1 = CFrame.new(0, 0, 0)
RootJoint.C0 = CFrame.new(0, 0, 0)
Torso.Neck.C1 = CFrame.new(0, 0, 0)
Torso.Neck.C0 = CFrame.new(0, 1.5, 0)

local rarmc1 = RW.C1
local larmc1 = LW.C1
local rlegc1 = RH.C1
local llegc1 = LH.C1

local resetc1 = false

function PlayAnimationFromTable(table, speed, bool)
	RootJoint.C0 = clerp(RootJoint.C0, table[1], speed) 
	Torso.Neck.C0 = clerp(Torso.Neck.C0, table[2], speed) 
	RW.C0 = clerp(RW.C0, table[3], speed) 
	LW.C0 = clerp(LW.C0, table[4], speed) 
	RH.C0 = clerp(RH.C0, table[5], speed) 
	LH.C0 = clerp(LH.C0, table[6], speed) 
	if bool == true then
		if resetc1 == false then
			resetc1 = true
			RootJoint.C1 = RootJoint.C1
			Torso.Neck.C1 = Torso.Neck.C1
			RW.C1 = rarmc1
			LW.C1 = larmc1
			RH.C1 = rlegc1
			LH.C1 = llegc1
		end
	end
end

ArtificialHB = Create("BindableEvent", script){
	Parent = script,
	Name = "Heartbeat",
}

script:WaitForChild("Heartbeat")

frame = 1 / 30
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
		ArtificialHB.Event:wait()
	else
		for i = 0, num do
			ArtificialHB.Event:wait()
		end
	end
end

function RemoveOutlines(part)
	part.TopSurface, part.BottomSurface, part.LeftSurface, part.RightSurface, part.FrontSurface, part.BackSurface = 10, 10, 10, 10, 10, 10
end
	
CFuncs = {	
	["Part"] = {
		Create = function(Parent, Material, Reflectance, Transparency, BColor, Name, Size)
			local Part = Create("Part"){
				Parent = Parent,
				Reflectance = Reflectance,
				Transparency = Transparency,
				CanCollide = false,
				Locked = true,
				BrickColor = BrickColor.new(tostring(BColor)),
				Name = Name,
				Size = Size,
				Material = Material,
			}
			RemoveOutlines(Part)
			return Part
		end;
	};
	
	["Mesh"] = {
		Create = function(Mesh, Part, MeshType, MeshId, OffSet, Scale)
			local Msh = Create(Mesh){
				Parent = Part,
				Offset = OffSet,
				Scale = Scale,
			}
			if Mesh == "SpecialMesh" then
				Msh.MeshType = MeshType
				Msh.MeshId = MeshId
			end
			return Msh
		end;
	};
	
	["Mesh"] = {
		Create = function(Mesh, Part, MeshType, MeshId, OffSet, Scale)
			local Msh = Create(Mesh){
				Parent = Part,
				Offset = OffSet,
				Scale = Scale,
			}
			if Mesh == "SpecialMesh" then
				Msh.MeshType = MeshType
				Msh.MeshId = MeshId
			end
			return Msh
		end;
	};
	
	["Weld"] = {
		Create = function(Parent, Part0, Part1, C0, C1)
			local Weld = Create("Weld"){
				Parent = Parent,
				Part0 = Part0,
				Part1 = Part1,
				C0 = C0,
				C1 = C1,
			}
			return Weld
		end;
	};

	["Sound"] = {
		Create = function(id, par, vol, pit) 
			coroutine.resume(coroutine.create(function()
				local S = Create("Sound"){
					Volume = vol,
					Pitch = pit or 1,
					SoundId = id,
					Parent = par or workspace,
				}
				wait() 
				S:play() 
				game:GetService("Debris"):AddItem(S, 6)
			end))
		end;
	};
	
	["ParticleEmitter"] = {
		Create = function(Parent, Color1, Color2, LightEmission, Size, Texture, Transparency, ZOffset, Accel, Drag, LockedToPart, VelocityInheritance, EmissionDirection, Enabled, LifeTime, Rate, Rotation, RotSpeed, Speed, VelocitySpread)
			local fp = Create("ParticleEmitter"){
				Parent = Parent,
				Color = ColorSequence.new(Color1, Color2),
				LightEmission = LightEmission,
				Size = Size,
				Texture = Texture,
				Transparency = Transparency,
				ZOffset = ZOffset,
				Acceleration = Accel,
				Drag = Drag,
				LockedToPart = LockedToPart,
				VelocityInheritance = VelocityInheritance,
				EmissionDirection = EmissionDirection,
				Enabled = Enabled,
				Lifetime = LifeTime,
				Rate = Rate,
				Rotation = Rotation,
				RotSpeed = RotSpeed,
				Speed = Speed,
				VelocitySpread = VelocitySpread,
			}
			return fp
		end;
	};

	CreateTemplate = {
	
	};
}



New = function(Object, Parent, Name, Data)
	local Object = Instance.new(Object)
	for Index, Value in pairs(Data or {}) do
		Object[Index] = Value
	end
	Object.Parent = Parent
	Object.Name = Name
	return Object
end
	

ShadowHead = New("Part",Character,"ShadowHead",{CanCollide = false,BrickColor = BrickColor.new("Really black"),Size = Vector3.new(1.20000005, 0.600000024, 1),CFrame = CFrame.new(68.5999985, 0.700013041, 9.89999962, 1, 0, 0, 0, 1, 0, 0, 0, 1),Material=Enum.Material.Neon})
ShadowHead.Material = "Neon"
Mesh = New("SpecialMesh",ShadowHead,"Mesh",{Scale = Vector3.new(1.25999999, 1.5, 1.25999999),})
Weld = New("Weld",ShadowHead,"mot",{Part0 = ShadowHead,Part1 = Character.Head,C1 = CFrame.new(0, 0.200000048, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1),})

Handle = New("Part",m,"Handle",{Material = Enum.Material.SmoothPlastic,Transparency = 1,Transparency = 1,Size = Vector3.new(1.78105354, 1.21267569, 0.446083069),CFrame = CFrame.new(3.48884702, 1.89424598, -23.6011944, 0.0172098875, -7.30156898e-07, 0.999851942, 0.999853492, 1.19907781e-08, -0.0172098596, -1.80598714e-09, 1.00000083, 1.4975667e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
moter = New("Weld",Handle,"mot",{Part0 = RightArm,Part1 = Handle,})	
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.46324158, 2.55061626, -23.0996056, 0.0172099378, 1.26508749e-05, 0.999852061, 0.999856234, 0.000737910799, -0.0172098614, -0.000738026109, 1.00000215, 2.29468287e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.492160469, 0.24608025, 0.123040132),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098838, 0.999853015, -0.000738022442, 1.18836761e-05, 0.000737924012, 1.00000048, 0.999851942, -0.0172098614, 1.52736902e-06),C1 = CFrame.new(0.655831456, 0.501588821, -0.0368974209, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.200000003, 0.270688266, 0.270688266),CFrame = CFrame.new(3.47537327, 1.11045444, -23.2953625, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.123040125, 1, 1),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.783906102, 0.305831909, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(1.47648132, 0.221472263, 0.344512314),CFrame = CFrame.new(3.48828244, 1.86040294, -23.3093491, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 1.00999999, 1),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(-0.0338476896, 0.291845322, 1.8119812e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.98432076, 0.200000003, 0.24608022),CFrame = CFrame.new(3.48404813, 1.61474013, -23.4433804, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.246080264, 1),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279546618, 0.157814026, 1.21593475e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.984321058, 0.200000003, 0.200000003),CFrame = CFrame.new(3.36101127, 1.61687815, -23.4187717, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.492160618, 0.492160439),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279526353, 0.182422638, -0.123043299, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.53706741, 2.54934502, -23.0996056, 0.0172099378, 1.26508749e-05, 0.999852061, 0.999856234, 0.000737910799, -0.0172098614, -0.000738026109, 1.00000215, 2.29468287e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.492160469, 0.246080235, 0.123040132),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098838, 0.999853015, -0.000738022442, 1.18836761e-05, 0.000737924012, 1.00000048, 0.999851942, -0.0172098614, 1.52736902e-06),C1 = CFrame.new(0.655830979, 0.501588821, 0.0369393826, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(1.47648132, 0.200000003, 0.200000003),CFrame = CFrame.new(3.48828554, 1.86097884, -23.1606178, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.7382406),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.0332717896, 0.440576553, 1.14440918e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Partss1 = New("Part",m,"Part",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.200000003, 0.221472204, 0.221472189),CFrame = CFrame.new(3.47526526, 1.10428262, -23.2953568, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Partss1,"Mesh",{Scale = Vector3.new(0.123040125, 1, 1),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Partss1,"mot",{Part0 = Partss1,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.790078878, 0.305837631, 1.57356262e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.49040294, 1.9837563, -23.5174713, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.615200579, 0.36912033, 0.24608025),MeshId = "http://www.roblox.com/asset/?id=3270017",MeshType = Enum.MeshType.FileMesh,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(0.0895236731, 0.0837230682, 1.52587891e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.295296252, 0.738240778, 0.369120389),CFrame = CFrame.new(3.49802279, 2.42631888, -23.8138046, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(0.532151103, -0.212610245, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.344512314, 0.78745681, 0.344512314),CFrame = CFrame.new(3.49802279, 2.42631888, -23.8138046, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(0.532151103, -0.212610245, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.984321058, 0.200000003, 0.200000003),CFrame = CFrame.new(3.60706425, 1.61264217, -23.4187698, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.492160618, 0.492160439),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279527187, 0.182424545, 0.12304616, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.47672749, 1.18911982, -23.1232109, 0.999851942, 0.00638213893, 0.0159827713, -0.0172098316, 0.37065956, 0.928613782, 4.44045327e-06, -0.928749561, 0.370713741),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(0.24608025, 0.246080264, 0.615200639),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098316, 3.67313623e-06, 0.00638283044, 0.370658338, -0.928748012, 0.0159824342, 0.928610861, 0.370713145),C1 = CFrame.new(-0.705229163, 0.477983475, 1.76429749e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.344512254, 0.787456751, 0.200000003),CFrame = CFrame.new(3.50247502, 2.68478155, -23.8132839, 0.999851942, 1.0713723e-05, -0.0172099732, -0.0172098912, 0.000738376984, -0.999856234, 4.21693585e-06, 1.00000226, 0.000738456321),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.861280859),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098912, 3.44961882e-06, 9.9465251e-06, 0.000738390256, 1.0000006, -0.0172099192, -0.999853015, 0.000738452654),C1 = CFrame.new(0.790651679, -0.212089539, 2.07424164e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.4904809, 1.98827124, -23.5162678, -0.999852061, -0.0148990965, 0.00861407723, 0.0172099397, -0.865535975, 0.500560343, -4.36594746e-06, 0.500633478, 0.865662456),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(0.24608025, 0.369120389, 0.861280918),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -0.999851942, 0.0172099397, -3.59863043e-06, -0.0148994327, -0.865533173, 0.500632644, 0.00861338526, 0.500558794, 0.865661025),C1 = CFrame.new(0.0940393209, 0.0849266052, 1.54972076e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.442944348, 0.200000003, 0.200000003),CFrame = CFrame.new(3.37415838, 2.37982368, -23.1609974, 0.0172098633, 1.48413446e-05, 0.999851882, 0.999856234, 0.0007376945, -0.0172097869, -0.000737846654, 1.00000215, 7.44058752e-08),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098093, 0.999853015, -0.000737842987, 1.40741467e-05, 0.000737707771, 1.00000048, 0.999851823, -0.0172097888, -6.92903996e-07),C1 = CFrame.new(0.483531356, 0.440196991, -0.12302804, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.61520052, 0.200000003, 0.200000003),CFrame = CFrame.new(3.35783243, 1.43252242, -23.1602993, 0.0172098633, 1.48413446e-05, 0.999851882, 0.999856234, 0.0007376945, -0.0172097869, -0.000737846654, 1.00000215, 7.44058752e-08),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.0172098093, 0.999853015, -0.000737842987, 1.40741467e-05, 0.000737707771, 1.00000048, 0.999851823, -0.0172097888, -6.92903996e-07),C1 = CFrame.new(-0.463909149, 0.440895081, -0.123048544, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(1.47648132, 0.200000003, 0.200000003),CFrame = CFrame.new(3.61130548, 1.85886192, -23.160614, -0.0172098689, 1.04156998e-05, -0.99985218, -0.999856234, 0.000738191127, 0.0172097925, 0.000738266157, 1.00000238, -4.55221243e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, -0.0172098149, -0.999853075, 0.00073826249, 9.64850187e-06, 0.00073820434, 1.00000072, -0.999852121, 0.0172097944, -3.78489494e-06),C1 = CFrame.new(-0.0332713127, 0.440580368, 0.123049498, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.36912033, 0.738240778, 0.200000003),CFrame = CFrame.new(3.50183868, 2.64789343, -23.8132629, 0.999851942, 1.0818032e-05, -0.017209895, -0.0172098186, 0.000737608876, -0.999856234, 4.13497901e-06, 1.00000238, 0.000737691764),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.738240719),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098186, 3.36766243e-06, 1.00508332e-05, 0.000737622147, 1.00000072, -0.0172098409, -0.999853015, 0.000737688097),C1 = CFrame.new(0.753758311, -0.212068558, 1.93119049e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.344512254, 0.787456751, 0.200000003),CFrame = CFrame.new(3.49357963, 2.16808391, -23.8129005, 0.999852061, -1.05647114e-05, 0.0172100067, -0.0172099303, -0.000737611321, 0.999856114, 4.36594746e-06, -1.00000226, -0.000737689785),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.861280859),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851942, -0.0172099303, 3.59863043e-06, -9.79751348e-06, -0.000737624592, -1.0000006, 0.0172099527, 0.999852955, -0.000737686118),C1 = CFrame.new(0.273878455, -0.211706161, 1.90734863e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.36912033, 0.738240659, 0.200000003),CFrame = CFrame.new(3.49420977, 2.20497489, -23.8129292, 0.999852061, -1.05647114e-05, 0.0172100067, -0.0172099303, -0.000737611321, 0.999856114, 4.36594746e-06, -1.00000226, -0.000737689785),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.738240719),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle,C0 = CFrame.new(0, 0, 0, 0.999851942, -0.0172099303, 3.59863043e-06, -9.79751348e-06, -0.000737624592, -1.0000006, 0.0172099527, 0.999852955, -0.000737686118),C1 = CFrame.new(0.310774684, -0.211734772, 1.43051147e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})

Handle2 = New("Part",m,"Handle2",{Material = Enum.Material.SmoothPlastic,Transparency = 1,Transparency = 1,Size = Vector3.new(1.78105354, 1.21267569, 0.446083069),CFrame = CFrame.new(3.48884702, 1.89424598, -23.6011944, 0.0172098875, -7.30156898e-07, 0.999851942, 0.999853492, 1.19907781e-08, -0.0172098596, -1.80598714e-09, 1.00000083, 1.4975667e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
moter2 = New("Weld",Handle2,"mot",{Part0 = LeftArm,Part1 = Handle2,})	
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.46324158, 2.55061626, -23.0996056, 0.0172099378, 1.26508749e-05, 0.999852061, 0.999856234, 0.000737910799, -0.0172098614, -0.000738026109, 1.00000215, 2.29468287e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.492160469, 0.24608025, 0.123040132),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098838, 0.999853015, -0.000738022442, 1.18836761e-05, 0.000737924012, 1.00000048, 0.999851942, -0.0172098614, 1.52736902e-06),C1 = CFrame.new(0.655831456, 0.501588821, -0.0368974209, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.200000003, 0.270688266, 0.270688266),CFrame = CFrame.new(3.47537327, 1.11045444, -23.2953625, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.123040125, 1, 1),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.783906102, 0.305831909, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(1.47648132, 0.221472263, 0.344512314),CFrame = CFrame.new(3.48828244, 1.86040294, -23.3093491, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 1.00999999, 1),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(-0.0338476896, 0.291845322, 1.8119812e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.98432076, 0.200000003, 0.24608022),CFrame = CFrame.new(3.48404813, 1.61474013, -23.4433804, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.246080264, 1),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279546618, 0.157814026, 1.21593475e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.984321058, 0.200000003, 0.200000003),CFrame = CFrame.new(3.36101127, 1.61687815, -23.4187717, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.492160618, 0.492160439),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279526353, 0.182422638, -0.123043299, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.53706741, 2.54934502, -23.0996056, 0.0172099378, 1.26508749e-05, 0.999852061, 0.999856234, 0.000737910799, -0.0172098614, -0.000738026109, 1.00000215, 2.29468287e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(0.492160469, 0.246080235, 0.123040132),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098838, 0.999853015, -0.000738022442, 1.18836761e-05, 0.000737924012, 1.00000048, 0.999851942, -0.0172098614, 1.52736902e-06),C1 = CFrame.new(0.655830979, 0.501588821, 0.0369393826, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(1.47648132, 0.200000003, 0.200000003),CFrame = CFrame.new(3.48828554, 1.86097884, -23.1606178, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("BlockMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.7382406),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.0332717896, 0.440576553, 1.14440918e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Partss2 = New("Part",m,"Part",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.200000003, 0.221472204, 0.221472189),CFrame = CFrame.new(3.47526526, 1.10428262, -23.2953568, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Partss2,"Mesh",{Scale = Vector3.new(0.123040125, 1, 1),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Partss2,"mot",{Part0 = Partss2,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.790078878, 0.305837631, 1.57356262e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.49040294, 1.9837563, -23.5174713, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(0.615200579, 0.36912033, 0.24608025),MeshId = "http://www.roblox.com/asset/?id=3270017",MeshType = Enum.MeshType.FileMesh,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(0.0895236731, 0.0837230682, 1.52587891e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.295296252, 0.738240778, 0.369120389),CFrame = CFrame.new(3.49802279, 2.42631888, -23.8138046, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(0.532151103, -0.212610245, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.344512314, 0.78745681, 0.344512314),CFrame = CFrame.new(3.49802279, 2.42631888, -23.8138046, 0.0172099452, 3.70001203e-08, 0.999852061, 0.99985671, -3.59708352e-09, -0.0172098596, -4.18887769e-09, 1.0000025, 2.26488032e-06),BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),C1 = CFrame.new(0.532151103, -0.212610245, 1.74045563e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Part = New("Part",m,"Part",{Material = Enum.Material.SmoothPlastic,Shape = Enum.PartType.Cylinder,Size = Vector3.new(0.984321058, 0.200000003, 0.200000003),CFrame = CFrame.new(3.60706425, 1.61264217, -23.4187698, 0.0172099359, 1.26359728e-05, 0.999851942, 0.999856234, 0.000738034665, -0.0172098596, -0.000738148578, 1.00000226, 2.36918868e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Part,"Mesh",{Scale = Vector3.new(1, 0.492160618, 0.492160439),MeshType = Enum.MeshType.Cylinder,})
mot = New("Weld",Part,"mot",{Part0 = Part,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098819, 0.999853015, -0.00073814491, 1.18687749e-05, 0.000738047936, 1.0000006, 0.999851882, -0.0172098596, 1.60187483e-06),C1 = CFrame.new(-0.279527187, 0.182424545, 0.12304616, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.47672749, 1.18911982, -23.1232109, 0.999851942, 0.00638213893, 0.0159827713, -0.0172098316, 0.37065956, 0.928613782, 4.44045327e-06, -0.928749561, 0.370713741),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(0.24608025, 0.246080264, 0.615200639),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098316, 3.67313623e-06, 0.00638283044, 0.370658338, -0.928748012, 0.0159824342, 0.928610861, 0.370713145),C1 = CFrame.new(-0.705229163, 0.477983475, 1.76429749e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.344512254, 0.787456751, 0.200000003),CFrame = CFrame.new(3.50247502, 2.68478155, -23.8132839, 0.999851942, 1.0713723e-05, -0.0172099732, -0.0172098912, 0.000738376984, -0.999856234, 4.21693585e-06, 1.00000226, 0.000738456321),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.861280859),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098912, 3.44961882e-06, 9.9465251e-06, 0.000738390256, 1.0000006, -0.0172099192, -0.999853015, 0.000738452654),C1 = CFrame.new(0.790651679, -0.212089539, 2.07424164e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.200000003, 0.200000003, 0.200000003),CFrame = CFrame.new(3.4904809, 1.98827124, -23.5162678, -0.999852061, -0.0148990965, 0.00861407723, 0.0172099397, -0.865535975, 0.500560343, -4.36594746e-06, 0.500633478, 0.865662456),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(0.24608025, 0.369120389, 0.861280918),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, -0.999851942, 0.0172099397, -3.59863043e-06, -0.0148994327, -0.865533173, 0.500632644, 0.00861338526, 0.500558794, 0.865661025),C1 = CFrame.new(0.0940393209, 0.0849266052, 1.54972076e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.442944348, 0.200000003, 0.200000003),CFrame = CFrame.new(3.37415838, 2.37982368, -23.1609974, 0.0172098633, 1.48413446e-05, 0.999851882, 0.999856234, 0.0007376945, -0.0172097869, -0.000737846654, 1.00000215, 7.44058752e-08),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098093, 0.999853015, -0.000737842987, 1.40741467e-05, 0.000737707771, 1.00000048, 0.999851823, -0.0172097888, -6.92903996e-07),C1 = CFrame.new(0.483531356, 0.440196991, -0.12302804, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.61520052, 0.200000003, 0.200000003),CFrame = CFrame.new(3.35783243, 1.43252242, -23.1602993, 0.0172098633, 1.48413446e-05, 0.999851882, 0.999856234, 0.0007376945, -0.0172097869, -0.000737846654, 1.00000215, 7.44058752e-08),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.0172098093, 0.999853015, -0.000737842987, 1.40741467e-05, 0.000737707771, 1.00000048, 0.999851823, -0.0172097888, -6.92903996e-07),C1 = CFrame.new(-0.463909149, 0.440895081, -0.123048544, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(1.47648132, 0.200000003, 0.200000003),CFrame = CFrame.new(3.61130548, 1.85886192, -23.160614, -0.0172098689, 1.04156998e-05, -0.99985218, -0.999856234, 0.000738191127, 0.0172097925, 0.000738266157, 1.00000238, -4.55221243e-06),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 0.369120389, 0.492160529),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, -0.0172098149, -0.999853075, 0.00073826249, 9.64850187e-06, 0.00073820434, 1.00000072, -0.999852121, 0.0172097944, -3.78489494e-06),C1 = CFrame.new(-0.0332713127, 0.440580368, 0.123049498, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.36912033, 0.738240778, 0.200000003),CFrame = CFrame.new(3.50183868, 2.64789343, -23.8132629, 0.999851942, 1.0818032e-05, -0.017209895, -0.0172098186, 0.000737608876, -0.999856234, 4.13497901e-06, 1.00000238, 0.000737691764),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.738240719),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.999851882, -0.0172098186, 3.36766243e-06, 1.00508332e-05, 0.000737622147, 1.00000072, -0.0172098409, -0.999853015, 0.000737688097),C1 = CFrame.new(0.753758311, -0.212068558, 1.93119049e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.344512254, 0.787456751, 0.200000003),CFrame = CFrame.new(3.49357963, 2.16808391, -23.8129005, 0.999852061, -1.05647114e-05, 0.0172100067, -0.0172099303, -0.000737611321, 0.999856114, 4.36594746e-06, -1.00000226, -0.000737689785),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.861280859),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.999851942, -0.0172099303, 3.59863043e-06, -9.79751348e-06, -0.000737624592, -1.0000006, 0.0172099527, 0.999852955, -0.000737686118),C1 = CFrame.new(0.273878455, -0.211706161, 1.90734863e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})
Wedge = New("WedgePart",m,"Wedge",{BrickColor = BrickColor.new("Black"),Material = Enum.Material.SmoothPlastic,Size = Vector3.new(0.36912033, 0.738240659, 0.200000003),CFrame = CFrame.new(3.49420977, 2.20497489, -23.8129292, 0.999852061, -1.05647114e-05, 0.0172100067, -0.0172099303, -0.000737611321, 0.999856114, 4.36594746e-06, -1.00000226, -0.000737689785),CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,Color = Color3.new(0.105882, 0.164706, 0.207843),})
Mesh = New("SpecialMesh",Wedge,"Mesh",{Scale = Vector3.new(1, 1, 0.738240719),MeshType = Enum.MeshType.Wedge,})
mot = New("Weld",Wedge,"mot",{Part0 = Wedge,Part1 = Handle2,C0 = CFrame.new(0, 0, 0, 0.999851942, -0.0172099303, 3.59863043e-06, -9.79751348e-06, -0.000737624592, -1.0000006, 0.0172099527, 0.999852955, -0.000737686118),C1 = CFrame.new(0.310774684, -0.211734772, 1.43051147e-05, 0.0172098875, 0.999853492, -1.80598714e-09, -7.30156898e-07, 1.19907781e-08, 1.00000083, 0.999851942, -0.0172098596, 1.4975667e-06),})

for _,v in pairs(m:children()) do
if v:IsA("Part") then
v.CanCollide = false
end
end

function rayCast(Position, Direction, Range, Ignore)
	return game:service("Workspace"):FindPartOnRay(Ray.new(Position, Direction.unit * (Range or 999.999)), Ignore) 
end 

--[[FindNearestTorso = function(pos)
	local list = (game.Workspace:children())
	local torso = nil
	local dist = 1000
	local temp, human, temp2 = nil, nil, nil
	for x = 1, #list do
		temp2 = list[x]
		if temp2.className == "Model" and temp2.Name ~= Character.Name then
			temp = temp2:findFirstChild("Torso")
			human = temp2:findFirstChild("Humanoid")
			if temp ~= nil and human ~= nil and human.Health > 0 and (temp.Position - pos).magnitude < dist then
				local dohit = true
				if dohit == true then
					torso = temp
					dist = (temp.Position - pos).magnitude
				end
			end
		end
	end
	return torso, dist
end]]
function FindNearestTorso(Position, Distance, SinglePlayer)
	if SinglePlayer then
		return (SinglePlayer.Torso.CFrame.p - Position).magnitude < Distance
	end
	local List = {}
	for i, v in pairs(workspace:GetChildren()) do
		if v:IsA("Model") then
			if v.Name == "Dummy" then
				for _,k in next, v:children() do
					if k:IsA"Model" then
						print(k.Name)
						if k:FindFirstChild"Torso" then
							if k ~= Character then
								if (k.Torso.Position - Position).magnitude <= Distance then
									table.insert(List, k)
								end 
							end 
						end
					end
				end
			end
			if v:findFirstChild("Torso") then
				if v ~= Character then
					if (v.Torso.Position - Position).magnitude <= Distance then
						table.insert(List, v)
					end 
				end 
			end 
		end
	end
	return List
end
function Damage(Part, hit, minim, maxim, knockback, Type, Property, Delay, HitSound, HitPitch)
	if hit.Parent == nil then
		return
	end
	local h = hit.Parent:FindFirstChild("Humanoid")
	for _, v in pairs(hit.Parent:children()) do
		if v:IsA("Humanoid") then
			h = v
		end
	end
	if h ~= nil and hit.Parent.Name ~= Character.Name and hit.Parent:FindFirstChild("Torso") ~= nil then
		if hit.Parent:findFirstChild("DebounceHit") ~= nil then
			if hit.Parent.DebounceHit.Value == true then
				return
			end
		end
		local c = Create("ObjectValue"){
			Name = "creator",
			Value = game:service("Players").LocalPlayer,
			Parent = h,
		}
		game:GetService("Debris"):AddItem(c, .5)
		if HitSound ~= nil and HitPitch ~= nil then
			CFuncs.Sound.Create(HitSound, hit, 1, HitPitch) 
		end
		local Damage = math.random(minim, maxim)
		local blocked = false
		local block = hit.Parent:findFirstChild("Block")
		if block ~= nil then
			if block.className == "IntValue" then
				if block.Value > 0 then
					blocked = true
					block.Value = block.Value - 1
					print(block.Value)
				end
			end
		end
		if blocked == false then
			h.Health = h.Health - Damage
			ShowDamage((Part.CFrame * CFrame.new(0, 0, (Part.Size.Z / 2)).p + Vector3.new(0, 1.5, 0)), -Damage, 1.5, BrickColor.new("Really black").Color)
		else
			h.Health = h.Health - (Damage / 2)
			ShowDamage((Part.CFrame * CFrame.new(0, 0, (Part.Size.Z / 2)).p + Vector3.new(0, 1.5, 0)), -Damage, 1.5, BrickColor.new("Really black").Color)
		end
		if Type == "Knockdown" then
			local hum = hit.Parent.Humanoid
			hum.PlatformStand = true
			coroutine.resume(coroutine.create(function(HHumanoid)
				swait(1)
				HHumanoid.PlatformStand = false
			end), hum)
			local angle = (hit.Position - (Property.Position + Vector3.new(0, 0, 0))).unit
			local bodvol = Create("BodyVelocity"){
				velocity = angle * knockback,
				P = 5000,
				maxForce = Vector3.new(8e+003, 8e+003, 8e+003),
				Parent = hit,
			}
			local rl = Create("BodyAngularVelocity"){
				P = 3000,
				maxTorque = Vector3.new(500000, 500000, 500000) * 50000000000000,
				angularvelocity = Vector3.new(math.random(-10, 10), math.random(-10, 10), math.random(-10, 10)),
				Parent = hit,
			}
			game:GetService("Debris"):AddItem(bodvol, .5)
			game:GetService("Debris"):AddItem(rl, .5)
		elseif Type == "Normal" then
			local vp = Create("BodyVelocity"){
				P = 500,
				maxForce = Vector3.new(math.huge, 0, math.huge),
				velocity = Property.CFrame.lookVector * knockback + Property.Velocity / 1.05,
			}
			if knockback > 0 then
				vp.Parent = hit.Parent.Torso
			end
			game:GetService("Debris"):AddItem(vp, .5)
		elseif Type == "Up" then
			local bodyVelocity = Create("BodyVelocity"){
				velocity = Vector3.new(0, 20, 0),
				P = 5000,
				maxForce = Vector3.new(8e+003, 8e+003, 8e+003),
				Parent = hit,
			}
			game:GetService("Debris"):AddItem(bodyVelocity, .5)
		elseif Type == "DarkUp" then
			coroutine.resume(coroutine.create(function()
				for i = 0, 1, 0.1 do
					swait()
					Effects.Block.Create(BrickColor.new("Black"), hit.Parent.Torso.CFrame, 5, 5, 5, 1, 1, 1, .08, 1)
				end
			end))
			local bodyVelocity = Create("BodyVelocity"){
				velocity = Vector3.new(0, 20, 0),
				P = 5000,
				maxForce = Vector3.new(8e+003, 8e+003, 8e+003),
				Parent = hit,
			}
			game:GetService("Debris"):AddItem(bodyVelocity, 1)
		elseif Type == "Snare" then
			local bp = Create("BodyPosition"){
				P = 2000,
				D = 100,
				maxForce = Vector3.new(math.huge, math.huge, math.huge),
				position = hit.Parent.Torso.Position,
				Parent = hit.Parent.Torso,
			}
			game:GetService("Debris"):AddItem(bp, 1)
		elseif Type == "Freeze" then
			local BodPos = Create("BodyPosition"){
				P = 50000,
				D = 1000,
				maxForce = Vector3.new(math.huge, math.huge, math.huge),
				position = hit.Parent.Torso.Position,
				Parent = hit.Parent.Torso,
			}
			local BodGy = Create("BodyGyro") {
				maxTorque = Vector3.new(4e+005, 4e+005, 4e+005) * math.huge ,
				P = 20e+003,
				Parent = hit.Parent.Torso,
				cframe = hit.Parent.Torso.CFrame,
			}
			hit.Parent.Torso.Anchored = true
			coroutine.resume(coroutine.create(function(Part) 
				swait(1.5)
				Part.Anchored = false
			end), hit.Parent.Torso)
			game:GetService("Debris"):AddItem(BodPos, 3)
			game:GetService("Debris"):AddItem(BodGy, 3)
		end
		local debounce = Create("BoolValue"){
			Name = "DebounceHit",
			Parent = hit.Parent,
			Value = true,
		}
		game:GetService("Debris"):AddItem(debounce, Delay)
		c = Create("ObjectValue"){
			Name = "creator",
			Value = Player,
			Parent = h,
		}
		game:GetService("Debris"):AddItem(c, .5)
	end
end

function ShowDamage(Pos, Text, Time, Color)
	local Rate = (1 / 30)
	local Pos = (Pos or Vector3.new(0, 0, 0))
	local Text = (Text or "")
	local Time = (Time or 2)
	local Color = (Color or Color3.new(1, 0, 1))
	local EffectPart = CFuncs.Part.Create(workspace, "SmoothPlastic", 0, 1, BrickColor.new(Color), "Effect", Vector3.new(0, 0, 0))
	EffectPart.Anchored = true
	local BillboardGui = Create("BillboardGui"){
		Size = UDim2.new(3, 0, 3, 0),
		Adornee = EffectPart,
		Parent = EffectPart,
	}
	local TextLabel = Create("TextLabel"){
		BackgroundTransparency = 1,
		Size = UDim2.new(1, 0, 1, 0),
		Text = Text,
		Font = "SciFi",
		TextColor3 = Color,
		TextScaled = true,
		Parent = BillboardGui,
	}
	game.Debris:AddItem(EffectPart, (Time))
	EffectPart.Parent = game:GetService("Workspace")
	delay(0, function()
		local Frames = (Time / Rate)
		for Frame = 1, Frames do
			wait(Rate)
			local Percent = (Frame / Frames)
			EffectPart.CFrame = CFrame.new(Pos) + Vector3.new(0, Percent, 0)
			TextLabel.TextTransparency = Percent
		end
		if EffectPart and EffectPart.Parent then
			EffectPart:Destroy()
		end
	end)
end

local lrs = game:service'RunService'.RenderStepped
function bleed(chr,timeforbleed)
	local Rate = (1/30)
	local clr = BrickColor.new"Maroon"
	if chr.Name == "Quil_Cyndaquil" or chr.Name == "TheBoozled" or chr.Parent.Name == "Quil_Cyndaquil" or chr.Parent.Name == "TheBoozled" then
		clr = BrickColor.new"Teal"
	elseif chr.Name == "Salvo_Starly" or chr.Parent.Name == "Salvo_Starly" then
		clr = BrickColor.new"Really red"
	elseif chr.Name == "visabledude" or chr.Parent.Name == "visabledude" then
		clr = BrickColor.new"Really blue"
	end
	local Frames = timeforbleed / Rate
	wait(.25)

	for Frame = 1, Frames do
		coroutine.wrap(function()
			local p = Instance.new("Part",workspace)
			p.BrickColor = clr
			p.Size = Vector3.new(.25,.25,.25)
			p.Material = Enum.Material.Neon
			local prt
			if chr:IsA"Model" then
				prt =  chr:FindFirstChild"Torso" or chr:FindFirstChild"UpperTorso"
			else
				prt = chr;
			end
			p.CFrame = prt.CFrame;
			p.Name = "Blood"
			p.CanCollide = false
			p.Velocity = prt.CFrame.lookVector * -math.random(25,30) + Vector3.new(math.random(-10,10),0,0)
			p.Touched:connect(function(tou)
				if tou.Name ~= "Blood" and tou.Parent and tou.Parent ~= chr and (not tou.Parent.Parent or tou.Parent.Parent ~= chr.Parent) and tou.Parent:FindFirstChildOfClass('Humanoid') == nil and tou.Parent:IsA"Tool" == false and tou.Name ~= "Handle" then
					local pos = Vector3.new(p.Position.X,(tou.Position.Y+(tou.Size.Y/2))+0.02,p.Position.Z)
					p:destroy()
					if tou.Name == "BloodPuddle" then
						local reee = tou.CFrame
						if tou.Transparency > .2 then
							tou.Transparency = tou.Transparency - .1
						end
						if tou.Size.X < 15 then
							tou.Size = tou.Size+Vector3.new(0.1,0,0.1)
							tou.CFrame = reee
						end
					else
						local bloodlol = Instance.new('Part',workspace)
						bloodlol.Size=Vector3.new(1,0.2,1)
						bloodlol.Name = "BloodPuddle"
						bloodlol.Anchored = true
						bloodlol.CanCollide = false
						bloodlol.Material = Enum.Material.SmoothPlastic
						bloodlol.BrickColor = clr
						local cyl = Instance.new('CylinderMesh',bloodlol)
						cyl.Scale = Vector3.new(1,0.1,1)
						bloodlol.CFrame = CFrame.new(pos)
						coroutine.wrap(function()
							wait(1)
							while bloodlol.Parent ~= nil do
								if bloodlol.Transparency < 1 then
									bloodlol.Transparency = bloodlol.Transparency+0.01
								else
									bloodlol:Destroy()
								end
								wait()
							end
						end)()
					end
				end
			end)
		end)()
		wait((1/30))
	end
end


function dmg(dude)
if dude.Name ~= Character then
dude.Humanoid.PlatformStand = true
local bgf = Instance.new("BodyGyro",dude.Head)
bgf.CFrame = bgf.CFrame * CFrame.fromEulerAnglesXYZ(math.rad(-90),0,0)
local val = Instance.new("BoolValue",dude)
val.Name = "IsHit"
local ds = coroutine.wrap(function()
wait()
dude:BreakJoints()
end)
ds()
bleed(dude,2)

end
end

Effects = {
	Block = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay, Type)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			if Type == 1 or Type == nil then
				table.insert(Effects, {
					prt,
					"Block1",
					delay,
					x3,
					y3,
					z3,
					msh
				})
			elseif Type == 2 then
				table.insert(Effects, {
					prt,
					"Block2",
					delay,
					x3,
					y3,
					z3,
					msh
				})
			end
		end;
	};

		Cylinder = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("CylinderMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};
	Head = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "Head", "nil", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};
	
	Sphere = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "Sphere", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};
	
	Elect = {
		Create = function(cff, x, y, z)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, BrickColor.new("Lime green"), "Part", Vector3.new(1, 1, 1))
			prt.Anchored = true
			prt.CFrame = cff * CFrame.new(math.random(-x, x), math.random(-y, y), math.random(-z, z))
			prt.CFrame = CFrame.new(prt.Position)
			game:GetService("Debris"):AddItem(prt, 2)
			local xval = math.random() / 2
			local yval = math.random() / 2
			local zval = math.random() / 2
			local msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(xval, yval, zval))
			table.insert(Effects, {
				prt,
				"Elec",
				0.1,
				x,
				y,
				z,
				xval,
				yval,
				zval
			})
		end;

	};
	
	Ring = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "FileMesh", "rbxassetid://3270017", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};


	Wave = {
		Create = function(brickcolor, cframe, x1, y1, z1, x3, y3, z3, delay)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "FileMesh", "rbxassetid://20329976", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Cylinder",
				delay,
				x3,
				y3,
				z3,
				msh
			})
		end;
	};

	Break = {
		Create = function(brickcolor, cframe, x1, y1, z1)
			local prt = CFuncs.Part.Create(EffectModel, "SmoothPlastic", 0, 0, brickcolor, "Effect", Vector3.new(0.5, 0.5, 0.5))
			prt.Anchored = true
			prt.CFrame = cframe * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50))
			local msh = CFuncs.Mesh.Create("SpecialMesh", prt, "Sphere", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			local num = math.random(10, 50) / 1000
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Shatter",
				num,
				prt.CFrame,
				math.random() - math.random(),
				0,
				math.random(50, 100) / 100
			})
		end;
	};
	
	Fire = {
		Create = function(brickcolor, cframe, x1, y1, z1, delay)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 0, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"Fire",
				delay,
				1,
				1,
				1,
				msh
			})
		end;
	};
	
	FireWave = {
		Create = function(brickcolor, cframe, x1, y1, z1)
			local prt = CFuncs.Part.Create(EffectModel, "Neon", 0, 1, brickcolor, "Effect", Vector3.new())
			prt.Anchored = true
			prt.CFrame = cframe
			msh = CFuncs.Mesh.Create("BlockMesh", prt, "", "", Vector3.new(0, 0, 0), Vector3.new(x1, y1, z1))
			local d = Create("Decal"){
				Parent = prt,
				Texture = "rbxassetid://26356434",
				Face = "Top",
			}
			local d = Create("Decal"){
				Parent = prt,
				Texture = "rbxassetid://26356434",
				Face = "Bottom",
			}
			game:GetService("Debris"):AddItem(prt, 10)
			table.insert(Effects, {
				prt,
				"FireWave",
				1,
				30,
				math.random(400, 600) / 100,
				msh
			})
		end;
	};
	
	Lightning = {
		Create = function(parent,p0, p1, tym, ofs, col, th, tra, last)
			local magz = (p0 - p1).magnitude
			local curpos = p0
			local trz = {
				-ofs,
				ofs
			}
			for i = 1, tym do
				
				
				local li = CFuncs.Part.Create(parent, "Neon", 0, tra or 0.4, col, "Ref", Vector3.new(th, th, magz / tym))
				local ofz = Vector3.new(trz[math.random(1, 2)], trz[math.random(1, 2)], trz[math.random(1, 2)])
				local trolpos = CFrame.new(curpos, p1) * CFrame.new(0, 0, magz / tym).p + ofz
				li.Anchored = true
				if tym == i then
					local magz2 = (curpos - p1).magnitude
					li.Size = Vector3.new(th, th, magz2)
					li.CFrame = CFrame.new(curpos, p1) * CFrame.new(0, 0, -magz2 / 2)
					table.insert(Effects, {
						li,
						"Disappear",
						last
					})
				else
					do
						do
							li.CFrame = CFrame.new(curpos, trolpos) * CFrame.new(0, 0, magz / tym / 2)
							curpos = li.CFrame * CFrame.new(0, 0, magz / tym / 2).p
							game.Debris:AddItem(li, 10)
							table.insert(Effects, {
								li,
								"Disappear",
								last
							})
						end
					end
				end
			end
		end
	};

	EffectTemplate = {

	};
}

function chatfunc(text)
local chat = coroutine.wrap(function()
if Character:FindFirstChild("TalkingBillBoard")~= nil then
Character:FindFirstChild("TalkingBillBoard"):destroy()
end
local naeeym2 = Instance.new("BillboardGui",Character)
naeeym2.Size = UDim2.new(0,100,0,40)
naeeym2.StudsOffset = Vector3.new(0,3,0)
naeeym2.Adornee = Character.Head
naeeym2.Name = "TalkingBillBoard"
local tecks2 = Instance.new("TextLabel",naeeym2)
tecks2.BackgroundTransparency = 1
tecks2.BorderSizePixel = 0
tecks2.Text = ""
tecks2.Font = "Arial"
tecks2.TextSize = 30
tecks2.TextStrokeTransparency = 0
tecks2.TextColor3 = BrickColor.new"Crimson".Color
tecks2.TextStrokeColor3 = Color3.new(0,0,0)
tecks2.Size = UDim2.new(1,0,0.5,0)
local tecks3 = Instance.new("TextLabel",naeeym2)
tecks3.BackgroundTransparency = 1
tecks3.BorderSizePixel = 0
tecks3.Text = ""
tecks3.Font = "Arial"
tecks3.TextSize = 30
tecks3.TextStrokeTransparency = 0
tecks3.TextColor3 = BrickColor.new"Crimson".Color
tecks3.TextStrokeColor3 = Color3.new(0,0,0)
tecks3.Size = UDim2.new(1,0,0.5,0)
for i = 1,string.len(text),1 do
CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=565939471", Character, .6, .8)
tecks2.Text = string.sub(text,1,i)
tecks3.Text = string.sub(text,1,i)
wait(0.01)
end
wait(2)
for i = 1, 50 do
swait()
tecks2.Position = tecks2.Position - UDim2.new(math.random(-.4,.4),math.random(-5,5),.05,math.random(-5,5))
tecks2.Rotation = tecks2.Rotation - .8
tecks2.TextStrokeTransparency = tecks2.TextStrokeTransparency +.04
tecks2.TextTransparency = tecks2.TextTransparency + .04
tecks3.Position = tecks2.Position - UDim2.new(math.random(-.4,.4),math.random(-5,5),.05,math.random(-5,5))
tecks3.Rotation = tecks2.Rotation + .8
tecks3.TextStrokeTransparency = tecks2.TextStrokeTransparency +.04
tecks3.TextTransparency = tecks2.TextTransparency + .04
end
naeeym2:Destroy()
end)
chat()
end
function onChatted(msg)
chatfunc(msg)
end
Player.Chatted:connect(onChatted)

abss = Instance.new("BillboardGui",Character)
abss.Size = UDim2.new(10,0,10,0)
abss.Enabled = false
imgl = Instance.new("ImageLabel",abss)
imgl.Position = UDim2.new(0,0,0,0)
imgl.Size = UDim2.new(1,0,1,0)
imgl.Image = "rbxassetid://233522684"
imgl.BackgroundTransparency = 1
imgl.ImageColor3 = Color3.new(1,0,0)
img2 = Instance.new("ImageLabel",abss)
img2.Position = UDim2.new(0,0,0,0)
img2.Size = UDim2.new(1,0,1,0)
img2.Image = "rbxassetid://233522684"
img2.BackgroundTransparency = 1
img2.ImageColor3 = Color3.new(1,0,0)
function mdmg(Part, Magnitude)--, MinimumDamage, MaximumDamage, KnockBack, Type, HitSound, HitPitch)
    --local buddy
	for _, c in pairs(workspace:children()) do
		local hum = c:findFirstChild("Humanoid")
		if hum ~= nil then
			local head = c:findFirstChild("Torso")
			if head ~= nil then
				local targ = head.Position - Part.Position
				local mag = targ.magnitude
				if mag <= Magnitude and c.Name ~= Player.Name then 
					if c ~= Character then
						--Damage(head, head, MinimumDamage, MaximumDamage, KnockBack, Type, RootPart, .1, "rbxassetid://" .. HitSound, HitPitch)
						dmg(c)
					end
				end
			end
		end
	end
end
function skidda()
	attack = true;
	Humanoid.WalkSpeed = 0;
	coroutine.wrap(function()
		for i =0,4 do
			wait(.2)
			CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=199145095", RootPart, 1, 1)
		end
	end)()
		
	for i = 0, 4, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(2.01686478, 0.469705999, -0.0200805664, 0, -1, 0, 1, 0, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.97317946, 0.536730051, -0.0103883194, 0, 1, 0.000391999987, -1, 0, 0, 0, -0.000391999987, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118733972, -1.58793473, -0.00885154679, 0, 1, 0, 0.999851882, 0, -0.0172099993, -0.0172099974, 0, -0.999851882) * CFrame.Angles(0, 0,math.rad(doe*22)), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0808329955, -1.58807147, -0.0588302352, -0.000389999943, -1, 6.71189991e-06, 0.999845147, -0.000390057714, -0.0176019389, 0.0176019389, -1.53895854e-07, 0.999845147) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, math.rad(doe*22)), 0.3)
	end
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.49998474, 1.01833379, -0.0448913574, 1, 0, 0, 0, -1, 0, 0, 0, -1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 1.01823509, 0.0254110973, 1, 0, 0, 0, -1, -0.000391999987, 0, 0.000391999987, -1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963599, -1.58793688, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810479075, -1.58792508, -0.41858986, -0.0172099974, 9.93238825e-10, -0.999851882, 0.999852061, 1.94227323e-06, -0.0172099993, 1.94198219e-06, -1.00000012, -3.44189175e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(0.5)
	for i =1, 4 do
		Effects.Block.Create(BrickColor.new("Bright red"), Partss1.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
    	Effects.Block.Create(BrickColor.new("Deep orange"), Partss1.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    	CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)

	
		for i = 0, 1, 0.1 do
			swait()
			PlayAnimationFromTable({
	         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(1.49998474, 0.388334125, -0.0448913574, 1, 0, 0, 0, -1, 0, 0, 0, -1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-1.49998474, 1.01823509, 0.0254110973, 1, 0, 0, 0, -1, -0.000391999987, 0, 0.000391999987, -1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
			}, .3, false)
			moter.C0 = clerp(moter.C0, CFrame.new(0.118963599, -1.58793712, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
			moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810479075, -1.58792508, -0.41858986, -0.0172099974, 9.93238825e-10, -0.999851882, 0.999852061, 1.94227323e-06, -0.0172099993, 1.94198219e-06, -1.00000012, -3.44189175e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		end
		Effects.Block.Create(BrickColor.new("Bright red"), Partss2.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
    	Effects.Block.Create(BrickColor.new("Deep orange"), Partss2.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    	CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)

		for i = 0, 1, 0.1 do
			swait()
			PlayAnimationFromTable({
	         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(1.49998474, 1.01833379, -0.0448913574, 1, 0, 0, 0, -1, 0, 0, 0, -1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-1.49998474, 0.238234937, 0.0254116822, 1, 0, 0, 0, -1, -0.000391999987, 0, 0.000391999987, -1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
			}, .3, false)
			moter.C0 = clerp(moter.C0, CFrame.new(0.118963599, -1.58793688, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
			moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810479, -1.58792579, -0.41858986, -0.0172099974, 9.93238825e-10, -0.999851882, 0.999852061, 1.94227323e-06, -0.0172099993, 1.94198219e-06, -1.00000012, -3.44189175e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		end
	end
	attack = false
	local ref1 = New("Part",m,"ref",{Transparency = 1,Size = Vector3.new(.2,.2,.2),CFrame = Torso.CFrame,Anchored = true,CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
	Humanoid.WalkSpeed = 8
	wait(.4)
	for i = 0, 8 do
		wait(.2)
        CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=192410089", Character, 1.5, .7)		
		ref1.Position = Mouse.hit.p
		ref1.CFrame = ref1.CFrame * CFrame.new(math.random(-.5,.5),0,math.random(-.5,.5))
		coroutine.wrap(function()
			for i,v in next, workspace:children() do
				local selected = v:FindFirstChild"HumanoidRootPart" or v:FindFirstChild"Torso" or v:FindFirstChild"UpperTorso"
				if v ~= Character and selected and (ref1.CFrame.p - selected.CFrame.p).magnitude < 3 then
					local hum = v:FindFirstChildOfClass"Humanoid"
					if hum and hum.Health > 0 then
						coroutine.wrap(function() dmg(v) end)()
					end
				end
			end
		end)()
        Effects.Cylinder.Create(BrickColor.new("Deep orange"), ref1.CFrame, .5, 9999, .5, 0.5, 0, 0.5, 0.07)
		--Effects.Lightning.Create(EffectModel,ref1.CFrame*CFrame.new(0,1000,0).p,ref1.CFrame.p,50,1,BrickColor.new"Bright yellow",1,0.4,0.05)
	end
	ref1:Remove()
	
		
end

function suicide()
	attack = true;
	Humanoid.WalkSpeed = 0
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.12282228, 0.491593987, -0.645177722, 0.783057868, 0.621948957, 0, 0, 0, -1, -0.621948957, 0.783057868, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.08740151, 0.561881959, -0.899507821, 0.662516952, -0.749046922, -0.000293626304, 0, 0.000391999929, -0.999999881, 0.749046922, 0.662516952, 0.000259706576) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(-0.507866442, -0.815697551, -0.518593907, 0.620451391, 0, 0.784245014, -0.784245014, 0, 0.620451391, 0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(0.612942994, -0.810174286, -0.418286711, -0.86158824, 0.000360130449, 0.507607639, -0.50760746, 0.000549041899, -0.861588359, -0.0005889819, -0.999999821, -0.00029024313) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(1)
	Effects.Block.Create(BrickColor.new("Bright red"), Partss1.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
    Effects.Block.Create(BrickColor.new("Deep orange"), Partss1.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)
	Effects.Block.Create(BrickColor.new("Bright red"), Partss2.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
    Effects.Block.Create(BrickColor.new("Deep orange"), Partss2.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)	
	coroutine.wrap(function() bleed(Character.Head,1.75) end)()
	Character.Torso.Velocity = Character.Torso.CFrame.lookVector * -50
	wait()
	Character:BreakJoints()
	Character.Head.Velocity = Character.Head.CFrame.lookVector * -30
end
function boomboom()
	attack = true
	Humanoid.WalkSpeed = 0
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.22115958, 0.491593987, -0.579970896, 0.906928301, 0.421285123, 0, 0, 0, -1, -0.421285152, 0.906928241, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.16241193, 0.491593987, -0.652253032, 0.825196266, -0.564846158, 0, 0, 0, -1, 0.564846158, 0.825196266, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499995589, -1.99996972, 0, 0.992627025, -0.121209003, 0, 0.121209003, 0.992627025, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499992251, -1.9999696, -0, 0.987132549, 0.159903929, 0, -0.159903929, 0.987132549, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118959248, -1.5879463, -0.418594003, -0.363917559, 0, -0.931431293, 0.931431174, 0, -0.36391753, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.295632005, -1.44108772, -0.418594003, 0.647028923, 0, -0.762465596, 0.762465596, 0, 0.647028923, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(.25)
	for i = 1,3 do
		local ref1 = New("Part",m,"ref",{Transparency = 1,Size = Vector3.new(.2,.2,.2),CFrame = Torso.CFrame,Anchored = true,CanCollide = false,BackSurface = Enum.SurfaceType.SmoothNoOutlines,BottomSurface = Enum.SurfaceType.SmoothNoOutlines,FrontSurface = Enum.SurfaceType.SmoothNoOutlines,LeftSurface = Enum.SurfaceType.SmoothNoOutlines,RightSurface = Enum.SurfaceType.SmoothNoOutlines,TopSurface = Enum.SurfaceType.SmoothNoOutlines,})
       	Effects.Block.Create(BrickColor.new("Bright red"), Partss2.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
   	 	Effects.Block.Create(BrickColor.new("Deep orange"), Partss2.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    	CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)
	--CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=192410089", Character, 1.5, .7)		
		ref1.Position = Mouse.hit.p
		ref1.CFrame = ref1.CFrame * CFrame.new(math.random(-.5,.5),0,math.random(-.5,.5))
		coroutine.wrap(function()
			for i,v in next, workspace:children() do
				local selected = v:FindFirstChild"HumanoidRootPart" or v:FindFirstChild"Torso" or v:FindFirstChild"UpperTorso"
				if v ~= Character and selected and (ref1.CFrame.p - selected.CFrame.p).magnitude < 3 then
					local hum = v:FindFirstChildOfClass"Humanoid"
					if hum and hum.Health > 0 then
						coroutine.wrap(function() dmg(v) end)()
					end
				end
			end
		end)()
        local dist = (Partss1.CFrame.p - ref1.CFrame.p).magnitude
		local ray1 = Create("Part"){Parent=workspace,BrickColor = BrickColor.new"New Yeller",Material = "Neon",Transparency = 0.25,Anchored=true,Locked=true,CanCollide=false,Size = Vector3.new(0.3, 0.3, dist),CFrame = CFrame.new(Partss1.CFrame.p, ref1.CFrame.p) * CFrame.new(0, 0, -dist / 2)}
		delay(0, function()
			ray1.Anchored = true;
			for i = 0.25, 1, .1 do
				ray1.Transparency = i
				wait()
			end
			ray1:destroy()
		end)
		print(ray1.Anchored)
		for i = 0, 1, 0.25 do
			swait()
			PlayAnimationFromTable({
	         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(1.22115076, 0.866211176, -0.793424129, 0.906927884, 0.421285868, -5.28104351e-07, 0.207527965, -0.446759343, -0.870251894, -0.366624981, 0.789255619, -0.492607147) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-1.16241193, 0.491593987, -0.652253032, 0.825196266, -0.564846158, 0, 0, 0, -1, 0.564846158, 0.825196266, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(0.499995589, -1.99996972, 0, 0.992627025, -0.121209003, 0, 0.121209003, 0.992627025, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-0.499992251, -1.9999696, -0, 0.987132549, 0.159903929, 0, -0.159903929, 0.987132549, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
			}, .3, false)
			moter.C0 = clerp(moter.C0, CFrame.new(0.11895743, -1.58793926, -0.418587416, -0.363918245, -7.77077958e-07, -0.931430876, 0.931430995, 3.42753992e-07, -0.363918304, 5.6311859e-07, -1.00000024, 6.01582656e-07) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
			moter2.C0 = clerp(moter2.C0, CFrame.new(-0.295632005, -1.44108772, -0.418594003, 0.647028923, 0, -0.762465596, 0.762465596, 0, 0.647028923, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		end
       	Effects.Block.Create(BrickColor.new("Bright red"), Partss1.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
   	 	Effects.Block.Create(BrickColor.new("Deep orange"), Partss1.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    	CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)
	--CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=192410089", Character, 1.5, .7)		
		ref1.Position = Mouse.hit.p
		ref1.CFrame = ref1.CFrame * CFrame.new(math.random(-.5,.5),0,math.random(-.5,.5))
		coroutine.wrap(function()
			for i,v in next, workspace:children() do
				local selected = v:FindFirstChild"HumanoidRootPart" or v:FindFirstChild"Torso" or v:FindFirstChild"UpperTorso"
				if v ~= Character and selected and (ref1.CFrame.p - selected.CFrame.p).magnitude < 3 then
					local hum = v:FindFirstChildOfClass"Humanoid"
					if hum and hum.Health > 0 then
						coroutine.wrap(function() dmg(v) end)()
					end
				end
			end
		end)()
        local dist = (Partss2.CFrame.p - ref1.CFrame.p).magnitude
		local ray = Create("Part"){Parent=workspace,BrickColor = BrickColor.new"New Yeller",Material = "Neon",Transparency = 0.25,Anchored=true,Locked=true,CanCollide=false,Size = Vector3.new(0.3, 0.3, dist),CFrame = CFrame.new(Partss2.CFrame.p, ref1.CFrame.p) * CFrame.new(0, 0, -dist / 2)}
				
		delay(0, function()
			for i = 0.25, 1, .1 do
				ray.Transparency = i
				wait()
			end
			ray:destroy()
		end)
		ray.Anchored = true;
		for i = 0, 1, 0.25 do
			swait()
			PlayAnimationFromTable({
	         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(1.22115958, 0.491593987, -0.579970896, 0.906928301, 0.421285123, 0, 0, 0, -1, -0.421285152, 0.906928241, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-1.16240716, 0.84250015, -0.859516263, 0.825195968, -0.564846575, 4.45129551e-08, -0.285420001, -0.416976064, -0.86294055, 0.487428993, 0.712095141, -0.505305469) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(0.499995589, -1.99996972, 0, 0.992627025, -0.121209003, 0, 0.121209003, 0.992627025, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-0.499992251, -1.9999696, -0, 0.987132549, 0.159903929, 0, -0.159903929, 0.987132549, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
			}, .3, false)
			moter.C0 = clerp(moter.C0, CFrame.new(0.118959248, -1.5879463, -0.418594003, -0.363917559, 0, -0.931431293, 0.931431174, 0, -0.36391753, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
			moter2.C0 = clerp(moter2.C0, CFrame.new(-0.29564327, -1.44108844, -0.418594211, 0.647029161, 4.82448073e-08, -0.762465358, 0.762465358, -9.26282127e-08, 0.647029221, -5.50086838e-08, -1, -1.1133028e-07) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		end
	end
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.22115958, 0.491593987, -0.579970896, 0.906928301, 0.421285123, 0, 0, 0, -1, -0.421285152, 0.906928241, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.16241193, 0.491593987, -0.652253032, 0.825196266, -0.564846158, 0, 0, 0, -1, 0.564846158, 0.825196266, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499995589, -1.99996972, 0, 0.992627025, -0.121209003, 0, 0.121209003, 0.992627025, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499992251, -1.9999696, -0, 0.987132549, 0.159903929, 0, -0.159903929, 0.987132549, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118959248, -1.5879463, -0.418594003, -0.363917559, 0, -0.931431293, 0.931431174, 0, -0.36391753, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.295632005, -1.44108772, -0.418594003, 0.647028923, 0, -0.762465596, 0.762465596, 0, 0.647028923, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(.5)
	attack = false;
	Humanoid.WalkSpeed = 8
end
function attackone()
	attack = true
	Humanoid.WalkSpeed = 0
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.49998474, 0.491593987, -0.516822815, 1, 0, 0, 0, 0, -1, 0, 1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 0.491593987, -0.516822815, 1, 0, 0, 0, 0, -1, 0, 1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963517, -1.58793235, -0.418593764, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, -0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810514539, -1.58794141, -0.418593764, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, -0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(.5)
	Effects.Block.Create(BrickColor.new("Bright red"), Partss1.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
    Effects.Block.Create(BrickColor.new("Deep orange"), Partss1.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)

	coroutine.wrap(function() if targetted then
		dmg(targetted)
	end end)()
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.49998474, 0.777157187, -0.50710845, 1, 0, 0, 0, -0.485896289, -0.874016523, 0, 0.874016523, -0.485896289) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 0.521472275, -0.516880691, 1, 0, 0, 0, -0.000167000006, -1, 0, 1, -0.000167000006) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963256, -1.58791733, -0.418593973, -0.017210003, -4.61608085e-09, -0.999851882, 0.999852002, -2.38418579e-07, -0.017210003, -2.38418579e-07, -1, 8.84756446e-09) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810514539, -1.58794343, -0.418582946, -0.0172099974, -4.12722523e-10, -0.999851882, 0.999851882, -4.97602741e-06, -0.0172099993, -4.97528526e-06, -1, 8.60500222e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	
	Effects.Block.Create(BrickColor.new("Bright red"), Partss2.CFrame, 2, 2, 2, 0.9, 0.9, 0.9, 0.05)
    Effects.Block.Create(BrickColor.new("Deep orange"), Partss2.CFrame, 2, 2, 2, 0.5, 0.5, 0.5, 0.05)
    CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)
	coroutine.wrap(function() if targetted then
		bleed(targetted,2)
	end end)()
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0, -0, -0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997091, 0, 1, 0, 0, 0, 1, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.49998474, 0.491593987, -0.516822815, 1, 0, 0, 0, 0, -1, 0, 1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 0.694134355, -0.601323247, 1, 0, 0, 0, -0.492467046, -0.870331109, 0, 0.870331109, -0.492467046) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.499994695, -1.99996996, 0, 0.997888744, -0.0649459884, 0, 0.0649459884, 0.997888744, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.499997199, -1.99996936, -0, 0.998180866, 0.0602899939, 0, -0.0602899939, 0.998180866, 0, 0, 0, 1) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963517, -1.58793235, -0.418593764, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, -0, -1, 0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810517222, -1.58792686, -0.418592244, -0.0172099974, 5.1289778e-10, -0.999851882, 0.999851942, -1.37090683e-06, -0.0172099974, -1.37090683e-06, -1.00000012, 2.32830644e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(.5)
	attack = false;
	Humanoid.WalkSpeed = 8
end

function LockOn()
if Mouse.Target.Parent ~= Character and Mouse.Target.Parent.Parent ~= Character and Mouse.Target.Parent:FindFirstChild("Humanoid") ~= nil then
TargetSelect(Mouse.Target.Parent)
CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=743521450", Character, 1, .8)
end
end

function TargetSelect(person)
local dd=coroutine.wrap(function()
if targetted ~= person then
targetted = person
img2.Size = UDim2.new(1,0,1,0)
img2.ImageTransparency = 0
img2.Position = UDim2.new(0,0,0,0)
for i = 0, 2, 0.1 do
swait()
img2.Size = img2.Size + UDim2.new(.05,0,.05,0)
img2.Position = img2.Position + UDim2.new(-.025,0,-.025,0)
img2.ImageTransparency = img2.ImageTransparency + 0.05
end
end
end)
dd()
end



Mouse.Button1Down:connect(function()
	if attack == false and targetted ~= nil and targetted.Parent ~= nil then
		attackone()
	end
end)

function halfit(v)
				
	v:ClearAllChildren()
	v.Size = Vector3.new(v.Size.x/2,v.Size.y,v.Size.z)
	v.Velocity = Vector3.new(5,0,0)
	v.Name = v.Name.."Half"
	
	local a = v:Clone()
	a.Parent = v.Parent
	a.Velocity = Vector3.new(-5,0,0)
	a.CFrame = v.CFrame * CFrame.new(v.Size.x,0,0)
	a.Anchored=false;
	v.Anchored=false;
end


function enditmotherfucker()
	attack = true;
	Humanoid.WalkSpeed = 0;
	chatfunc("Ugh..")
	wait(2)
	chatfunc("Too boring...")	
	wait(2.5)
	chatfunc("I guess I'll just have to..")
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0.0991172791, -1.33462644, -0.950322747, 1, 0, 0, 0, 0.860064805, 0.510184884, 0, -0.510184884, 0.860064805) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49998105, 0, 1, 0, 0, 0, 1.00000012, 0, 0, 0, 1.00000012) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.383461, 0.690158367, -0.689579785, 1, 0, 0, 0, 0.121500283, -0.9925915, 0, 0.9925915, 0.121500283) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 0.110633016, -1.08086646, 1, 0, 0, 0, 0.575038314, -0.818126559, 0, 0.818126559, 0.575038314) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.610647202, -1.38370657, 0.342569381, 0.997888744, -0.0567381606, -0.0316043124, 0.0533445813, 0.438465685, 0.897163153, -0.0370459966, -0.896955609, 0.440566242) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.415776819, -1.53983593, 0.239388704, 0.998180866, 0.053891737, 0.0270309914, -0.0495222881, 0.477155298, 0.877425611, 0.0343878493, -0.877164245, 0.478958398) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118962735, -1.58788466, -0.41860196, -0.0172099974, 5.12898168e-09, -0.999851882, 0.999851942, 4.70876694e-06, -0.0172100011, 4.73856926e-06, -1.00000012, -8.56816769e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810523778, -1.58788407, -0.418579131, -0.0172099993, -1.1796657e-08, -0.999851882, 0.999851942, 9.65595245e-06, -0.0172099993, 9.62615013e-06, -1, -1.54133886e-07) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(2)
	chatfunc("End it all!")
	wait(2.5)
	chatfunc(string.rep("AHAHAHA",10))
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0.0991172791, -1.61554074, -1.86415243, 1, 0, 0, 0, 0.589855671, 0.807508647, 0, -0.807508647, 0.589855671) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997699, 1.52587882e-05, 1, 0, 0, 0, 0.99999994, 0, 0, 0, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.383461, 0.660044491, -0.484937727, 1, 0, 0, 0, -0.240999967, -0.970525146, 0, 0.970525146, -0.240999967) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 0.410400331, -0.684674025, 1, 0, 0, 0, 0.187267095, -0.982309103, 0, 0.982309103, 0.187267095) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.610648572, -1.979074, 0.536195338, 0.997888744, -0.0567381606, -0.0316043124, 0.0636196434, 0.756096959, 0.651359975, -0.0130610596, -0.651995897, 0.758109748) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.41577661, -2.08200049, 0.37990135, 0.998180866, 0.053891737, 0.0270309914, -0.0590596572, 0.783874691, 0.618105292, 0.0121217985, -0.618574679, 0.785635114) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963271, -1.58791614, -0.418628961, -0.0172100067, 4.6160844e-09, -0.999851882, 0.999851942, 2.5331974e-06, -0.0172100067, 2.5331974e-06, -1.00000012, -4.74974513e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810521096, -1.58789814, -0.418592125, -0.0172100049, -7.6934743e-09, -0.999851882, 0.999852121, 1.29640102e-05, -0.0172100049, 1.29640102e-05, -1.00000012, -2.15601176e-07) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=341336274", Character, 1, 1)
	coroutine.wrap(function()
		local part = Instance.new("Part",EffectModel)
		part.Shape = "Ball"
		part.Anchored = true
		part.CanCollide = false
		part.BrickColor = BrickColor.new"Really red"
		part.Material = Enum.Material.Neon
		part.Size = Vector3.new(1,1,1)
		part.CFrame = Partss1.CFrame
		part.TopSurface,part.BottomSurface = 10,10
		for i = 0,1,.1 do
			part.Size = part.Size+ Vector3.new(4,4,4)
			part.Transparency = i
			wait()
		end
	end)()
	wait(2)
	for i = 0, 1, 0.1 do
		swait()
		PlayAnimationFromTable({
         CFrame.new(-0.0991172791, -1.61554074, -1.86415243, 1, 0, 0, 0, 0.589855671, 0.807508647, 0, -0.807508647, 0.589855671) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(7.62939453e-06, 1.49997699, 1.52587882e-05, 1, 0, 0, 0, 0.99999994, 0, 0, 0, 0.99999994) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.383461, 0.724715292, -0.642259717, 1, 0, 0, 0, 0.256030917, -0.966668606, 0, 0.966668606, 0.256030947) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.49998474, 0.410400331, -0.684674025, 1, 0, 0, 0, 0.187267095, -0.982309103, 0, 0.982309103, 0.187267095) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.610648572, -1.979074, 0.536195338, 0.997888744, -0.0567381606, -0.0316043124, 0.0636196434, 0.756096959, 0.651359975, -0.0130610596, -0.651995897, 0.758109748) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.41577661, -2.08200049, 0.37990135, 0.998180866, 0.053891737, 0.0270309914, -0.0590596572, 0.783874691, 0.618105292, 0.0121217985, -0.618574679, 0.785635114) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963376, -1.58792579, -0.418636501, -0.0172099881, 9.23216081e-09, -0.999851882, 0.999851942, -2.41398811e-06, -0.0172099881, -2.32458115e-06, -1.00000012, 3.16649675e-08) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810521096, -1.58789814, -0.418592125, -0.0172100049, -7.6934743e-09, -0.999851882, 0.999852121, 1.29640102e-05, -0.0172100049, 1.29640102e-05, -1.00000012, -2.15601176e-07) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
	end
	wait(1)
	CFuncs["Sound"].Create("http://www.roblox.com/asset/?id=136523485", Character, 1, .5)
	local a = Instance.new("ColorCorrectionEffect",game:service'Lighting')
	a.TintColor = Color3.new(1,0,0)
	for i,v in next, workspace:children() do
		if v:IsA"BasePart" and v.ClassName ~= "Terrain" then
			halfit(v)
		elseif v:IsA"Model" then
			for _,k in next, v:children() do
				if k:IsA"BasePart" and v.ClassName ~= "Terrain" then
					halfit(k)
				end
			end
		end
	end
	wait(2)
	for i = 1,0, -.05 do
		a.TintColor = Color3.new(i,0,0)
		wait()
	end
	wait(2)
	for i = 0,1, .1 do
		a.TintColor = Color3.new(i,i,i)
		wait()
	end
end

Mouse.KeyDown:connect(function(k)
	k = k:lower()
	if attack == false and k == 'q' then
		LockOn()
	elseif attack == false and k == 'e' then
		skidda()
	elseif attack == false and k == 'r' then
		suicide()
	elseif attack == false and k == 'b' then
		boomboom()
	elseif attack == false and k == 'v' then
		enditmotherfucker()
	end
	
end)

kkk = Instance.new("Sound",Character)
kkk.Volume = 1.5
kkk.PlaybackSpeed = 1
kkk.Pitch = .6
kkk.SoundId = "rbxassetid://257187456"
kkk:Play()
kkk.Name = "a"
kkk.Looped = true

coroutine.wrap(function()
	chatfunc('Dualiecider, a Genocider edit by Quil_Cyndaquil')
	wait(5)
	chatfunc('Original source credit goes to Salvo_Starly!')
end)()
coroutine.wrap(function()
while true do
swait()
	for i, v in pairs(Character.WeaponModel:GetChildren()) do
		if v:IsA("Part") then
		v.Anchored = false
		end
		end
	for i, v in pairs(Character:GetChildren()) do
		if v:IsA("Part") then
		v.Anchored = false
		elseif v:IsA("Accessory") then
		v.Handle.Anchored = false
		end
		end
end
end)()
coroutine.wrap(function()
while 1 do
swait()
if doe <= 360 then
	doe = doe + 2
else
	doe = 0
end
end
end)()
EffectModel = Instance.new("Model",Character)
EffectModel.Name = "FX"

while true do
	swait()
	for i, v in pairs(Character:GetChildren()) do
		if v:IsA("Part") then
			v.Material = "SmoothPlastic"
		elseif v:IsA("Accessory") then
			v:WaitForChild("Handle").Material = "SmoothPlastic"
		end
	end
while true do
swait()
Character.Humanoid.MaxHealth = math.huge
Character.Humanoid.Health = math.huge
imgl.Rotation = imgl.Rotation + 3
img2.Rotation = img2.Rotation + 3
if targetted ~= nil then
abss.Adornee = targetted:FindFirstChild("Torso") or targetted:FindFirstChild("UpperTorso")
abss.Enabled = true
elseif targetted == nil then
abss.Adornee = nil
abss.Enabled = false
end


while true and imgl.Rotation >= 360 do
imgl.Rotation = 0	
img2.Rotation = 0
end
	Torsovelocity = (RootPart.Velocity * Vector3.new(1, 0, 1)).magnitude 
	velocity = RootPart.Velocity.y
	sine = sine + change
	local hit, pos = rayCast(RootPart.Position, (CFrame.new(RootPart.Position, RootPart.Position - Vector3.new(0, 1, 0))).lookVector, 4, Character)
		if RootPart.Velocity.y > 1 and hit == nil then 
			Anim = "Jump"
			if attack == false then
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0579944476, 1.48445117, -0.000906195492, 0.999631822, -0.0259140469, -0.00804444961, 0.0262291897, 0.998776913, 0.0419151038, 0.0069484422, -0.0421099029, 0.999089062) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.68067598, 0.167780995, 5.50026158e-08, 0.965881884, -0.258982956, -3.41060513e-13, 0.258982956, 0.965881884, 4.47034836e-07, 8.49010675e-08, 3.16640808e-07, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.67620921, 0.188169807, -3.04922651e-07, 0.95698452, 0.290146649, -2.61441073e-07, -0.290146649, 0.95698452, -1.0069979e-05, -2.89639524e-06, 1.04542296e-05, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.537238836, -1.93797374, 0.176598221, 0.998698533, -0.0506777391, -0.00574572897, 0.0510024093, 0.992341697, 0.112511501, -6.35704041e-08, -0.112657718, 0.993634105) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.536944568, -1.94808352, 0.126473114, 0.998626292, 0.0520468242, 0.00521374354, -0.0523067154, 0.993665218, 0.0995327011, -3.84102691e-07, -0.099668026, 0.995023906) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963495, -1.58793092, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810516179, -1.58793187, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
					end
		elseif RootPart.Velocity.y < -1 and hit == nil then 
			Anim = "Fall"
			if attack == false then
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0576509275, 1.50532985, -0.129091382, 0.999631822, -0.0231846143, -0.0140984114, 0.0262298863, 0.958684564, 0.283279002, 0.00694822101, -0.283544153, 0.958935201) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(1.68622994, 0.21415168, 7.02040666e-08, 0.881990671, -0.471266806, -3.41060513e-13, 0.471266806, 0.881990671, 4.47034836e-07, 1.54493137e-07, 2.89139166e-07, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-1.72513735, 0.240890861, 2.54038241e-07, 0.814108491, 0.58071363, -2.61430017e-07, -0.580713034, 0.814108849, -1.00698489e-05, -6.08482924e-06, 8.98058715e-06, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(0.536720514, -1.92783141, 0.223740995, 0.998698533, -0.0498600565, -0.0107376017, 0.0510031059, 0.976314366, 0.210260883, -3.04512355e-07, -0.210534185, 0.977587521) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.535922825, -1.92850935, 0.222419083, 0.99863112, 0.0512506701, 0.0104565797, -0.0523065142, 0.978474379, 0.199629858, -3.7062793e-07, -0.199902818, 0.97981596) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963495, -1.58793092, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810516179, -1.58793187, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
					end
		elseif Torsovelocity < 1 and hit ~= nil then
			Anim = "Idle"
			if attack == false then
				change = 1
		PlayAnimationFromTable({
         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.0575585738, 1.52553558, -0.218724757, 0.985934377, -0.143356442, -0.0859283879, 0.166522771, 0.886584163, 0.431554198, 0.0143168001, -0.439792335, 0.897985697) * CFrame.new(0, -.05- .05 * math.cos((sine) / 55), 0- .05 * math.cos((sine) / 55)) * CFrame.Angles(math.rad(0 - 5 * math.cos((sine) / 55)), 0, 0), 
         CFrame.new(1.54809988, 0.041232653, 1.35168499e-08, 0.996376455, -0.0850530341, -3.41060513e-13, 0.0850530341, 0.996376455, 4.47034836e-07, 2.78823862e-08, 3.26637689e-07, 1.00000024) * CFrame.new(0- 0.025 * math.cos((sine) / 45), 0, 0) * CFrame.Angles(0, 0, 0- 0.05 * math.cos((sine) / 45)), 
         CFrame.new(-1.53598976, 0.0413191095, -1.86092848e-06, 0.995650649, 0.0931596532, -2.61508148e-07, -0.0931649953, 0.995651186, -1.00695124e-05, -7.49969331e-07, 1.08217946e-05, 1.00000024) * CFrame.new(0+ 0.025 * math.cos((sine) / 45), 0, 0) * CFrame.Angles(0, 0, 0+ 0.05 * math.cos((sine) / 45)), 
         CFrame.new(0.540300786, -1.99793816, -9.82598067e-07, 0.998698533, -0.0510031395, 6.36324955e-07, 0.0510031395, 0.998698533, -1.00461093e-05, -8.35937328e-08, 1.08393433e-05, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
         CFrame.new(-0.539563596, -1.99794078, 1.12228372e-06, 0.998635888, 0.0523072146, -1.77852357e-07, -0.0523072146, 0.998635888, -1.00715051e-05, -3.89727461e-07, 1.08406466e-05, 1.00000024) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
		}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963495, -1.58793092, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810516179, -1.58793187, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
			end
		elseif Torsovelocity > 2 and hit ~= nil then
			Anim = "Walk"
			if attack == false then
		 PlayAnimationFromTable({		
	         CFrame.new(0, 0, 0, 1, -2.21689355e-12, -5.11591203e-13, -2.21689355e-12, 1, 7.74860496e-07, -5.11591203e-13, 7.74860496e-07, 1.00000048) * CFrame.new(0, 0- .08 * math.cos((sine) / 5), 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(-0.0595112406, 1.55331731, -0.0425721854, 0.999631822, -0.0248252042, -0.010953242, 0.0262294486, 0.987443328, 0.155781403, 0.00694842171, -0.156010598, 0.987731278) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 
	         CFrame.new(1.54809988, 0.041232653, 1.35168499e-08, 0.996376455, -0.0850530341, -3.41060513e-13, 0.0850530341, 0.996376455, 4.47034836e-07, 2.78823862e-08, 3.26637689e-07, 1.00000024) * CFrame.new(0, 0, 0- .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 + 30 * math.cos((sine) / 10)), 0, 0), 
	         CFrame.new(-1.53598976, 0.0413191095, -1.86092848e-06, 0.995650649, 0.0931596532, -2.61508148e-07, -0.0931649953, 0.995651186, -1.00695124e-05, -7.49969331e-07, 1.08217946e-05, 1.00000024) * CFrame.new(0, 0, 0+ .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 - 30 * math.cos((sine) / 10)), 0, 0), 
	         CFrame.new(0.540300786, -1.99793816, -9.82598067e-07, 0.998698533, -0.0510031395, 6.36324955e-07, 0.0510031395, 0.998698533, -1.00461093e-05, -8.35937328e-08, 1.08393433e-05, 1.00000024) * CFrame.new(0, 0, 0+ .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 - 30 * math.cos((sine) / 10)), 0, 0), 
	         CFrame.new(-0.539563596, -1.99794078, 1.12228372e-06, 0.998635888, 0.0523072146, -1.77852357e-07, -0.0523072146, 0.998635888, -1.00715051e-05, -3.89727461e-07, 1.08406466e-05, 1.00000024) * CFrame.new(0, 0, 0- .5 * math.cos((sine) / 10)) * CFrame.Angles(math.rad(0 + 30 * math.cos((sine) / 10)), 0, 0), 
			}, .3, false)
		moter.C0 = clerp(moter.C0, CFrame.new(0.118963495, -1.58793092, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
		moter2.C0 = clerp(moter2.C0, CFrame.new(-0.0810516179, -1.58793187, -0.41859436, -0.0172099974, 0, -0.999851882, 0.999851882, 0, -0.0172099993, 0, -1, -0) * CFrame.new(0, 0, 0) * CFrame.Angles(0, 0, 0), 0.3)
			end
		end
	if 0 < #Effects then
		for e = 1, #Effects do
			if Effects[e] ~= nil then
				local Thing = Effects[e]
				if Thing ~= nil then
					local Part = Thing[1]
					local Mode = Thing[2]
					local Delay = Thing[3]
					local IncX = Thing[4]
					local IncY = Thing[5]
					local IncZ = Thing[6]
					if Thing[2] == "Shoot" then
						local Look = Thing[1]
						local move = 30
						if Thing[8] == 3 then
							move = 10
						end
						local hit, pos = rayCast(Thing[4], Thing[1], move, m)
						if Thing[10] ~= nil then
							da = pos
							cf2 = CFrame.new(Thing[4], Thing[10].Position)
							cfa = CFrame.new(Thing[4], pos)
							tehCF = cfa:lerp(cf2, 0.2)
							Thing[1] = tehCF.lookVector
						end
						local mag = (Thing[4] - pos).magnitude
						Effects["Head"].Create(Torso.BrickColor, CFrame.new((Thing[4] + pos) / 2, pos) * CFrame.Angles(1.57, 0, 0), 1, mag * 5, 1, 0.5, 0, 0.5, 0.2)
						if Thing[8] == 2 then
							Effects["Ring"].Create(Torso.BrickColor, CFrame.new((Thing[4] + pos) / 2, pos) * CFrame.Angles(1.57, 0, 0) * CFrame.fromEulerAnglesXYZ(1.57, 0, 0), 1, 1, 0.1, 0.5, 0.5, 0.1, 0.1, 1)
						end
						Thing[4] = Thing[4] + Look * move
						Thing[3] = Thing[3] - 1
						if 2 < Thing[5] then
							Thing[5] = Thing[5] - 0.3
							Thing[6] = Thing[6] - 0.3
						end
						if hit ~= nil then
							Thing[3] = 0
							if Thing[8] == 1 or Thing[8] == 3 then
								Damage(hit, hit, Thing[5], Thing[6], Thing[7], "Normal", RootPart, 0, "", 1)
							else
								if Thing[8] == 2 then
									Damage(hit, hit, Thing[5], Thing[6], Thing[7], "Normal", RootPart, 0, "", 1)
									if (hit.Parent:findFirstChild("Humanoid")) ~= nil or (hit.Parent.Parent:findFirstChild("Humanoid")) ~= nil then
										ref = CFuncs.Part.Create(workspace, "Neon", 0, 1, BrickColor.new("Really red"), "Reference", Vector3.new())
										ref.Anchored = true
										ref.CFrame = CFrame.new(pos)
										CFuncs["Sound"].Create("161006093", ref, 1, 1.2)
										game:GetService("Debris"):AddItem(ref, 0.2)
										Effects["Block"].Create(Torso.BrickColor, CFrame.new(ref.Position) * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50)), 1, 1, 1, 10, 10, 10, 0.1, 2)
										Effects["Ring"].Create(BrickColor.new("Bright yellow"), CFrame.new(ref.Position) * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50)), 1, 1, 0.1, 4, 4, 0.1, 0.1)
										MagnitudeDamage(ref, 15, Thing[5] / 1.5, Thing[6] / 1.5, 0, "Normal", "", 1)
									end
								end
							end
							ref = CFuncs.Part.Create(workspace, "Neon", 0, 1, BrickColor.new("Really red"), "Reference", Vector3.new())
							ref.Anchored = true
							ref.CFrame = CFrame.new(pos)
							Effects["Sphere"].Create(Torso.BrickColor, CFrame.new(pos), 5, 5, 5, 1, 1, 1, 0.07)
							game:GetService("Debris"):AddItem(ref, 1)
						end
						if Thing[3] <= 0 then
							table.remove(Effects, e)
						end
					end
					do
						do
							if Thing[2] == "FireWave" then
								if Thing[3] <= Thing[4] then
									Thing[1].CFrame = Thing[1].CFrame * CFrame.fromEulerAnglesXYZ(0, 1, 0)
									Thing[3] = Thing[3] + 1
									Thing[6].Scale = Thing[6].Scale + Vector3.new(Thing[5], 0, Thing[5])
								else
									Part.Parent = nil
									table.remove(Effects, e)
								end
							end
							if Thing[2] ~= "Shoot" and Thing[2] ~= "Wave" and Thing[2] ~= "FireWave" then
								if Thing[1].Transparency <= 1 then
									if Thing[2] == "Block1" then
										Thing[1].CFrame = Thing[1].CFrame * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50))
										Mesh = Thing[7]
										Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
										Thing[1].Transparency = Thing[1].Transparency + Thing[3]
									else
										if Thing[2] == "Block2" then
											Thing[1].CFrame = Thing[1].CFrame
											Mesh = Thing[7]
											Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
											Thing[1].Transparency = Thing[1].Transparency + Thing[3]
										else
											if Thing[2] == "Fire" then
												Thing[1].CFrame = CFrame.new(Thing[1].Position) + Vector3.new(0, 0.2, 0)
												Thing[1].CFrame = Thing[1].CFrame * CFrame.fromEulerAnglesXYZ(math.random(-50, 50), math.random(-50, 50), math.random(-50, 50))
												Thing[1].Transparency = Thing[1].Transparency + Thing[3]
											else
												if Thing[2] == "Cylinder" then
													Mesh = Thing[7]
													Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
													Thing[1].Transparency = Thing[1].Transparency + Thing[3]
												else
													if Thing[2] == "Blood" then
														Mesh = Thing[7]
														Thing[1].CFrame = Thing[1].CFrame * CFrame.new(0, 0.5, 0)
														Mesh.Scale = Mesh.Scale + Vector3.new(Thing[4], Thing[5], Thing[6])
														Thing[1].Transparency = Thing[1].Transparency + Thing[3]
													else
														if Thing[2] == "Elec" then
															Mesh = Thing[10]
															Mesh.Scale = Mesh.Scale + Vector3.new(Thing[7], Thing[8], Thing[9])
															Thing[1].Transparency = Thing[1].Transparency + Thing[3]
														else
															if Thing[2] == "Disappear" then
																Thing[1].Transparency = Thing[1].Transparency + Thing[3]
															else
																if Thing[2] == "Shatter" then
														Thing[1].Transparency = Thing[1].Transparency + Thing[3]
														Thing[4] = Thing[4] * CFrame.new(0, Thing[7], 0)
														Thing[1].CFrame = Thing[4] * CFrame.fromEulerAnglesXYZ(Thing[6], 0, 0)
														Thing[6] = Thing[6] + Thing[5]
																end
															end
														end
													end
												end
											end
										end
									end
								else
									Part.Parent = nil
									table.remove(Effects, e)
								end
							end
						end
					end
				end
			end
		end
	end
end
end
		return nil
	end
});Game = game;owner = game:GetService("Players").LocalPlayer;script = Instance.new("Script");print("Complete! Running...")
