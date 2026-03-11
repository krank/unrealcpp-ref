# Komponenter

**Actor-komponenter** är återanvändbara objekt som kan kopplas till [actors](../aactor/).

**Scenkomponenter** Actor-komponenter som har en "transform", alltså en position, rotation och skalning – de är "sub-objects" till Actors.

Normalt skapar man dem i Actorns konstruktor, och attach:ar dem till varandra eller till Actorns RootComponent för att skapa en hierarki.

```cpp
VisualMesh = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("Mesh"));
VisualMesh->SetupAttachment(RootComponent);
```

### CreateDefaultSubobject<>()

Skapar en instans av given componentklass, med namnet som anges som parameter.

```cpp
VisualMesh = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("Mesh"));
```
