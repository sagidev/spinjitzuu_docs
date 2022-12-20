<div align="center">
<img src="https://cdn.discordapp.com/attachments/989659099203506267/989659796003233862/watermark.png" alt="spinlogo" width="512">
</div>

## What is this?
spinjitzuu is an External LUA based League of Legends scripting platform with excellent DX11 no-performance loss drawings working on all resolution.

## Core Features
- Undetectability - As platform is fully external, ban chance is almost impossible.
- Ability to write your own scripts in LUA to fullfill your needs.
- DX11 performant GUI and Overlay with not a single FPS lost.


# SDK

## Basic Guide

1. Create a script file with ".lua" extension in "/scripts/" folder

2. Write a [`Update`](#Update) function to execute it each frame. Simple example of writing champion ranges with spinjitzuu.
   ```js
	function Update(Game)
		for id, champion in pairs(Game.champs) do
			if (champion.is_visible and champion.is_alive and champion.health > 0) then
				Game:DrawRange(champion,champion.atk_range, 2)
			end
		end
	end
	```
  
3. Write a [`DrawSettings`](#DrawSettings) function to draw GUI settings.
   ```js
	function DrawSettings(GUI) 
	  drawchamps = GUI:Checkbox("draw champs", drawchamps)
	  keybind = GUI:KeySelect("Orbwalker key", keybind)
   end
   ```
## Inputs
```lua
Game:PressRightClick()
Game:PressLeftClick()
Game:PressKey(int key)
Game:IsKeyDown(int key) [Boolean]
Game:GetCursor() [Vector2]
Game:MoveMouse(int x, int y)
```
## Game
Available Properties:
arrays: {champs, minions, turrets, missiles}
floats: time 

Available Functions:
- GetPlayer()
```lua
Game:GetPlayer()
```

- GetChampionScreenPos(LeagueObject champion) - returns a Vector2 of object's screen position
```lua
screen_pos = Game:GetChampionScreenPos(champion)
```
- IsOnScreen(LeagueObject champion) - returns a boolean
```lua
test = Game:IsOnScreen(champion)
```
- Distance(LeagueObject champion1, LeagueObject champion2) - returns a Vector2
```lua
test = Game:Distance(champion1,champion2)
```
- Randomize(int fromnumber, int tonumber) - returns a Vector2
```lua
test = Game:Randomize(10,20)
```


## Objects

Available Properties:
name, health, max_health, mana, max_mana, base_ad, bonus_ad, atk_range, attack_speed, armor, magic_resist, is_visible, is_alive, is_targetable, pos
```lua
hp = champion.health
position = champion.pos
```

Available Functions:
- GetAttackSpeed(float gametime) - returns real attackspeed with lethaltempo stuff included
```lua
champion:GetAttackSpeed(gametime)
```
- GetSpellCooldown(char spell, float gametime) - returns spells cooldown in seconds
```lua
champion:GetSpellCooldown('Q',gametime)
```
- IsSpellReady(char spell, float gametime) - boolean that returns if spell is ready to use
```lua
champion:IsSpellReady('Q', gametime)
```
- HasBuff(string buffname, float gametime) - boolean that returns if specified buff is active or not
```lua
champion:HasBuff("JinxQ",gametime)
```
- GetBuffCount(string buffname, float gametime) - returns an amount of stacks of desired buff. if buff is not active, then return is 0
```lua
stacks = champion:GetBuffCount("TwitchDeadlyVenom", gametime)
```

## GUI

- Text
```lua
GUI:Text("test")
```
- Button
```lua
if GUI:Button("text")then
end
```
- Separator
```lua
GUI:Separator()
```
- SameLine
```lua
GUI:SameLine()
```
- CheckBox
```lua
bool text = GUI:CheckBox("test", false)
```
- SliderInt
```lua
int value = GUI:SliderInt("test", value, int valMin, int valMax)
```
- SliderFloat
```lua
float value = GUI:SliderFloat("test", value, float valMin, float valMax)
```
- KeySelect
```lua
int key = GUI:KeySelect("test", key)
```

