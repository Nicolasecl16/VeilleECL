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
Comme on l'a vu précédemment, le Ray Tracing avec illumination globale (méthode de Monte Carlo) ne converge pas vers des images nettes sans un nombre conséquent de rayons lancés par pixel. Si l'on se place dans un contexte temps réel, e.g un temps de calcul par image inférieur à 16 ms, les images seront forcément bruitées. 
</p>

<p align="center"><img src="img_noise.png" alt="noisy image" width="600"></p>

<p style='text-align: justify;'> 
La technique de denoising consiste donc à ne lancer que quelques rayons par pixel, et d'appliquer des filtres sur l'image bruitée. Cela fait plusieurs années (début des années 2010) que le sujet est creusé par de nombreuses recherches, notamment l'industrie du cinéma d'animation, où la grande qualité des images et la complexité des scènes nécessitent parfois jusqu'à des dizaines d'heures par image.  <a href="https://studios.disneyresearch.com/category/rendering/"> Les studios Disney ont sortie de nombreux papiers depuis </a>
</p>

<p align="center"><img src="img_disney.png" alt="noisy image" width="600"></p>

<p style='text-align: justify;'> 
Cependant, ces recherches n'avaient pas pour objectif un rendu temps réel, et les algorithmes développés rendent des images souvent dans un ordre de grandeur de une à plusieurs dizaines de minutes par image. EN 2017, NVidia, très impliquée dans la course au Ray Tracing temps réel, a sortie un résultat de recherche présentant un denoising temps réel à un seul rayon/pixel avec une qualité comparable à un rendu à 2000 rayons/pixel. Le résultat est visible sur la vidéo ci-dessous de <i>Two Minutes Papers</i>.
</p>

<p align="center">
  <a href="https://www.youtube.com/watch?v=HSmm_vEVs10"> 
    <img src="https://img.youtube.com/vi/HSmm_vEVs10/0.jpg" alt="noisy image" width="380">
  </a>. 
</p>

<p style='text-align: justify;'> 
  En voyant cela, il est difficile de croire qu'il soit possible de passer d'un tel bruit à une image nette, cependant il faut garder à l'esprit que le bruit est seulement dû à la composante de lumière indirecte : Sans illumination globale, l'image n'est certes pas parfaites en termes de jeu de lumière, mais il n'y a aucun bruit. La technique consiste donc à passer ne filtrer la composante indirecte que sur les zones de pixel correspondant aux zones homogènes de l'image nette. Les <i> sharp egdes </i> sont donc préservés, et moins de flou se trouve introduit. En plus de cela, le filtre est aussi temporel: les données des rayons lancés dans pour générer une <i>frame</i> sont réutilisées pour générer les frames suivantes. L'IA a une part importante à jouer dans les filtres appliqués, qui sont constitués de réseaux de convolution, d'auto-encoder, etc.
</p>

<p style='text-align: justify;'> 
Depuis de nombreux autres recherches continuent d'améliorer ces résultats. Le blog de <a href="https://alain.xyz/blog/raytracing-denoising"> Alain Galvan</a>, <i>Graphics Software Engineer</i>, recense de manière approfondie toutes les techniques et performances actuelles de la recherche sur le sujet. <i>Sampling Techniques</i>, <i>Sobol Sequences</i>, <i>Spatio-Temporal Techniques</i>, <i>Motion Buffer</i>, <i>Bluring Kernels</i>, <i>Firefly Rejection</i> pour les intéressés.
</p>

<p style='text-align: justify;'> 
Malgré cela, des imperfections subsistent et la technologie n'est pas encore totalement prête. De plus, l'industrie du jeu vidéo n'est pas prête d'abandonner la rastérisation et ses qualités. Ainsi, aujourd'hui, en mars 2020, quand on parle de ray tracing dans le jeu vidéo, on parle surtout de <a href="./rtx.html"> la technologie RTX. </a>. 
</p>

## Références

Alan Galvan, An overview of the state of the art in ray denoising, https://alain.xyz/blog/raytracing-denoising

Disney, Denoising Deep Monte Carlo Renderings, et autres publications, https://studios.disneyresearch.com/category/rendering/

NVidia, Interactive Reconstruction of Monte Carlo Image Sequences using a Recurrent Denoising Autoencoder, https://research.nvidia.com/sites/default/files/publications/dnn_denoise_author.pdf

Koskela et al , Blockwise Multi-Order Feature Regression for Real-Time Path Tracing Reconstruction, http://www.tut.fi/vga/publications/Blockwise_Multi-Order_Feature_Regression_for_Real-Time_Path_Tracing_Reconstruction.html

