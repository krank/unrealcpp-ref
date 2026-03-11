# UKismetMathLibrary

## FindLookAtRotation()

Tar emot två [FVectors](datatyper/fvector.md). Skapar en FRotator som motsvarar vinkeln som uppstår om den första FVectorn tittar på den andra.

```cpp
const FRotator AimRot = UKismetMathLibrary::FindLookAtRotation(SpawnLoc, TargetLocation);
```
