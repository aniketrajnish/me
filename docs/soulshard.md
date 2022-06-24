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
* The tiling, erosion & color of the material were exposed as dynamic parameters to be controlled by the Niagara system.
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
My next task was to develop a footprint system over snow for Ambrose and Nimue. 
