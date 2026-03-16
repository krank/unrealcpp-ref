# USceneComponent

En "tom" komponent som alla andra komponenter som ska finnas i spelvärlden ärver från.

## SetupAttachment()

Anger vilken komponent som ska vara komponentens _parent_.

```cpp
VisualMesh->SetupAttachment(RootComponent);
```

Om komponenten har _sockets_, så kan man ange socketens namn som andra parameter.

```cpp
CameraComp->SetupAttachment(SpringArm, USpringArmComponent::SocketName);
```

## SetRelativeLocation()

Bestämmer komponentens position relativt sin _parent_. Anges som en [FVector](../datatyper/fvector.md).

```cpp
VisualMesh->SetRelativeLocation(FVector(0.0f,0.0f,0.0f));
```

## SetRelativeRotation()

Bestämmer komponentens rotation relativt sin _parent_. Anges som en [FRotator](../datatyper/frotator.md).

```cpp
VisualMesh->SetRelativeLocation(FRotator(0.0f,0.0f,60.0f));
```

## SetRelativeLocationAndRotation()

Bestämmer komponentens position och rotation relativt sin parent. Anges som en [FVector](../datatyper/fvector.md) och en [FRotator](../datatyper/frotator.md).

```cpp
SpringArmComp->SetRelativeLocationAndRotation(
  FVector(0.0f, 0.0f, 50.0f),
  FRotator(-60.0f, 0.0f, 0.00f)
);
```

## GetComponentRotation()

Returnerar en FRotator som beskriver komponentens rotation i relation till spelvärlden.

```cpp
FRotator Rotation = SpringArmComp->GetComponentRotation();
```
