---
title: Zia - 3D Character Animation
youtube: lJHgmDBUM6M
weight: 3
tags:
    - Technical Art
    - 3D/2D Art
    - 3D Modelling
    - Character Concept Art
    - Technical Animation

summary: Using advanced IK to FK rigging tools with Python shortcuts, Zia is an NPC character made using Maya, Substance 3D painter and Unreal Engine 4. 

links:
    - name: Gameplay video
      url: https://www.youtube.com/watch?v=lJHgmDBUM6M
---

<br/><br/>

# !Project Currently being updated! <br/>
I in the process of updating this project. The improved 'work in progress' images will be featured next to the original ones. <br/>
Besides improved the topology & UV map, the update will feature procedurally generated hair materials & animations, as well as differing 3D model textures, based on the player's choice of race (Elf, water elemental or fire elemental).

<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.5.0/model-viewer.min.js"></script>

### WIP Update - New Zia 3D model (Interactable):
<model-viewer alt="this is Zia" src="/img/zia/revamp_textures.glb" ar environment-image="/img/zia/texture_update_normal.png" poster="/img/zia/texture_update_normal.png" shadow-intensity="0" camera-controls touch-action="pan-y"></model-viewer>

<br/><br/>

# Zia

This project serves to demonstrate my abilities in creating a character purposed for a video game, using streamlined rigging, correct topology and UV mapping.
Zia is the main NPC of an open world adventure game. She resides in a single location, assigning quests to the player.

### Skills gained:

- Custom, streamlined FK to IK joint switch.
- Efficient UV maps creation.
- Stylised, hand painted texturing in substance 3D Painter.
- Python shortcut scripting in Maya.
- Exporting & scripting functional character in Unreal Engine.

<br/>

{{<row>}}
{{<image src="zia/70.jpg" height="500" caption="Older version - 3D model still 1">}}
{{<image src="zia/Still_5.jpg" height="500" caption="Older version - 3D model still 2">}}
{{</row>}}

<br/><br/>

# Concept Art

For Zia and her staff, I experimented with a few different iterations before creating the final reference. 
For the table and carpet, I created 3 different colour pallets that compliment Zia’s character. These are used to retexture the table and carpets, maximising efficiency in terms of re-using objects in a scene while minimising repetition.

{{<row>}}
{{<image src="zia/ca_staff.png" height="400" caption="Staff concept art">}}
{{<image src="zia/ca_allstaffs.png" height="400" caption="Previous itterations">}}
{{<image src="zia/ca_table.png" height="400" caption="Table concept art & colour schemes">}}
{{</row>}}

{{<rowgap>}}
{{<image src="zia/ca_zia.png" height="400" caption="Zia concept art & previous itterations">}}
{{<image src="zia/ca_elementals.png" height="400" caption="WIP update - elemental races concept art">}}
{{</rowgap>}}
<br/><br/>

# 3D Modelling

Zia's model features dynamic topology. For instance, her face segments following a direction akin to that of facial muscles, or several circular segments on her knuckles, elbows, shoulders etc. These will allow for more realistic skin bending when animated.

{{<row>}}
{{<image src="zia/3Dmodel_old.jpg" height="560" caption="Zia old 3D model render">}}
{{<image src="zia/wire_old.jpg" height="560" caption="Zia old wireframe">}}
{{</row>}}

WIP update: Zia's hair will be added later procedurally. Certain unnecessary segments were removed while, in more flexible areas (such as the shoulders & midriff) they were increased in order to avoid unnatural stretching issues. More details were added, such as the shoulder cloth and necklaces (evidencing her materialistic personality).

{{<row>}}
{{<image src="zia/3Dmodel_update.jpg" height="545" caption="WIP update - Zia new 3D model render">}}
{{<image src="zia/wire_update.jpg" height="545" caption="WIP update - Zia new wireframe">}}
{{</row>}}

<br/><br/>

# Texture

The texture was painted on Substance Painter using fill layers and black masks for easy modification. Being hand painted gives the model a more stylized look that compliments its base model.

{{<row>}}
{{<image src="zia/old_front.jpg" height="470" caption="Old texture - front view">}}
{{<image src="zia/old_side.jpg" height="470" caption="Old texture - Side view">}}
{{<image src="zia/old_back.jpg" height="470" caption="Old texture - Back view">}}
{{</row>}}

WIP update: The UV mapps were greatly improved, taking the least amount of space possible to keep the texture size small, while remaining unpixelated, undistorted and symmetrical where necessary to speed up the painting process with mirroring. I also took advantage of the black mask technique, quickly changing the texture colours & details to give the appearance of different magical races.

{{<row>}}
{{<image src="zia/texture_update_normal.png" height="375" caption="WIP Update - Zia elf texutre">}}
{{<image src="zia/texture_update_water.png" height="375" caption="WIP Update - Zia water elemental texture">}}
{{<image src="zia/texture_update_fire.png" height="375" caption="WIP Update - Zia fire elemental texture">}}
{{</row>}}

<br/><br/>

# Rigging & Technicalities

Zia uses advanced rigging methods, such as a custom value that allows the main joint to transition from IK to FK controls, made using nodes. 
Other methods include pole vectors, export skeletons and various nurb controls. 
These made the animation and export process significantly more efficient.

{{<rowgap>}}
{{<image src="zia/rig_hand.PNG" height="500" caption="Effective hand topology for accurate bending">}}
{{<image src="zia/rig_visibility.PNG" height="500" caption="Nodes altering visibility between IK & FK">}}
{{<image src="zia/rig_export.PNG" height="500" caption="Python skeleton selection group shortcut for quick exports">}}
{{<image src="zia/rig_poly.PNG" height="500" caption="Using a polysurface to direct axes orientation">}}
{{<image src="zia/rig_rig.PNG" height="550" caption="Final rig screenshot">}}
{{</rowgap>}}

<br/><br/>

# Export to Unreal Engine

I efficiently exported Zia into Unreal by replacing the included First Person Blueprint with Zia’s skeleton. After importing her textures and my decorational 3D assets, I created a state machine and a blueprint that would allow Zia to autonomously switch between her 2 animations.

{{<rowgap>}}
{{<image src="zia/unreal_1.PNG" height="420" caption="Replacing First Person with Zia">}}
{{<image src="zia/unreal_state.PNG" height="420" caption="Creating a state machine for animation transitions">}}
{{<image src="zia/unreal_code.PNG" height="420" caption="Custom blueprint to give Zia movement">}}
{{</rowgap>}}

To decorate her scene, I created a table and carpet 3D model, using black masks in Substance painter to efficiently diversify the environment through different coloured textures. 

{{<rowgap>}}
{{<image src="zia/Unreal_final.PNG" height="500" caption="Screenshot of Zia NPC in her scene">}}
{{</rowgap>}}

<br/><br/>

# Conclusion

As previously mentioned, Zia is currently being updated. Her new model & textures are finished. Next, I will skin her new model to the her original rig using Perry Leijten "Maya Skinning tools V5". After this, a simple 3D hair model will be created & placed using Unreal Engine character sockets, where 3 procedural hair materials will be placed, depending on the player's magical race choice.