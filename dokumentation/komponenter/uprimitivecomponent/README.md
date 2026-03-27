# UPrimitiveComponent

En USceneComponent som har någon form av fysisk geometri, en _form_ i 3D-rymden, och som därmed kan kollidera med andra saker i spelvärlden.

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

## FirstPersonPrimitiveType

En variabel som bestämmer hur komponenten ska hanteras när den ses i ett förstapersonsspel.

```cpp
FirstPersonMesh->FirstPersonPrimitiveType = EFirstPersonPrimitiveType::FirstPerson;
```

Möjliga värden:

* EFirstPersonPrimitiveType::**FirstPerson** – Renderas med kamerans förstapersons-inställningar
* EFirstPersonPrimitiveType::**WorldSpaceRepresentation** – Renderas bara för andra spelare/kameror
* EFirstPersonPrimitiveType::**None** – ändras inte av förstaperspns-rendering.

## SetOnlyOwnerSee()

Bestämmer ifall komponenten bara ska vara synlig för dess ägare.

```cpp
FirstPersonMesh->SetOnlyOwnerSee(true);
```

## SetCollisionProfileName()

## Overlaps

Overlapping är när två former överlappar i 3D-världen. För att detta ska kunna kännas av med kod behöver man dels aktivera så att formerna genererar overlap events, och dels knyta ihop så att dessa events får funktioner att köras.

### SetGenerateOverlapEvents() / GetGenerateOverlapEvents()

Metoder som ändrar resp läser av ifall formen ska generera _overlap events_. Behöver vara true på båda formerna för att events ska genereras.

### OnComponentBeginOverlap

Detta är en event som man kan prenumerera på genom att lägga till funktioner med rätt profil. Detta gör man via AddDynamic.

```cpp
MeleeDamageCollider->OnComponentBeginOverlap.AddDynamic(
    this, &AExperimentalCharacter::OnMeleeBeginOverlap);
```

Exempel på funktion med rätt profil:

```cpp
void AExperimentalCharacter::OnMeleeBeginOverlap(UPrimitiveComponent* MyComp, 
    AActor* Other, UPrimitiveComponent* OtherComp, 
    int32 OtherBodyIndex, bool bFromSweep, 
    const FHitResult& SweepResult)
{
}
```

Tar emot _åtta_ parametrar.

* [UPrimitiveComponent](./)\* **MyComp**: Den av AActorns komponenter som kände av kollisionen.
* [AActor](../../aactor/)\* **Other**: Den AActor som kolliderades med.
* [UPrimitiveComponent](./)\* **OtherComp**: Den av den andra AActorns komponenter som kolliderades med.
* int32 **OtherBodyIndex:** Om OtherComp är en [USkeletalMeshComponent](uskeletalmeshcomponent.md) så är detta index för det specifika ben som kolliderades med.
* bool **bFromSweep:** ???
* [FHitResult](../../datatyper/fhitresult.md)& **SweepResult:** Extra data om kollisionen.

### SetCollisionEnabled()

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
