# Position och rotation

## GetActorForwardVector()

Läser av objektets nuvarande "framåt"-riktning i form av en [FVector](../datatyper/fvector.md) med längden 1.

```cpp
FVector Forward = GetGetActorForwardVector()
```

## GetActorRightVector()

Läser av objektets nuvarande "höger"-riktning i form av en [FVector](../datatyper/fvector.md) med längden 1.

```cpp
FVector Forward = GetGetActorRightVector()
```

## GetActorLocation()

Läser av objektets nuvarande position som en [FVector](../datatyper/fvector.md).

```cpp
FVector Location = GetActorLocation();
```

## SetActorLocation()

Bestämmer att objektet ska befinna sig på en specifik position, definierad som en [FVector](../datatyper/fvector.md).

```cpp
SetActorLocation(Rotation);
```

## GetActorRotation()

Läser av objektets nuvarande rotation som en [FRotator](../datatyper/frotator.md).

```cpp
FRotator Rotation = GetActorRotation();
```

## SetActorRotation()

Bestämmer att objektet ska ha en viss rotation, definierad som en [FRotator](../datatyper/frotator.md).

```cpp
SetActorRotation(Rotation);
```

## SetActorLocationAndRotation()

Bestämmer position och rotation samtidigt. Tar emot en [FVector](../datatyper/fvector.md) och en [FRotator](../datatyper/frotator.md) som parametrar.

```cpp
SetActorLocationAndRotation(Location, Rotation);
```
