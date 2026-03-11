# FTransform

Alla FActors har en FTransform som samlar deras position, rotation och skalning.

FTransforms kan också användas fristående, just för att samla den kombinationen.

```cpp
FTransform Transform (FRotator(), FVector(0,0,0), FVector::OneVector);
```

Det finns flera versioner av konstruktorn. Den ovan tar emot FTransformens rotation, position och skalning som en [FRotator](frotator.md) och två [FVectors](fvector.md).

## GetRotation() / SetRotation()

Returnerar resp. ändrar FTransformens rotation, i form av en [FRotator](frotator.md).

## GetLocation() / SetLocation()

Returnerar resp. ändrar FTransformens position, i form av en [FVector](fvector.md).

## GetScale3D() / SetScale3D()

Returnerar resp. ändrar FTransformens skalning, i form av en [FVector](fvector.md).
