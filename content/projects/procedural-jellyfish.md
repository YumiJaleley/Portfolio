---
title: Procedural Jellyfish
youtube: cXyxCfFtzfU
weight: 1
tags:
  - Technical Art
  - Programming
  - UI Programming

summary: Detailed jellyfish customisation game, made using only procedural content generation to optimize performance in Unreal Engine 5.

links:
    - name: Gameplay video
      url: https://www.youtube.com/watch?v=cXyxCfFtzfU
---

# Procedural Content Generation - Jellyfish Customisation

This final MA university project is a jellyfish customisation program using only procedural content generation (PCG) in Unreal Engine 5.This program allows players to alter detailed attributes of their jellyfish’s textures and movement using UI sliders. 
By using entirely procedural content generation, this program will be optimized for minimal disk space.

### Skills Gained:
- UI sliders & widgets in UE5.
- PCG texture creation.
- Complex vertex dissplacement animation.
- Performance optimisation.
- Environment & lighting design.
- 3D creature design.

### The 3 vertex displacement movements: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 3D models Concept art:
<img src="img/Jellyfish/allmovements.gif" width="600" height="340" />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="img/Jellyfish/Jellyfish_Diagram.PNG" width="550" height="340" />

<br/><br/>

# Materials
All material parameters are customisable by the player, including colour, animation speed, transparency & pattern manipulation.

- The regular material uses a fresnel & noise node to create a realistic jellyfish appearance.
- The chrome material uses the fresnel node to create a realistic metallic, rainbow chrome effect.
- The rock material uses a texture sample (which I generated procedurally & converted into a texture sample) into a parallax occlusion node, creating a fake, cheap 3D effect.
- The camouflage material  uses a 
black to white gradient multiplied by noise, animated to periodically become transparent. The base colour is also animated to change between 3 colours. 


### Regular &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Chrome &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Rock
<img src="img/Jellyfish/j_regular.png" width="350" height="350" />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="img/Jellyfish/j_chrome.png" width="350" height="350" />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="img/Jellyfish/j_rock.png" width="350" height="350" />

### Camouflage &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Gif of camouflage material:
<img src="img/Jellyfish/j_camo.png" width="350" height="350" />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
<img src="img/Jellyfish/camo_gif.gif" width="670" height="350" />

<br/><br/>

# Movement

I created 3 different movement for players to select, using sine equations and vertex displacement for fluid, infinitely customisable animations. The Bounce equation was created by replicating a sine wave from Alexander Hoover's dissertaion. The rest, I discovered myself through observation and experimentation.

- The “Drift” movement uses an asymmetric sine equation to give the appearance of drifting with the water.
- The “Twist” movement starts with the drift nodes, but adds a linear fall of sine equation and rotation nodes, giving it its twisting motion.
- The final “Bounce” movement uses an absolute wave to create a propelling motion. I then used a tapering function to remove an artefact problem, as well as removing unwanted harshness from the absolute values.

### Asymetrical sine wave: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Sine nodes producing drift: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Gif of "Drift" effect:
<img src="img/Jellyfish/asymetrical.png" width="320" height="225"/>
<img src="img/Jellyfish/nodes_drift.png" width="590" height="225"/>
<img src="img/Jellyfish/gif_drift.gif" width="270" height="225"/>

### Reverse linear fall off sine wave: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Rotation nodes: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Gif of "Twist" effect:
<img src="img/Jellyfish/linearfalloff.png" width="320" height="225"/>
<img src="img/Jellyfish/nodes_twist.png" width="590" height="225"/>
<img src="img/Jellyfish/gif_twist.gif" width="270" height="225"/>

### Absolute & tapering sine waves: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Sine nodes producing bounce: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Gif of "Bounce" effect:
<img src="img/Jellyfish/absolute.png" width="160" height="225"/>
<img src="img/Jellyfish/tapering.png" width="160" height="225"/>
<img src="img/Jellyfish/nodes_bounce.png" width="590" height="225"/>
<img src="img/Jellyfish/gif_bounce.gif" width="270" height="225"/>

<br/><br/>

# Profiling & Optimization

By using GPU profiling, I discovered that my sine equations were slightly affecting performance. I was able to successfully optimise all of my movement blueprints by drastically simplifying each equation. Although marginally increase frame rate in this case, this good practice would be essential to maintain a larger games' performance at optimal levels.

### Example of movement equation before optimization: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; GPU profiling before:
<img src="img/Jellyfish/opt_before.png" width="600" height="225"/>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 
<img src="img/Jellyfish/gpu_bad.png" width="450" height="225"/>

### Example of movement equation after optimization: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; GPU profiling after:
<img src="img/Jellyfish/opt_after.png" width="600" height="225"/>
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 
<img src="img/Jellyfish/gpu_good.png" width="450" height="225"/>

<br/><br/>

# Environment & UI Sliders

For the sliders, I created my own work method to maximise code efficiency: by setting up the slider code within each corresponding widget & referencing the 3D models using an array. The resulting code is very clean, organised and efficient.

For the environment, I created a PCG sand texture and a Post Processing volume to create a underwater atmosphere with a disappearing render distance. I also added a daytime/night-time option.

### Example of slider code in a widget: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Example of 3D models reference in a widget:
<img src="img/Jellyfish/ui_objectref.png" width="580" height="325"/>
<img src="img/Jellyfish/ui_slidercode.png" width="580" height="325"/>

### Gif of sliders being used: &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Scene with light-off button active:
<img src="img/Jellyfish/ui_gif.gif" width="580" height="325"/>
<img src="img/Jellyfish/ui_night.png" width="600" height="325"/>

<br/><br/>

# Conclusion

After using Unreal Engine's colourblind testing feature and adding several of my own soundtrack, my jellyfish program was completed with 4 textures, 3 movements, 65 differing sliders and 4 differing buttons with a zipped file size smaller than 100MB.
