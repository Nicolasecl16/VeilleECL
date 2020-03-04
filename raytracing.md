---
layout: default
title: default
description: default
---

[Retour sommaire](./)

## Ray Tracing 

<p style='text-align: justify;'> 
patatipatata
</p>

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

<p style='text-align: justify;'> 
patatiatata
</p>

![Image](img_rast.png)

<p style='text-align: justify;'> 

</p>
<p style='text-align: justify;'> 
 <a href="./raytracing.html"> le Ray-Tracing </a>. 
</p>

