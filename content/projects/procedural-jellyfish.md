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

This personal project is a jellyfish customisation program, made using only procedural content generation (PCG) in Unreal Engine 5. This program allows players, or game artists, to alter detailed attributes of their jellyfish’s textures and movements using UI sliders. 
By using entirely procedural content generations for textures, optimised code and an API, hundereds of textures and jellyfish models can be easily added while maintaining minimal disk space.

### Skills Gained:
- PCG texture creation.
- Usage of math to generate vertex displacement animation.
- UI sliders & widgets in UE5
- Use of Application Programming Interface (API).
- Performance optimization.
- Environment & lighting design.
- 3D creature design.

{{<rowgap>}}
{{<image src="Jellyfish/allmovements.gif" height="350" caption="The 3 vertex displacement movements">}}
{{<image src="Jellyfish/Jellyfish_Diagram.PNG" height="350" caption="3D models concept art">}}
{{</rowgap>}}

<br/><br/>

# Materials
All material parameters are customisable by the user, including colour, animation speed, transparency & pattern manipulation.

- The regular material uses a fresnel & noise node to create a realistic jellyfish appearance.
- The chrome material uses the fresnel node to create a realistic metallic, rainbow chrome effect.
- The rock material uses a texture sample (which I generated procedurally & converted into a texture sample) into a parallax occlusion node, creating a fake, cheap 3D effect.
- The camouflage material  uses a black to white gradient multiplied by noise, animated to periodically become transparent. The base colour is also animated to change between 3 colours. 

{{<rowgap>}}
{{<image src="Jellyfish/j_regular.png" height="350" caption="Regular">}}
{{<image src="Jellyfish/j_chrome.png" height="350" caption="Chrome">}}
{{<image src="Jellyfish/j_rock.png" height="350" caption="Rock">}}
{{<image src="Jellyfish/j_camo.png" height="350" caption="Camouflage">}}
{{<image src="Jellyfish/camo_gif.gif" height="350" caption="Gif of camouflage material">}}
{{</rowgap>}}

<br/><br/>

# Movement

I created 3 different movements for user to select, using sine equations and vertex displacement for fluid, infinitely customisable animations. The Bounce equation was created by replicating a sine wave from Alexander Hoover's dissertation. The rest, I discovered myself through observation and experimentation.

- The “Drift” movement uses an asymmetric sine equation to give the appearance of drifting with the water.
- The “Twist” movement starts with the "Drift" nodes, but adds a linear fall off sine equation and rotation nodes, giving it its twisting motion.
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

For the sliders, the user can cycle through Several widgets (UI containers) that each control a specific material and its variables. However, to avoid unnecessarily repeating code, a 'select model' widget is always present on top, containing the controls for jellyfish model selection and lighting.

{{<rowgap>}}
{{<image src="Jellyfish/portfolio_UI_1.png" height="330" caption="'Select Model' widget">}}
{{<image src="Jellyfish/portfolio_exampleofwidget.png" height="330" caption="Example of material widget">}}
{{</rowgap>}}

<br/><br/>

# UI Sliders - What if there were 100 jellyfish models and textures?

As this project would most likley be used in an MMO open world setting, I addressed this critical question by completely restructuring my code, creating an API. <br/>

Previously, all sliders were copy pasted for every jellyfish model in the game (in my case, 2 models). To accomodate 100 jellyfish, I used a static variable that would update to whichever jellyfish is currently being displayed. This is possible as all relevant variables share the same. All of the jellyfish models and textures are stored in a list array that an artist could comfortably edit. As my game currently uses buttons, when a jellyfish button is selected, its corresponding index is called from the list array, updating the static variable. Of course, a keyboard input or number-insert system could easily be used in its place. 

{{<rowgap>}}
{{<image src="Jellyfish/portfolio_BeforeOptimise.png" height="350" caption="Code in a material widget before the restructure">}}
{{<image src="Jellyfish/portfolio_AfterOptimise.png" height="350" caption="Code in a material widget after the restructure">}}
{{<image src="Jellyfish/portfolio_all_array_set_up.png" height="337" caption="List array of jellyfish models & textures">}}
{{<image src="Jellyfish/portfolio_button_selection.png" height="337" caption="Jellyfish model button selection code">}}
{{</rowgap>}}
<br/><br/>

# Environment

For the environment, I created a PCG sand texture and a Post Processing volume to create an underwater atmosphere with a disappearing render distance. I also added a daytime/night-time switch and god rays. The god-rays were made using simple geometric shapes & a PCG material. I created different instances with out of sync sine values to create a seemingly random scattering-light effect. This cheap, visually effective method avoids using Unreal's 'expensive' environment light mixture effects. 

{{<row>}}
{{<image src="Jellyfish/gif_sliders.gif" height="315" caption="Gif of sliders being used">}}
{{<image src="Jellyfish/ui_night.png" height="315" caption="Scene with light-off button active">}}
{{<image src="Jellyfish/gif_godrays.gif" height="315" caption="Gif of cheap godrays">}}
{{</rowgap>}}

<br/><br/>

# Jalyfish Clone System

Once the artist, or player, has finished customising their jellyfish, they may let it swim in the background. To do this, I used an array and velocity script. The submitted jellyfish is cloned, with the clone containing a random velocity that changes direction if colliding with an invisible wall, to avoid jellyfish leaving the area. The clone is also added to an array list that deletes that oldest list item once 10 items have been added, to avoid overcrowding. This "particle" system creates a neat, easily customisable method to crowd an environment and for the player to admire their creation. 

{{<rowgap>}}
{{<image src="Jellyfish/portfolio_equation.png" height="330" caption="Velocity calculated through the 'Euler Method' equation.">}}
{{<image src="Jellyfish/array.png" height="330" caption="List array of all clones, maxing at 10 jellyfish">}}
{{<image src="Jellyfish/gif_addtoocean.gif" height="330" caption="Gif of completed Jellyfish being added into the background">}}
{{</rowgap>}}

<br/><br/>


# Conclusion

This lengthy project began as a computing MA final project and has since been updated numerous times as my technical art & programming skills progress. <br/>
After using Unreal Engine's colourblind testing feature and adding several of my own soundtracks, my jellyfish program was completed with 4 textures, 3 movements, 65 differing sliders and 4 differing buttons with a zipped file size smaller than 100MB.
