---
title: Procedural Jellyfish
video: /img/Jellyfish/frontvid_jelly.webm
weight: 1
tags:
  - Technical Art
  - Programming
  - UI Design
  - 3D/2D Art
  - Technical Art Mobile Games
  - Game Design
  - Technical Animation

summary: Detailed jellyfish customisation game, made using only procedural content generation to optimize performance in Unreal Engine 5.

links:
    - name: Gameplay video
      url: https://www.youtube.com/watch?v=s03iVL0zItw
---

<br/><br/>

<iframe width="600" height="338" src="https://www.youtube.com/embed/s03iVL0zItw" frameborder="0" allowfullscreen></iframe>

# Procedural Content Generation - Jellyfish Customisation

In gaming, 3D character and creature models often focus on familiar archetypes like humanoids and dragons, leaving intriguing designs like jellyfish largely underrepresented. Their diverse textures and fluid, sine-wave movements make jellyfish ideal candidates for Procedural Content Generation (PCG).

The initial aim of this project was to create a jellyfish customization game using UI sliders for real-time adjustments. As development progressed, the project evolved to include multiple updates that enhance technical efficiency, such as an API for streamlined asset management and an array of jellyfish clones to populate the environment. These features not only optimize performance but also enable a rich variety of jellyfish while minimizing file size and resource usage, showcasing the powerful capabilities of PCG in game development.

### Skills Gained:
- PCG texture creation.
- Usage of math to generate vertex displacement animation.
- UI sliders & widgets in UE5
- Use of Application Programming Interface (API).
- Performance optimization.
- Environment & lighting design.
- 3D creature design.

{{<rowgap>}}
{{<image src="Jellyfish/realjf.gif" height="350" caption="The sea Nettle jellyfish">}}
{{<image src="Jellyfish/realjf2gif.gif" height="350" caption="The portuguese man o' war jellyfish">}}
{{<image src="Jellyfish/Jellyfish_Diagram.PNG" height="350" caption="3D models concept art inspired from the jellyfish above">}}
{{</rowgap>}}

<br/><br/>

# Materials
In developing the jellyfish textures, I focused on enhancing my expertise with material nodes (specifcially, 
learning the 'Parallax occlusion Mapping' and 'Fresnel' nodes) and exploring advanced techniques for generating 
unique visual effects. My objectives included creating a realistic jellyfish texture that captures its characteristic 
transparency, along with more striking and visually appealing options designed to attract players, such as the camouflage material, 
inspired by the mimic octopus.

{{<rowgap>}}
{{<image src="Jellyfish/moonjelly.jpg" height="300" caption="Most common jellyfish texture">}}
{{<image src="Jellyfish/chrome.jpg" height="300" caption="Example of chrome metal">}}
{{<image src="Jellyfish/octopus.gif" height="300" caption="The mimic octopus">}}
{{</rowgap>}}

<br/><br/>

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

With numerous unique customizable variables, such as color, animation speed, transparency, and pattern manipulation, my effective and optimised use of PCG textures allow for multiple jellyfish variations with minimal disk space usage.

<br/><br/>

# Movement

Jellyfish move in flowing, sine-like motions, making vertex displacement—a branch of PCG—ideal for capturing this behaviour. 
This technique enables organic, fluid movements while minimising disk space. Therefore, I created 3 different animations using 
this method. <br/><br>

- The “Drift” movement aims to replicate the man o' war jellyfish. The equation uses an asymmetric sine equation to give the appearance 
of drifting with the water.

{{<row>}}
{{<image src="Jellyfish/asymetrical.png" height="225" caption="Asymetrical sine wave">}}
{{<image src="Jellyfish/nodes_drift.PNG" height="225" caption="Sine nodes producing drift">}}
{{<image src="Jellyfish/gif_drift.gif" height="225" caption="Gif of 'Drift' effect">}}
{{</row>}}

<br>

- The “Twist” movement was developed through creative exploration and experimentation. Starting with the "Drift" nodes, I added a 
linear fall off sine equation and rotation nodes, giving it its twisting motion.

{{<row>}}
{{<image src="Jellyfish/linearfalloff.png" height="225" caption="Reverse linear fall off sine wave">}}
{{<image src="Jellyfish/nodes_twist2.png" height="225" caption="Rotation nodes">}}
{{<image src="Jellyfish/gif_twist.gif" height="225" caption="Gif of 'Twist' effect">}}
{{</row>}}

<br>

- The final “Bounce” movement aimed to replicate the sea nettle jellyfish. Starting by replicating a sine wave from Alexander 
Hoover's dissertation, I added an absolute wave to create a propelling motion. I then used a tapering function to remove an artefact, 
as well as removing unwanted harshness from the absolute values.

{{<row>}}
{{<image src="Jellyfish/essay.png" height="255" caption="Screenshot from Hoover's essay, showing jellyfish propultion & sine wave motion">}}
{{</row>}}

<br>

{{<row>}}
{{<image src="Jellyfish/absolute.png" height="225" caption="Absolute sine wave">}}
{{<image src="Jellyfish/tapering.png" height="225" caption="Tapering function">}}
{{<image src="Jellyfish/nodes_bounce.png" height="225" caption="Sine nodes producing bounce">}}
{{<image src="Jellyfish/gif_bounce.gif" height="225" caption="Gif of 'Bounce' effect">}}
{{</row>}}

<br>

{{<row>}}
{{<image src="Jellyfish/allmovements.gif" height="360" caption="The final 3 vertex displacement movements">}}
{{</row>}}

By leveraging multiple sine equations and advanced mathematical methods, I created numerous animation variations 
with customizable parameters, allowing for a multitude of unique possible outcomes.

<br/><br/>

# Profiling & Optimization

An experienced technical artist recommended that I improve my equations, and through GPU profiling, I found that a 
populated scene with these equations was indeed impacting performance. By consolidating all calculations into a single sine 
equation, I successfully optimized my movement blueprints. While the unoptimized equations had only a slight effect on frame 
rates, this practice is crucial for maintaining sustained performance in larger-scale games.

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

# UI Sliders - What if there were 100 jellyfish models and textures?

During an interview, I was challenged with a crucial question: how could my code accommodate 100 jellyfish models for an MMO open-world 
setting? At that time, my approach relied on copy-pasting code for each jellyfish (in my case, 2 models), which was neither efficient 
nor scalable. Therefore, I set out to completely restructure my codebase. <br/>

For the sliders, users can cycle through several widgets, each controlling specific materials and their variables. Initially, I 
repeated code for the light switch and buttons within each widget. To eliminate this redundancy, I added a separate "select model" 
widget that remains fixed on top, consolidating all controls for jellyfish model selection and lighting. <br/>

{{<rowgap>}}
{{<image src="Jellyfish/portfolio_UI_1.png" height="330" caption="'Select Model' widget">}}
{{<image src="Jellyfish/portfolio_exampleofwidget.png" height="330" caption="Example of material widget">}}
{{</rowgap>}}

<br/>

To accomodate 100 jellyfish, I used a static variable that would update to whichever jellyfish is currently being displayed. This is 
possible as all relevant variables share the same name. All of the jellyfish models and textures are stored in a list array 
that an artist could comfortably edit. As my game currently uses buttons, when a jellyfish button is selected, its corresponding 
index is called from the list array, updating the static variable. Of course, a keyboard input or number-insert system could easily 
be used in its place. 

{{<rowgap>}}
{{<image src="Jellyfish/portfolio_BeforeOptimise.png" height="350" caption="Code in a material widget before the restructure">}}
{{<image src="Jellyfish/portfolio_AfterOptimise.png" height="350" caption="Code in a material widget after the restructure">}}
{{<image src="Jellyfish/portfolio_all_array_set_up.png" height="337" caption="List array of jellyfish models & textures">}}
{{<image src="Jellyfish/portfolio_button_selection.png" height="337" caption="Jellyfish model button selection code">}}
{{</rowgap>}}
<br/><br/>

This newer method allows the user to instantiate multiple, unique jellyfish with much fewer lines of code. 
This improvement not only streamlined the implementation process but also significantly improved performance, allowing for 
a cheap, intuitive method to populate an environment.

# Environment

In developing the environment for the jellyfish, I aimed to create a underwater atmosphere that would compliment the jellyfish models &
 MMO scenario

I created a PCG sand texture and a Post Processing volume (PPV) to create an underwater atmosphere with animated sand rays and a 
disappearing render distance. I also added a daytime/night-time switch to better view emissive customisation options. 
Finally, I created god rays; they were made using simple geometric shapes & a PCG material. I created different instances with out 
of sync sine values to create a seemingly random scattering-light effect.

{{<row>}}
{{<image src="Jellyfish/gif_sliders.gif" height="315" caption="Gif of sliders being used">}}
{{<image src="Jellyfish/ui_night.png" height="315" caption="Scene with light-off button active">}}
{{<image src="Jellyfish/gif_godrays.gif" height="315" caption="Gif of cheap godrays">}}
{{</rowgap>}}

The sand texture and PPV enhance the environment while cleverly masking the small loaded area, conserving disk
 space. Meanwhile, the god rays provide a visually effective and cost-effective alternative to Unreal's more expensive
  environment light mixture effects.

<br/><br/>

# Jellyfish Clone System


As mentioned, users can populate their environment with custom jellyfish. I included this feature to showcase how artists 
could utilize my project to fill a space with NPCs or allow players to save their personalized jellyfish creations.

To do this, I used an array and velocity script. The submitted jellyfish is cloned, with the clone containing a random velocity that 
changes direction if colliding with an invisible wall, to avoid jellyfish leaving the area. The clone is also added to an 
array list that deletes that oldest list item once 10 items have been added, to avoid overcrowding. This 
creates an intuitive, easily editable set up for an artist to use or for a player, of any specs, to admire their creations. 

{{<rowgap>}}
{{<image src="Jellyfish/portfolio_equation.png" height="330" caption="Velocity calculated through the 'Euler Method' equation.">}}
{{<image src="Jellyfish/array.png" height="330" caption="List array of all clones, maxing at 10 jellyfish">}}
{{<image src="Jellyfish/gif_addtoocean.gif" height="330" caption="Gif of completed Jellyfish being added into the background">}}
{{</rowgap>}}

<br/><br/>


# Conclusion

This extensive project began as my final project for a computing MA and has since undergone numerous updates as my technical 
art and programming skills have evolved. After utilizing Unreal Engine's colorblind testing feature and adding several original 
soundtracks, my jellyfish program was complete. With optimized movement equations, an API for jellyfish models and textures, 
an enhanced environment, numerous stored materials & movements all within a zipped file size of 
under 100MB, I take great pride in this project as it demonstrates essential skills in both programming and technical art.
