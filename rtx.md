---
layout: default
title: default
description: default
---

[Retour sommaire](./) 
<p>
<a href="./rt_denoising.html"> Retour chapitre Débruitage </a>. 
</p>

## Technologie RTX 

<p style='text-align: justify;'> 
  En 2018, Microsoft annonce la sortie de DirectX Raytracing à la GDC (Game Developers Conference). C'est cette sortie qui va permettre l'implémentation du ray tracing dans les grosses liscences sorties les deux dernières années comme Battlefield 5 ou Minecraft.
</p>

<p align="center"><img src="https://upload.wikimedia.org/wikipedia/fr/b/b0/Directx.jpg" alt="minecraft" width="60"></p> 

<p style='text-align:justify;'> 
  Microsoft DirectX est une collection de bibliothèques destinées à la programmation d’applications multimédia, plus particulièrement de jeux ou de programmes faisant intervenir de la vidéo, sur les plates-formes Microsoft (Xbox, systèmes d’exploitation Windows). Sortie en 1995, DirextX est aujourd'hui largement répandue et utilisée dans la plupart des moteurs de jeux. 
</p>

<p style='text-align:justify;'> 
  DirextX Raytracing (DXT) a été deveoppé en Collaboration avec NVidia, et constitue une extention de DirectX 12. C'est donc une pierre de plus à l'édifice d'API déja déployées comme Direct3D. Le but de DXT est donc de pourvoir aux deveoppeurs une API simple encapsulant les élément de base de l'algorthmie du Ray tracing, en portant le tout sur GPU. Cette API comprend :
  
- une mise en place simple de pipepline de shader HSLS
- des inttersections rayon/triangle optimisés
- des structures d'accélération type BVH (Bounding volume hierarchy)7
- une encapsulation de la gestion complexe d'accès mémoire et transfert de données GPU/CPU
  
Mais le principal atout est la synergie rasterisation/ray tracing qu'offre DXT. En effet, comme on l'a vu précedemment, on ne peut pas se passer de la rasterisation aujourd'hui, et même si on le pourrait dans les prochaines années, seules les meilleurs (et plus onéreuses) cartes graphiques seraient à meme de supporter un ray tracing complet. Ainsi, il faut pourvoir mixer les deux technologies, et c'est ce qu'apporte DXR. Une des applications possible est de calculer le rendu sans ombres grâce à la rasterisation, et d'implémenter celles-ci grâce au raytracing. Il en va de même pour les surface transparente ou réfléchissantes: on détermine sur quels pixel de l'image les rayons doivent être lancés grâce à la rastérisation pour ensuite laisser place au raytracing.
</p>

<p style='text-align:justify;'> 
Un autre atout pour Microsoft est le timing de la sortie d prochaine XBox, qui pourra bénificer de la technologie DXT. Plusieurs viéos sont disponibles en ligne (liens ci-dessous), faisant l'étalage des possibilité offerte par DXT. 
</p>


<p align="center"> <i>SEED, Electronic Arts :</i></p>
<p align="center">
  <a href="https://www.youtube.com/watch?v=LXo0WdlELJk"> 
    <img src="https://img.youtube.com/vi/LXo0WdlELJk/0.jpg" alt="noisy image" width="380">
  </a>
</p>

<p align="center"> <i>EPIC, with collaboration from ILMxLAB and NVIDIA : </i> </p>  
<p align="center"> 
  <a href="https://www.youtube.com/watch?v=J3ue35ago3Y"> 
    <img src="https://img.youtube.com/vi/J3ue35ago3Y/0.jpg" alt="noisy image" width="380">
  </a>.
</p>


<p align="center"><img src="img_RT_minecraft.png" alt="minecraft" width="600"></p>

<p align="center"><img src="img_RT_battlefiled5.png" alt="battlfield5" width="600"></p>



