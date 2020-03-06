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
Comme on l'a vu précedemment, le ray tracing avec illumination gloabal (méthode de Monte Carlo) ne converge pas vers des images nettes sans un nombre conséquent de rayons lancés par pixel. Si l'on se place dans un contexte temps réel, e.g un temps de calcul par image inferieur à 16 ms, les images seront forcément bruitées. 
</p>

<p align="center"><img src="img_noise.png" alt="noisy image" width="600"></p>

<p align="center">
  <a href="https://www.youtube.com/watch?v=HSmm_vEVs10"> 
    <img src="https://img.youtube.com/vi/HSmm_vEVs10/0.jpg" alt="noisy image" width="380">
  </a>. 
</p>
