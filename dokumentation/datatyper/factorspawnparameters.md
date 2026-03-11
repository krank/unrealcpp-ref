# FActorSpawnParameters

En struct som beskriver inställningar och tillval för en [SpawnActor](../uworld.md#spawnactor).

```cpp
FActorSpawnParameters SpawnParams;
SpawnParams.SpawnCollisionHandlingOverride = ESpawnActorCollisionHandlingMethod::AlwaysSpawn;
SpawnParams.TransformScaleMethod = ESpawnActorScaleMethod::OverrideRootScale;
SpawnParams.Owner = GetOwner();
SpawnParams.Instigator = PawnOwner;
```

## SpawnCollisionHandlingOverride

Hur ska kollisioner som inträffar direkt när AActorn spawnas hanteras? Ska AActorn fortfarande spawnas?

```cpp
SpawnParams.SpawnCollisionHandlingOverride = 
  ESpawnActorCollisionHandlingMethod::AlwaysSpawn;
SpawnParams.SpawnCollisionHandlingOverride = 
  ESpawnActorCollisionHandlingMethod::DontSpawnIfColliding;
```

## TransformScaleMethod

Ska den spawnade AActorn skalas utifrån objektet som spawnade det (MultiplyWithRoot), eller utifrån spelvärlden (OverrideRootScale)?

```cpp
SpawnParams.TransformScaleMethod = ESpawnActorScaleMethod::OverrideRootScale;
SpawnParams.TransformScaleMethod = ESpawnActorScaleMethod::MultiplyWithRoot;
```

## Owner

Vilken APawn det är som spawnat AActorn.

## Instigator

Vilken APawn som har ansvaret för skada som orsakas av den spawnade AActorn
