---
title: Procedural Jellyfish
youtube: s03iVL0zItw
weight: 1
tags:
  - Technical Art
  - Programming
  - UI Programming
  - 3D/2D Art
  - Technical Art Mobile Games
  - Game Design

summary: Detailed jellyfish customisation game, made using only procedural content generation to optimize performance in Unreal Engine 5.

links:
    - name: Gameplay video
      url: https://www.youtube.com/watch?v=s03iVL0zItw
---

# Procedural Content Generation - Jellyfish Customisation

This final MA university project is a jellyfish customisation program, made using only procedural content generation (PCG) in Unreal Engine 5. This program allows players to alter detailed attributes of their jellyfish’s textures and movements using UI sliders. 
By using entirely procedural content generation, this program is optimised for minimal disk space.

### Skills Gained:
- UI sliders & widgets in UE5.
- PCG texture creation.
- Complex vertex displacement animation.
- Performance optimization.
- Environment & lighting design.
- 3D creature design.

{{<rowgap>}}
{{<image src="Jellyfish/allmovements.gif" height="350" caption="The 3 vertex displacement movements">}}
{{<image src="Jellyfish/Jellyfish_Diagram.PNG" height="350" caption="3D models concept art">}}
{{</rowgap>}}

<br/><br/>

# Materials
All material parameters are customisable by the player, including colour, animation speed, transparency & pattern manipulation.

- The regular material uses a fresnel & noise node to create a realistic jellyfish appearance.
- The chrome material uses the fresnel node to create a realistic metallic, rainbow chrome effect.
- The rock material uses a texture sample (which I generated procedurally & converted into a texture sample) into a parallax occlusion node, creating a fake, cheap 3D effect.
- The camouflage material  uses a 
black to white gradient multiplied by noise, animated to periodically become transparent. The base colour is also animated to change between 3 colours. 

{{<rowgap>}}
{{<image src="Jellyfish/j_regular.png" height="350" caption="Regular">}}
{{<image src="Jellyfish/j_chrome.png" height="350" caption="Chrome">}}
{{<image src="Jellyfish/j_rock.png" height="350" caption="Rock">}}
{{<image src="Jellyfish/j_camo.png" height="350" caption="Camouflage">}}
{{<image src="Jellyfish/camo_gif.gif" height="350" caption="Gif of camouflage material">}}
{{</rowgap>}}

<br/><br/>

# Movement

I created 3 different movements for players to select, using sine equations and vertex displacement for fluid, infinitely customisable animations. The Bounce equation was created by replicating a sine wave from Alexander Hoover's dissertation. The rest, I discovered myself through observation and experimentation.

- The “Drift” movement uses an asymmetric sine equation to give the appearance of drifting with the water.
- The “Twist” movement starts with the "Drift" nodes, but adds a linear fall of sine equation and rotation nodes, giving it its twisting motion.
- The final “Bounce” movement uses an absolute wave to create a propelling motion. I then used a tapering function to remove an artefact, as well as removing unwanted harshness from the absolute values.

{{<row>}}
{{<image src="Jellyfish/asymetrical.png" height="225" caption="Asymetrical sine wave">}}
{{<image src="Jellyfish/nodes_drift.PNG" height="225" caption="Sine nodes producing drift">}}
{{<image src="Jellyfish/gif_drift.gif" height="225" caption="Gif of 'Drift' effect">}}
{{</row>}}

<br>

{{<row>}}
{{<image src="Jellyfish/linearfalloff.png" height="225" caption="Reverse linear fall off sine wave">}}
{{<image src="Jellyfish/nodes_twist2.png" height="225" caption="Rotation nodes">}}
{{<image src="Jellyfish/gif_twist.gif" height="225" caption="Gif of 'Twist' effect">}}
{{</row>}}

<br>

{{<row>}}
{{<image src="Jellyfish/absolute.png" height="225" caption="Absolute sine wave">}}
{{<image src="Jellyfish/tapering.png" height="225" caption="Tapering function">}}
{{<image src="Jellyfish/nodes_bounce.png" height="225" caption="Sine nodes producing bounce">}}
{{<image src="Jellyfish/gif_bounce.gif" height="225" caption="Gif of 'Bounce' effect">}}
{{</row>}}

<br/><br/>

# Profiling & Optimization

By using GPU profiling, I discovered that my sine equations were slightly affecting performance. I was able to successfully optimise all of my movement blueprints by drastically simplifying each equation. Although the unoptimized equations only marginally increased frame rate, this good practice would be essential to maintain a larger games' performance at optimal levels.

{{<rowgap>}}
{{<image src="Jellyfish/opt_before.png" height="230" caption="Example of movement equation before optimization">}}
{{<image src="Jellyfish/gpu_bad.png" height="225" caption="GPU profiling before">}}
{{</rowgap>}}

<br/>

{{<rowgap>}}
{{<image src="Jellyfish/opt_after.png" height="225" caption="Example of movement equation after optimization">}}
{{<image src="Jellyfish/gpu_good.png" height="225" caption="GPU profiling after">}}
{{</rowgap>}}

<br/><br/>

# UI Sliders

For the sliders, I created my own work method to maximise code efficiency: by setting up the slider code within each corresponding widget & referencing the 3D models using an array. The resulting code is very clean, organised and efficient.

{{<rowgap>}}
{{<image src="Jellyfish/ui_objectref.png" height="325" caption="Example of slider code in a widget">}}
{{<image src="Jellyfish/ui_slidercode.png" height="325" caption="Example of 3D models reference in a widget">}}
{{</rowgap>}}

# Environment

For the environment, I created a PCG sand texture and a Post Processing volume to create a underwater atmosphere with a disappearing render distance. I also added a daytime/night-time switch and god rays. The god-rays were made using simple geometric shapes & a PCG material. I created different instances with out of sync sine values to create a scattering-light effect. This cheap, visually effective method avoids using Unreal's "expensive" lighting effects. 

I added an option that allows players to add their customised jellyfish into the background, working much like a particle system. To do this, I used an array and velocity script. The submitted jellyfish is cloned, with the clone containing a random velocity that changes direction if colliding with an invisible wall, to avoid jellyfish leaving the visible area. The clone is also added to an array list that deletes that oldest list item once 10 items have been added, to avoid overcrowding. This "particle" system creates a neat, easily customisable method to crowd an environment and for the player to admire their creation. 

{{<row>}}
{{<image src="Jellyfish/ui_gif.gif" height="315" caption="Gif of sliders being used">}}
{{<image src="Jellyfish/ui_night.png" height="315" caption="Scene with light-off button active">}}
{{</rowgap>}}

<br/><br/>

# Conclusion

After using Unreal Engine's colourblind testing feature and adding several of my own soundtrack, my jellyfish program was completed with 4 textures, 3 movements, 65 differing sliders and 4 differing buttons with a zipped file size smaller than 100MB.
