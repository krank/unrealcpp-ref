# APawn

En Pawn är en actor som kan tas över och styras av en [spelare](ulocalplayer.md) eller en AI via en [AController](acontroller.md).

Alla klasser som beskriver pawns ska ärva från denna. Den ärver i sin tur från [AActor](aactor/).

## En nyskapad APawn-klass

{% code title="MyPawn.h" lineNumbers="true" expandable="true" %}
```cpp
#pragma once

#include "CoreMinimal.h"
#include "GameFramework/Pawn.h"
#include "MyPawn.generated.h"

UCLASS()
class MYPROJECT_API AMyPawn : public APawn
{
    GENERATED_BODY()

public:
    AMyPawn();

protected:
    virtual void BeginPlay() override;

public: 
    virtual void Tick(float DeltaTime) override;
    virtual void SetupPlayerInputComponent(class UInputComponent* PlayerInputComponent) override;
};
```
{% endcode %}

{% code title="MyPawn.cpp" lineNumbers="true" expandable="true" %}
```cpp
#include "MyPawn.h"

AMyPawn::AMyPawn()
{
    PrimaryActorTick.bCanEverTick = true;
}

void AMyPawn::BeginPlay()
{
    Super::BeginPlay();    
}

void AMyPawn::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);
}

void AMyPawn::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
    Super::SetupPlayerInputComponent(PlayerInputComponent);
}
```
{% endcode %}

## SetupPlayerInputComponent()

Denna funktion körs när spelaren tar över pawn:en, för att binda spelarens knapptryckningar osv till objektets metoder.

Körs med en UInputComponent-instans som parameter.

## GetController()

Returnerar den [AController](acontroller.md) som just nu styr den här pawn:en.

```cpp
AController* AnyController = GetController();
APlayerController* PlayerController = Cast<APlayerController>(GetController());
```

## AutoPossessPlayer

Väljer vilken spelare som automatiskt ska ta kontrollen över objektet när det börjar finnas i spelet.

{% code title="" lineNumbers="true" %}
```cpp
AutoPossessPlayer = EAutoReceiveInput::Player0;
```
{% endcode %}
