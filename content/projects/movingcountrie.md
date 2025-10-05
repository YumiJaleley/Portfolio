---
title: Moving Countries - Unity Video Game
youtube: fYaEYadzhTg
weight: 5
tags:
  - UI Programming
  - VFX Artist
  - Programming
  - Technical Art Mobile Games
  - UI Design
  - Game Design
  - Technical Animation

summary: Multiple ending, silent narrative video game. Made using 2D animation in photoshop and C# code in Unity.

links:
    - name: Gameplay video
      url: https://www.youtube.com/watch?v=fYaEYadzhTg
    - name: Play the game
      url: https://yumi-jaleley.itch.io/moving-countries
---

This video game is based on my personal experience of moving countries as a child. It focuses on delivering a narrative without the use of any words.

### Skills gained:
- Unity animation & asset implementation.
- C# cheap sine equation movement.
- Game design to enhance narrative.
- UI/UX design.

{{<row>}}
{{<image src="movingcountries/conceptart_me.png" height="275" caption="Concept art of main character">}}
{{<image src="movingcountries/conceptart_teacher.png" height="275" caption="Concept art of teacher character">}}
{{</row>}}


<br/><br/>

# Home Town & New School Scenes

Moving countries is a silent narrative game with 2 different endings depending on player performance. 
It has 4 scenes: the home country scene, the new school schene, the classroom scene and the report card scene. 
The home country scene has an interractable NPC that kicks a ball and talks back to the player.
The new school scene has interractable NPCs that make fun of the player or talk amicably with them. This depends on the player actions, which include kicking the NPCs.

{{<rowgap>}}
{{<image src="movingcountries/homescene.png" height="360" caption="Home town scene">}}
{{<image src="movingcountries/npc_talking.png" height="360" caption="NPC talking and kicking the ball back to the player">}}
{{<image src="movingcountries/newschool.png" height="370" caption="New school scene">}}
{{<image src="movingcountries/making_fun_of_Player.png" height="370" caption="NPCs making fun of the player">}}
{{</rowgap>}}

<br/><br/>

# Classroom & Report Card Scene

The classroom scene involves a minigame in which the player must manouver the flower to avoid the moving letters. The letters will continuously increase in speed for 1 minute. If the player’s healthbar does not drop to 0, they will get a good grade, otherwise they will get a bad one.
The controles for the minigame are not revealed until the end of the game. This is to mimic the frustrating feeling of trying to write in an unkown language which is only learned at a later age, hence, the revealed controles at the end. <br/>
The report card scene reveals the player’s grade along with comments on their actions (e.g kicking the NPCs). The minigame controls or a secret message will then be revealed, depending on the player’s performance.

{{<rowgap>}}
{{<image src="movingcountries/classroom.png" height="350" caption="Classroom scene">}}
{{<image src="movingcountries/grade_bad.png" height="350" caption="Bad grade report card">}}
{{<image src="movingcountries/grade_good.png" height="368" caption="Good grade report card">}}
{{<image src="movingcountries/end_controles.png" height="368" caption="Controles reveal">}}
{{</rowgap>}}

<br/><br/>

# Code

For the NPC interractions, Courutines and trigger boxes were used to check player proximity and reply at the correct time, as well as booleans to check player behaviour.
For the various animations, I used Unity’s statemachine animations, using speed floats and other booleans to switch between animations. 
The ball object in the hometown scene checks how many times the player has kicked the ball, switching scenes on the last kick.

{{<rowgap>}}
{{<image src="movingcountries/code_1.png" height="410" caption="Home town NPC script controlling speech bubbles">}}
{{<image src="movingcountries/code_2.png" height="410" caption="New School NPC script checkin player behaviour">}}
{{<image src="movingcountries/code_3.png" height="350" caption="Player script controlling animation variables">}}
{{<image src="movingcountries/code_4.png" height="350" caption="Home town ball object checking kicks to change scenes">}}
{{</rowgap>}}

# Mini-Game Code

The classroom scene minigame was, relativley, the most challenging script.
The mini-game changes sprite’s alpha value to indicate cooldowns and warnings.
The enemy letters, which are obstacles the player must avoid, use a sin equation to move along the y axis, increasing speed every few seconds.

{{<rowgap>}}
{{<image src="movingcountries/code_5.png" height="320" caption="Mini-game flashing warning signal for low health bar">}}
{{<image src="movingcountries/code_6.png" height="405" caption="Mini-game lowering health bar if player hits obstacles">}}
{{<image src="movingcountries/code_7.png" height="360" caption="Mini-game checking healthbar size to determin game over">}}
{{<image src="movingcountries/code_8.png" height="380" caption="Mini-game enemies movement script">}}
{{</rowgap>}}

<br/><br/>

# Conclusion

I was quite pleased with the game’s final result. Its clear-cut code resulted in smooth gameplay that complimented the narrative.
