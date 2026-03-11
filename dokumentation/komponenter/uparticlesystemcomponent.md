# UParticleSystemComponent

En [USceneComponent](uscenecomponent.md) som beskriver ett partikelsystem som ska visas i spelvärlden.

## SetTemplate()

Bestämmer vilket [UParticleSystem](../datatyper/uparticlesystem.md) som ska användas av komponenten.

```cpp
OurParticleSystem->SetTemplate(ParticleAsset);
```

## ToggleActive()

Stänger av partikelsystemet om det är påslaget, och kör igång det om det är avslaget.

## bAutoActivate

Huruvida partikelsystemet drar igång direkt när objektet instansieras.

## Template

Det partikelsystem komponenten använder.
