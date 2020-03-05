---
layout: default
title: default
description: default
---

[Retour sommaire](./)

## Ray Tracing 


<p style='text-align: justify;'> 
Ne réinventons pas la roue, et tenons nous en à wikipedia pour ce qui est des définitions:
</p>

<p style='text-align:justify; background-color:#f3f6fa'> 
  «Le ray tracing (« lancer de rayons » en français) est une technique de calcul d'optique par ordinateur, utilisée pour le rendu en synthèse d'image ou pour des études de systèmes optiques. Elle consiste à simuler le parcours inverse de la lumière : on calcule les éclairages de la caméra vers les objets puis vers les lumières, alors que dans la réalité la lumière va de la scène vers l'œil.»
</p>

<p align="center"><img src="img_RTschema.png" alt="alt text" width="380"></p>

<p style='text-align: justify;'> 
Un rayon n'est rien d'autre qu'une droite qu'on définit par un point (l'origine du rayon) et un vecteur directeur.
Sur le schéma ci-dessus, la grille représente notre image finale. Dans le monde 3D, elle se représente par un plan situé entre notre caméra et la scène à visualiser. Chaque cellule de la grille représente un pixel. Pour colorer un pixel, on  "lance" un rayon ayant pour orgine la caméra et pour direction le pixel, la couleur de celui-ci sera définie par les matériaux des objects de la scène intersecté par le rayon. 
</p>

Pour faire le parallèle avec la rastérisation:
- la rastérisation amène les objets jusqu'au pixel.
- le ray tracing amène le pixel jusqu'aux objets.

Le papier précurseur de tout cela est de Turner Whitted, et date de 1980. Les techniques que l'on connait et utilise aujourd'hui en sont déja en bonne partie tirées, même les structures d'accélération que l'on retrouve dans les dernières technologies Nvidia/RTX.

<p align="center"><img src="img_RTwhitted.png" alt="alt text" width="580"></p>

Deux autres papiers ont suivies les années suivantes, et vont ajouter la composante aléatoire au ray tracing.
- Cook, 1984: ajout des ombres douces
- Kajiya 1986: ajout de l'illumination globale

On obtient alors des images d'un réalisme exeptionnel, mais aussi une consommation de ressource considérablement augmentée.

<p align="center"><img src="img_wikiRTpres.png" alt="alt text" width="480"></p>

<details>
  
  <summary>Pseudo code de Ray Tracing</summary>

  ```cpp
    Color TracePath(Ray ray, count depth) {
      if (depth >= MaxDepth) {
        return Black;  // Bounced enough times.
      }

      ray.FindNearestObject();
      if (ray.hitSomething == false) {
        return Black;  // Nothing was hit.
      }

      Material material = ray.thingHit->material;
      Color emittance = material.emittance;

      // Pick a random direction from here and keep going.
      Ray newRay;
      newRay.origin = ray.pointWhereObjWasHit;

      // This is NOT a cosine-weighted distribution!
      newRay.direction = RandomUnitVectorInHemisphereOf(ray.normalWhereObjWasHit);

      // Probability of the newRay
      const float p = 1/(2*M_PI);

      // Compute the BRDF for this ray (assuming Lambertian reflection)
      float cos_theta = DotProduct(newRay.direction, ray.normalWhereObjWasHit);
      Color BRDF = material.reflectance / M_PI ;

      // Recursively trace reflected light sources.
      Color incoming = TracePath(newRay, depth + 1);

      // Apply the Rendering Equation here.
      return emittance + (BRDF * incoming * cos_theta / p);
    }

    void Render(Image finalImage, count numSamples) {
      foreach (pixel in finalImage) {
        foreach (i in numSamples) {
          Ray r = camera.generateRay(pixel);
          pixel.color += TracePath(r, 0);
        }
        pixel.color /= numSamples;  // Average samples.
      }
    }
  ```

</details>


<p style='text-align: justify;'> 
patatiatata
</p>

![Image](img_rast.png)

<p style='text-align: justify;'> 

</p>
<p style='text-align: justify;'> 
 <a href="./raytracing.html"> le Ray-Tracing </a>. 
</p>

