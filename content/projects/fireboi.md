---
title: Fireboi Escapes The Lab - Unity C# Exploration
youtube: Jt1GzJWj9wA
weight: 2
tags:
  - Technical Art
  - Programming
  - Technical Art Mobile Games

summary: Using efficient, cheap and complex C# tools, "Fire Boi Escapes the Lab" is a timed, parkour/puzzle game based on the "Every 10 Seconds" theme.

links:
    - name: Gameplay video
      url: https://www.youtube.com/watch?v=Jt1GzJWj9wA
    - name: Play the game
      url: https://yumi-jaleley.itch.io/fireboi-escapes-the-lab
---

Fireboi Escapes the Lab features a fire alien that needs to escape a flooding lab, using his charged up fireballs to aid him in the process. This project was created for my university coding class, based on the prompt of “Every 10 Seconds”. It serves to demonstrate my skills in gameplay design and C# coding. 

### Skills gained:
- Complex line renderer using physics equations.
- Reusable, expandable shooting mechanic using state machine.
- High accuracy, cheap jump mechanic using raycast
- Cheap animation using Visual Scripting (Bolt).

<br/><br/>

# Aiming Mechanic

The aiming mechanic was, by far, the most challenging part of this project; it ultimately required me to create my own system, refering to physics equations in order to calculate the necesairy variables used in Unity's Line Renderer component. 

This process went through several iterations before arriving at the most efficient one. Recommended by my professor, I began by exploring raycasting, which was inefficient as rays cannot be curved and would therefore require multuple instances for every step of the curve. For my second attempt, I refered to online documentation of parabola generation using Line Renderes. Unfortunately, these were all limited to 2D Vector2. However, the article inspired me to create my own function using a Line Renderer component.

<br/>

{{<rowgap>}}
{{<image src="fireboi/2d.png" height="390" caption="Vector2 equation in 'Basic Trajectory Prediction in Unity' article, Dan Schatzeder">}}
{{<image src="fireboi/2d2.png" height="360" caption="Capture of Unity result from Schatzeder's article">}}
{{</rowgap>}}

<br/><br/>

### 'Point i' variable:

Line Renderer point = (Point i, Position). Where 'Point i' is the specific index of the generated point and 'Position' is the vector3 location of said point. Based on this Line Renderer function, I needed to generate a curved set of points that would then render the connecting line. 

For the 'Point i' variable, I created a loop that would generate each index, stopping at the maximum point: TotalTime/time between points (Aka, 'Step').

<br/>

{{<rowgap>}}
{{<image src="fireboi/linerenderer.PNG" height="50" caption="Main function">}}
{{<image src="fireboi/text.png" height="70" caption="Point i loop equation">}}
{{</rowgap>}}

<br/>

### 'Position' Variable:

The 'Position' variable needed to be calculated through physics. 

As the only forces acting on the bullets are its velocity and gravity, I knew that these were the only two vector3 variables impacting the position of 'Point i' and therefore the only ones to consider. 

{{<rowgap>}}
{{<image src="fireboi/lf_equation1.PNG" height="80" caption="Cumulative vectors">}}
{{<image src="fireboi/lf_equation2.PNG" height="120" caption="Velocity updating position">}}
{{<image src="fireboi/lf_equation3.PNG" height="190" caption="Rendered line from each updated position">}}

{{</rowgap>}}

<br/>

{{<rowgap>}}
{{<image src="fireboi/triangle.png" height="200" caption="Position formula">}}
{{<image src="fireboi/triangle2.png" height="200" caption="Velocity formula">}}

{{</rowgap>}}

As change in position(distance) is = Velocity x Time, I first needed to calculate velocity, which is Acceleration x time. As 'Step' is how much time between each point, this is the variable I would be using (which I made smaller to draw a higher resolution curve). As my only acceleration is gravity and my time between points is 'Step' I knew that I would need to add the following equations to my loop for every point index:





{{<rowgap>}}
{{<image src="fireboi/finalequation.png" height="130" caption="">}}
{{</rowgap>}}

<br/><br/>

### Final outcome of aiming mechanic:

{{<rowgap>}}
{{<image src="fireboi/textfinal.png" height="160" caption="All variables & definitions">}}
{{<image src="fireboi/lf_graph.PNG" height="450" caption="Graph explaining final method & variables">}}
{{</rowgap>}}

For the script itself, I created a 'Draw path' function that contains a loop for each index that updates position & velocity. I also used a variable from my charge state script (explored further on) to make sure the line renderer is pointing in the same direction as the bullet firepoint. The final result is cheap, reusable and accurate. 

<br/><br/>

{{<rowgap>}}
{{<image src="fireboi/code_drawpath1.png" height="430" caption="Draw Path Function - Parabola">}}
{{<image src="fireboi/gif_path.gif" height="310" caption="Gif of draw path outcome">}}
{{</rowgap>}}

<br/><br/>

# Raycasting & Visual Scripting Animation:

Fireboi’s movement was made using a character controller and raycasting. Unity’s Rigidbody “IsGrounded” check often causes unavoidable unwanted collisions, while raycasting's collision system is a cheap alternative that offers more control and is far more reliable. <br/>
For Fireboi's squishing & stretching animation, I used a state machine in Unity's Bolt (Visual scripting) to control Fireboi's stretching animation by reducing and increasing Fire Boi's X & Y scale through a lerp function. This script creates a smooth animation that, unlike a rig animation, can be edited directly in the engine. <br/>


{{<row>}}
{{<image src="fireboi/Code_raycasting.PNG" height="260" caption="Raycast to Check if player is grounded">}}
{{</row>}}

<br/>

{{<rowgap>}}
{{<image src="fireboi/code_jumpstate.PNG" height="310" caption="Squish animation state machine - on jump state">}}
{{<image src="fireboi/gif_squish.gif" height="310" caption="Squish & stretch gif">}}
{{</rowgap>}}

<br/><br/>

# Switch Statments & State Machine Charging Mechanic

For the charging mechanic, I used a switch statement in C# between waiting, aiming and shooting. This efficient shooting mechanic is easily reusable and cheap. This was also linked to Fireboi’s visuals, by reusing the "CurrentCharge" float as the perfect time variable to lerp fireboi's glow & non glow materials.

{{<rowgap>}}
{{<image src="fireboi/Code_switch.png" height="270" caption="Charge state in switch statments">}}
{{<image src="fireboi/code_lerp.PNG" height="190" caption="Lerping materials">}}
{{<image src="fireboi/code_chargedandnot.PNG" height="270" caption="Lerping materials">}}
{{</rowgap>}}

<br/><br/>

# Rising Water Function

To simulate a flooding lab, I created a boolean variable that would become true when Fireboi leaves the starting trigger box, triggering a lerp function that would raise the water level every 10 seconds.
<br/>

{{<rowgap>}}
{{<image src="fireboi/code_waterrise1.PNG" height="350" caption="Player triggering the water rise functoin">}}
{{<image src="fireboi/code_waterrise.PNG" height="350" caption="The water rise function">}}
{{</rowgap>}}

<br/><br/>

# Conclusion

For the majority of the mentioned coding methods, it was my first time implementing them in my own game. Although incredibly challenging, I’ve vastly improved my skills in C# coding as a result. Not only by knowing more coding methods but also in learning how to approach errors. <br/>
The soundtrack used was also made by myself using the App Garageband.

