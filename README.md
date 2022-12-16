# spinjitzuu air
<div align="center">
<img src="https://cdn.discordapp.com/attachments/989659099203506267/989659796003233862/watermark.png" alt="spinlogo" width="512">
</div>
## What is this?
spinjitzuu air is an External LUA based League of Legends scripting platform with excellent DX11 no-performance loss drawings working on all resolution.

## Core Features
- Undetectability - As platform is fully external, ban chance is almost impossible.
- Ability to write your own scripts in LUA to fullfill your needs.
- DX11 performant GUI and Overlay with not a single FPS lost.


# SDK

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
	  drawminions = GUI:Checkbox("draw minions", drawminions)
	  drawturrets = GUI:Checkbox("draw turrets", drawturrets)
	  drawmissiles = GUI:Checkbox("draw missiles", drawmissiles)
   end
   ```

