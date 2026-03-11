# UPrimitiveComponent

En USceneComponent som har någon form av fysisk geometri i 3D-rymden, och som därmed kan kollidera med andra saker i spelvärlden.

## SetCollisionProfileName()

Ändrar vilken kollisionsprofil komponenten ska använda sig av. Se Edit → Project settings → Engine → Collisions för en komplett lista.

```cpp
SphereComponent->SetCollisionProfileName(TEXT("Pawn"));
```

## IgnoreActorWhenMoving()

Ändrar ifall komponenten när den förflyttar sig och sitt objekt, ska ignorera en specifik annan AActor.

```cpp
CollisionComponent->IgnoreActorWhenMoving(GetInstigator(), true);
```

## SetCollisionEnabled()

Bestämmer vilken sorts kollisionshantering komponenten ska ha.

```cpp
CollisionComponent->SetCollisionEnabled(ECollisionEnabled::NoCollision);
```

Det finns två huvudkategorier av kollisionshantering; sådana som handlar om hur objekt fysiskt kolliderar och simuleras (Simulation) och sådana som handlar om mer abstrakta undersökningar av objektets form (Queries). Simulering kan i sin tur delas in i Physics och Probe.

* Simulation
  * Reagerar bara på Rigidbody och constraints-baserade kollisioner
  * Physics: applicerar fysisk kollisionshantering
  * Probe: applicerar inte fysisk kollisionshantering
* Queries
  * Reagerar bara på Raycasts, sweeps, overlaps.

Utifrån dessa finns ett antal kombinationer:

* NoCollision,
* QueryOnly,
* PhysicsOnly,
* QueryAndPhysics,
* ProbeOnly,
* QueryAndProbe,
