# UStaticMeshComponent

En komponent som visar ett [UStaticMesh](../../datatyper/#ustaticmesh) som ett objekt i spelvärlden. Ärver från [UPrimitiveComponent](./).

## SetStaticMesh()

Bestämmer vilket UStaticMesh som komponenten ska visa.

```cpp
VisualMesh->SetStaticMesh(VisualAsset);
```

## GetStaticMesh()

Läser av det UStaticMesh komponenten just nu visar.

```cpp
UStaticMesh mesh = VisualMesh->GetStaticMesh();
```
