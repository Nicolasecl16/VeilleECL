---
layout: default
title: default
description: default
---

[Retour sommaire](./) 
<p>
<a href="./raytracing.html"> Retour chapitre Ray Tracing </a>. 
</p>

## Débruitage appliqué au Ray Tracing

<p style='text-align: justify;'> 
Comme on l'a vu précedemment, le ray tracing avec illumination gloabal (méthode de Monte Carlo) ne converge pas vers des images nettes sans un nombre conséquent de rayons lancés par pixel. Si l'on se place dans un contexte temps réel, e.g un temps de calcul par image inferieur à 16 ms, les images seront forcément bruitées. 
</p>

<p align="center"><img src="img_noise.png" alt="noisy image" width="380"></p>

<p style='text-align: justify;'> 
La technique de denoising conssiste donc à ne lancer que quelques rayons par pixel, et d'appliquer des filtres sur l'image bruitée. Cela fait plusieurs années (début années 2010) que le sujet est creusé par de nombreuses recherchres, notemment l'industrie du cinéma d'animation, où la grande qualité des images et le complexité des scène necessite parfois jusqu'à des dizaines d'heures par image. Les studio Disney ont sortie de nombreux papiers (https://studios.disneyresearch.com/category/rendering/).
</p>

<p align="center"><img src="img_disney.png" alt="noisy image" width="380"></p>

<p style='text-align: justify;'> 
Cependant, toutes ces recherches n'avaient pas pour objectif un rendu temps réel, et les algorithmes developpé rendent des images souvent dans l'ordre une à 10 minutes par image.
</p>


