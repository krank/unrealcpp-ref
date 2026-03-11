# UPrimitiveComponent

En USceneComponent som har någon form av fysisk geometri i 3D-rymden, och som därmed kan kollidera med andra saker i spelvärlden.

## SetCollisionProfileName()

Ändrar vilken kollisionsprofil komponenten ska använda sig av. Se Edit → Project settings → Engine → Collisions för en komplett lista.

```cpp
SphereComponent->SetCollisionProfileName(TEXT("Pawn"));
```
