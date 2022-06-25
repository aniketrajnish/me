---
layout: default
---

## Soul Shard
Soul Shard is a cooperative puzzle platformer that takes inspiration from EA's 'It Takes Two'. It is being developed by [19 Souls on Board](https://www.19soulsonboard.com/about), a team of 19 student developers from Cohort 18 at the Florida Interactive Entertainment Academy on the downtown campus of the University of Central Florida. I'm assisting the team as a technical artist this summer.
* The development update to the game can be viewed [here](https://www.youtube.com/watch?v=cN4vf7va254). 
* The repository containing my contributions to the project can be found [here](https://github.com/19SOB/ucf-fiea-19sob-capstone-project-temp).

<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/SoulShard.png" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/19SOB.png" style="width:100%"></td>
 </tr>
 <tr>
    <td>Soul Shard Poster</td>
    <td>19 Souls on Board Logo</td>
 </tr>
</table>

## Smoke System
My first task was to design and develop a stylized explosive smoke particles for various machinery and explosions in the game. The basic idea was to develop a working prototype and then refine it in the iterative design process.

### Cloud Texture
Firstly, I designed various cloud textures with separate RGB channels for Base Color, Emmisivity and Opacity Mask. <br><br>
<img src="https://aniketrajnish.github.io/me/files/CloudRGB.png" style="width:100%">

### Smoke Material
* The smoke material was made using these textures. 
* The emmisivity and particle colors were exposed to edit while making the particles. <br><br> 
<img src="https://aniketrajnish.github.io/me/files/CloudMat.png" style="width:100%">

### Smoke Particles - 1st iteration
* The smoke particles were made using the Niagara VFX system. 
* The particles (100) were made to spawn in a burst around a cylinder with an initial velocity radially outwards. 
* A positive gravitational force was added to make the particles rise with a drag coefficient to smooth things out and make them feel natural. 
* The color (exposed parameter) was lerped between grey and black and rotation was added to individual particles aswell. <br><br>
<img src="https://aniketrajnish.github.io/me/files/Smoke1.gif" style="width:100%">

### Smoke Particles - 2nd iteration
* A light renderer was added to the particles to provide more definition to the explosion.
* The light renderer was intitited at the same intial position as the smoke particles.
* The intensity was lerped from 100 to 0.  <br><br>
<img src="https://aniketrajnish.github.io/me/files/Smoke2.gif" style="width:100%">

### Debris Texture
The debris texture was made in photoshop using refrence images online and the brush tool. <br><br>
<img src="https://aniketrajnish.github.io/me/files/DebrisTex.png" style="width:100%">

### Debris Material
The debris material was made using the debris texture in a similar fashion to the smoke material. <br><br>
<img src="https://aniketrajnish.github.io/me/files/DebrisMat.png" style="width:100%">

### Smoke Particles - 3rd iteration
* The debris particle was given the same parameters as the smoke particle.
* Since the debris appeared lighter, the drag was reduced and gravitational force (positive) was increased to increase the spread.
* Apart from that, a fountain emitter was assigned the same debris material to make the spread look more abrupt.  <br><br>
<img src="https://aniketrajnish.github.io/me/files/Smoke3.gif" style="width:100%">

### Spark Texture
The spark texture with separate RGB channels was obtained online. <br><br>
<img src="https://aniketrajnish.github.io/me/files/Spark.png" style="width:100%">

### Spark Material
* The spark material was made using the spark texture. 
* The blue channel was used as the opacity mask.
* The emmisive color was obtained by multiplying red and yellow. <br><br>
<img src="https://aniketrajnish.github.io/me/files/SparkMat.png" style="width:100%">

### Smoke Particles - Final iteration
* The spark particles were given the same parameter as the debris particle, i.e. a higher spread emitter and a fountain emitter.  <br><br>
<img src="https://aniketrajnish.github.io/me/files/Smoke4.gif" style="width:100%">

### Other Variations
Few other variations of the smoke system <br>

<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/Smoke5.gif" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/Smoke6.gif" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/Smoke7.gif" style="width:100%"></td>  
 </tr>
 <tr>
    <td>Less stylized system</td>
    <td>Debris only system</td>
    <td>Puff system</td>
 </tr>
</table>
*The gifs are sized properly, zoom in to see them clearly*

## Flame system
My next task was to come up with flame systems for different purposes like burning coal, chimneys, explosion, etc.

### Noise Texture
A stylized noise texture was created to serve as the opacity mask for the flame material. <br><br>
<img src="https://aniketrajnish.github.io/me/files/NoiseTex.png" style="width:100%">

### Flame Material
* Parametrically controlled texture coordinate was masked to obtain a controllable gradient. The value is clamped between 0 and 1 to prevent excessive bleeding.
* The noise texture was added to give fire-like shape to the mask.
* The UV map of the texture was given a panner (with texture coordinate as input) to animate it as if the fire was burning.
* A RadialGradientExponential (with texture coordinate as input) was subtracted from the mask to prevent square edges.
* The tiling, erosion & color of the material were exposed as dynamic parameters to be controlled by the Niagara system. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FlameMat.gif" style="width:100%">

### Flame Particles - 1st iteration
* The structure of the flame system was mostly done while making the material itself.
* The sprites were spawned in a circular grid with different rotations to give a 3D look.
* The color was lerped between yellow and red. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FlameVFX.gif" style="width:100%">

### Flame mesh
The flame system previously made was disapproved by the team for being too toony and not matching the game tone setting. So I decided to replace the sprite based particle system to a mesh based one. I modeled an icoshpere mesh with decimate modifier for this purpose to provide randomness. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FlameMesh.png" style="width:100%">

### Flame material
The flame material was created simply by assigning the particle color input to the emmisive color of the material so that we can assign it later in the emmiter itself. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FlameMat.png" style="width:100%">

### Flame Particles - Final iteration
* A fountain based emitter is chosen by removing gravity, cone velocity, drag and scaleColor just retaining the initial properties.
* The default sprite renderer is replaced with a mesh renderer and the icosphere and the flame material we created is assigned.
* The particles were assigned a random vertical velocity so that variance in the fire's peak giving it a natural look.
* They're scaled down in size as they reach up to give an inverted conical shape by using bezier curves to keep the transition smooth.
* The color is lerped between yellow and red with the lifetime of the particle. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FlameVFX2.gif" style="width:100%">

## Footprint System
Further I was assigned the task to develop a snow-based footprint system over snow for the main characters (Ambrose and Nimue).  

### Footprint Sprites - 1st iteration
* I used a snow texture I found online to make the footprint sprites.
* The foot impressions of the right foot of both the characters were traced using the pen tool and the texture was masked to make the footprint sprites.
* The left footprint sprite was simply made by inverting the image horizontally.

<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/AmbroseFI.png" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/NimueFI.png" style="width:100%"></td>
 </tr>
 <tr>
    <td>Ambrose Foot Impression</td>
    <td>Nimue Foot Impression</td>
 </tr>
</table>
*Foot Impressions*


<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/AmbroseFPS1.png" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/NimueFPS1.png" style="width:100%"></td>
 </tr>
 <tr>
    <td>Ambrose Footprint Sprite</td>
    <td>Nimue Footprint Sprite</td>
 </tr>
</table>
*Footprint Sprites*

### Footprint Material - 1st iteration 
* The material used for the footprints was a deferred decal material with blending mode set to translucent to be able to use it as a decal.
* The alpha of the texture/sprite was assigned to the opacity of the material and the RGB values to the base color. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FPMat1.png" style="width:100%">

### Footprint Blueprint
* An actor blueprint is created for both left and right footprints.
* A decal facing downwards with the footprint material is added as the child to the DefaultSceneRoot.
* The decal is made to fade away gradually after 5 seconds. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FPBP.png" style="width:100%">

### Adding to the third person blueprint
* I used the default third person character provided by Unreal to playtest the footprints.
* In the TPC blueprint, planes are added as a child of the mesh and the respective foot as the parent socket so that it snaps perfectly with the foot's movement.
* The planes are rendered as invisible (hidden in game), events are prevented from overlapping, and collisions are disabled as they're just meant for spawn refrence to the footprints. <br><br>
<img src="https://aniketrajnish.github.io/me/files/TPBP.png" style="width:100%">

### Animation Notifier
* Animation notifiers are added for each footprint to spawn at the appropriate time in the running animation.
* In the third person animation blueprint's event graph, a character reference is set and cast to the third person character as the blueprint awakes.
* In the third person character blueprint's event graph, two new custom events are introduced to spawn the footprints.
* The event is meant to spawn an actor from the footprint class we created earlier. 
* The foot reference is assigned to the spawn location. 
* The actor rotation is assigned to the spawn rotation.
* The spawn scale was decided after playtesting.
* The custom events are assigned to the animation notifier in the third person animation blueprint's event graph.

<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/AnimNoti.gif" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/TPAnimBP.png" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/TPCharBP.png" style="width:100%"></td>
 </tr>
 <tr>
    <td>Adding run animation notifier</td>
    <td>Third person animation event graph</td>
    <td>Third person character event graph</td>
 </tr>
</table>
*The images are sized properly, zoom in to see them clearly*

### 1st Output
<img src="https://aniketrajnish.github.io/me/files/FP1.gif" style="width:100%">

### Footprint Sprites - Final iteration
I was suggested by the team that the current footprint didn't look natural as snow footprints are generally a litte darker (dark grey/blue) with blue tint on the edges. Apart from this, they suggested to add normal information to the footprints aswell.
* I decreased the exposure of the textures, added bluish tint on the edges using the brush (Chalk 2) tool.
* Furthur, I generated the normals using the inbuilt 3D tools provided in Photoshop. (which turned out to be one of my laggiest workflow experiences with Photoshop).

<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/AmbroseFPS2.png" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/NimueFPS2.png" style="width:100%"></td>
 </tr>
 <tr>
    <td>New Ambrose footprint texture</td>
    <td>New Nimue footprint texture</td>
 </tr>
</table>
*Footprint Textures/Sprites*

<table border="0">
 <tr>
    <td><img src="https://aniketrajnish.github.io/me/files/AmbroseFPN.png" style="width:100%"></td>
    <td><img src="https://aniketrajnish.github.io/me/files/NimueFPN.png" style="width:100%"></td>
 </tr>
 <tr>
    <td>Ambrose footprint normal</td>
    <td>Nimue footprint normal</td>
 </tr>
</table>
*Footprint Normals*

### Footprint Material - Final iteration
The footprint material was now modified to support normal information and the noraml map textures generated were assigned. <br><br>
<img src="https://aniketrajnish.github.io/me/files/FPMat2.png" style="width:100%">

### Final Output
<img src="https://aniketrajnish.github.io/me/files/FP2.gif" style="width:100%">

## Snowstorm System
My next task was to design and develop a snowstorm system for the yard area. I was provided with a [reference video](https://www.shutterstock.com/video/clip-1058627680-dense-heavy-blizzard-snowstorm-vfx-insert-slow-motion) for the same.

### Snow Particles
* I found this task quite easy and felt that simply a fountain emitter with the default particle renderer would do the trick.
* So, I created a fountain emitter and inverted its initial velocity to make the particles fall downwards instead of upwards. 
* The particles were made to spawn around a big sphere.
* The trajectory cone's apex angle was increased aswell to increase the spread of the particles.
* The gravity was decreased and drag was increased to make the snowfall appear more natural. <br><br>
<img src="https://aniketrajnish.github.io/me/files/Snow1.gif" style="width:100%">

