# UWorld\*

En UWorld är en bana; en "värld".

## SpawnActor()

Skapar en instans av en [AActor](aactor/)-klass i spelvärlden. Returnerar en pekare till det skapade objektet.

```cpp
AFloatingActor* floater = GetWorld()->SpawnActor<AFloatingActor>();
```

Om man vill kan man ange en [FVector](datatyper/fvector.md) och en [FRotator](datatyper/frotator.md) som beskriver positionen AActorn ska skapas på, och dess rotation.

```cpp
AFloatingActor* floater = GetWorld()->SpawnActor<AFloatingActor>(Pos, Rot);
```

Man kan också ange dem som en [FTransform](datatyper/ftransform.md).

```cpp
AFloatingActor* floater = GetWorld()->SpawnActor<AFloatingActor>(Transform);
```

I båda fallen kan man också lägga till ett FActorSpawnParameters-objekt.

```cpp
AFloatingActor* floater = GetWorld()->SpawnActor<AFloatingActor>(Transform, SpawnParams);
```

