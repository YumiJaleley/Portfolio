---
title: Click to see - Fireboi Escapes The Lab
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
- Complex draw path usage.
- Reusable, expandable shooting mechanic using state machine.
- High accuracy, cheap jump mechanic using raycast
- Cheap animation using Visual Scripting (Bolt).

<br/><br/>

# Fireboi Controls:

Fireboi’s movement was made using a character controller and raycasting. This is a cheap alternative to Unity’s Rigidbody “IsGrounded” check and is far more reliable. <br/>
For Fireboi's squishing & stretching animation, I used a state machine in Unity's Bolt (Visual scripting). <br/>
For the charging mechanic, I used a switch statement in C# between waiting, aiming and shooting. This efficient shooting mechanic is easily reusable and cheap. This was also linked to Fireboi’s visuals, by reusing the "CurrentCharge" float as the perfect time variable to lerp fireboi's glow & non glow materials.

{{<row>}}
{{<image src="fireboi/Code_raycasting.PNG" height="260" caption="Raycast to Check if player is grounded">}}
{{</row>}}

<br/>

{{<rowgap>}}
{{<image src="fireboi/code_jumpstate.PNG" height="310" caption="Squish animation state machine - on jump state">}}
{{<image src="fireboi/gif_squish.gif" height="310" caption="Squish & stretch gif">}}
{{</rowgap>}}

<br/>

{{<rowgap>}}
{{<image src="fireboi/Code_switch.png" height="270" caption="Charge state in switch statments">}}
{{<image src="fireboi/code_lerp.PNG" height="190" caption="Lerping materials">}}
{{<image src="fireboi/code_chargedandnot.PNG" height="270" caption="Lerping materials">}}
{{</rowgap>}}

<br/><br/>

To simulate a flooding lab, I created a boolean variable that would become true when Fireboi leaves the starting trigger box, triggering a lerp function that would raise the water level every 10 seconds.
<br/>
The aiming mechanic was, by far, the most challenging part; It required a draw path function, referencing my charge state code to calculate the curve.

{{<rowgap>}}
{{<image src="fireboi/code_waterrise1.PNG" height="350" caption="Player triggering the water rise functoin">}}
{{<image src="fireboi/code_waterrise.PNG" height="350" caption="The water rise function">}}
{{</rowgap>}}

<br/>

{{<rowgap>}}
{{<image src="fireboi/code_drawpath1.png" height="430" caption="Draw Path Function - Parabola">}}
{{<image src="fireboi/gif_path.gif" height="310" caption="Gif of draw path outcome">}}
{{</rowgap>}}

<br/><br/>

# Conclusion

For the majority of the mentioned coding methods, it was my first time implementing them in my own game. Although incredibly challenging, I’ve vastly improved my skills in C# coding as a result. Not only by knowing more coding methods but also in learning how to approach errors. <br/>
The soundtrack used was also made by myself using the App Garageband.

