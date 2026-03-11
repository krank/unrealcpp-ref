# APlayerController

Player Controllers är objekt som låter players ([ULocalPlayer](ulocalplayer.md)) ta över och styra [Pawns](apawn.md). Ärver från [AController](acontroller.md).

## GetLocalPlayer()

Returnerar den [ULocalPlayer](ulocalplayer.md) som är kopplad till den här Player Controllern.

```cpp
const ULocalPlayer* Player = PlayerController->GetLocalPlayer();
```

## GetViewTarget()

Returnerar den AActor som är spelarens nuvarande kamera.

```cpp
AActor* CurrentCamera = OurPlayerController->GetViewTarget()
```

## SetViewTarget()

Ändrar vilken AActor som spelaren ska ha som sin kamera.

```cpp
OurPlayerController->SetViewTarget(CameraOne);
```

## SetViewTargetWithBlend()

Ändrar vilken AActor som spelaren ska ha som sin kamera – med en mjuk övergång. Första parametern är en AActor, andra är hur lång tid det ska ta att övergå från den nuvarande kameran till den nya.

```cpp
OurPlayerController->SetViewTargetWithBlend(CameraTwo, 0.2f);
```
