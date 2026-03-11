# UPawnMovementComponent

En UActorComponent som kan användas för att flytta en pawn. Ingår som standard i ACharacter, men kan implementeras och läggas till i APawns.

Komponenten har alltid en UpdatedComponent, som är den USceneComponent den flyttar på.

## TickComponent()

Metod som körs varje frame.

{% code title="CustomPawnMovementComponent.h" %}
```cpp
virtual void TickComponent(float DeltaTime, enum ELevelTick TickType, 
  FActorComponentTickFunction* ThisTickFunction) override;
```
{% endcode %}

```cpp
void UCustomPawnMovementComponent::TickComponent(float DeltaTime, enum ELevelTick TickType,
    FActorComponentTickFunction* ThisTickFunction)
{

}
```

## AddInputVector()

Lägger till en inputvektor till komponentens samlade input denna frame. Inputvektorer är normalt max 1 i längd.

```cpp
OurMovementComponent->AddInputVector(movementDirection);
```

## ConsumeInputVector()

Funktion som returnerar komponentens samlade inputvektor för denna frame.

```cpp
FVector DesiredMovementThisFrame = 
  ConsumeInputVector()
  .GetClampedToMaxSize(1.0f) * DeltaTime * 150.0f;
```

## SafeMoveUpdatedComponent()

Flyttar komponentens UpdatedComponent, och respekterar kollisioner (dvs objektet åker inte in i andra objekt).

```cpp
FHitResult Hit;
SafeMoveUpdatedComponent(DesiredMovementThisFrame, 
  UpdatedComponent->GetComponentRotation(), true, Hit);
```

Tar emot fyra parametrar:

* [FVector](../datatyper/fvector.md): Hur mycket den ska försöka förflytta
* [FRotator](../datatyper/frotator.md): Vilket håll den ska riktas åt
* bool: Om förflyttningen ska respektera kollisioner
* [FHitResult](../datatyper/fhitresult.md): Kommer att lagra information om eventuella kollisioner

## SlideAlongSurface()

Gör att objektet glider längsmed en yta, definierad som en normal-vektor.

```cpp
SlideAlongSurface(DesiredMovementThisFrame, 1.0f - Hit.Time, Hit.Normal, Hit);
```

Tar emot fyra parametrar:

* [FVector](../datatyper/fvector.md): Hur mycket den försökt förflytta sig denna frame
* float: Hur stor andel av denna som ska användas här
* [FVector](../datatyper/fvector.md): Normalen (vinkeln) för ytan man ska glida längsmed
* [FHitResult](../datatyper/fhitresult.md): Den hit som ledde till att man ville göra denna slide

## ShouldSkipUpdate()

Returnerar true om komponenten inte borde uppdateras denna frame (sitter fast eller inte renderas). Tar emot DeltaTime som parameter.

```cpp
if (ShouldSkipUpdate(DeltaTime)) return;
```

## PawnOwner

Den [APawn](../apawn.md) som äger komponenten.

## UpdatedComponent

Den [USceneComponent](uscenecomponent.md) som ska flyttas och uppdateras. Bör vara en subklass till [UPrimitiveComponent](uprimitivecomponent/) så att det finns någon form av 3D-form som kan känna av kollisioner med andra objekt.

