# AActor

En Actor är ett objekt som kan instansieras in i spelvärlden.

Alla klasser som beskriver actors ska ärva från denna. Ärver i sin tur från UObject.

## En nyskapad AActor-klass

{% code title="MyActor.h" lineNumbers="true" expandable="true" %}
```cpp
#pragma once

#include "CoreMinimal.h"
#include "GameFramework/Actor.h"
#include "MyActor.generated.h"

UCLASS()
class MYPROJECT_API AMyActor : public AActor
{
    GENERATED_BODY()
    
public: 
    AMyActor();

protected:
    virtual void BeginPlay() override;

public: 
    virtual void Tick(float DeltaTime) override;

};
```
{% endcode %}

{% code title="MyActor.cpp" lineNumbers="true" expandable="true" %}
```cpp
#include "MyActor.h"

AMyActor::AMyActor()
{
    PrimaryActorTick.bCanEverTick = true;
}

void AMyActor::BeginPlay()
{
    Super::BeginPlay();
}

void AMyActor::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);
}
```
{% endcode %}

## Konstruktorn

Konstruktorn körs när objektet _skapas i editorn_, och används för att ange defaultvärden, skapa och lägga till [komponenter](../komponenter/) osv.

## BeginPlay()

BeginPlay körs när objektet _börjar finnas i spelvärlden_. Som standard körs också BeginPlay()-versionen från AActor.

## Tick()

Tick körs en gång varje bildruta (frame). Det betyder att funktionen körs oftare om man har en bra dator, än om man har en dålig. Som standard körs också BeginPlay()-versionen från UObject.

Man får med **DeltaTime** som en parameter; det är en float som beskriver hur lång tid föregående frame tog (i sekunder).

## Destroy()

Förstör AActorn.

<pre class="language-cpp" data-title=""><code class="lang-cpp">if (HitPoints &#x3C;= 0)
{
<strong>  Destroy();
</strong>}
</code></pre>

## SetActorHiddenInGame()

Visar eller döljer AActorn.

{% code title="" %}
```cpp
SetActorHiddenInGame(true);
```
{% endcode %}

## MakeNoise()

Gör ett virtuellt "ljud" som kan uppfattas av AI-systemen.

```cpp
MakeNoise(ShotLoudness, PawnOwner, 
  PawnOwner->GetActorLocation(), ShotNoiseRange, ShotNoiseTag);
```

Tar emot parametrar för:

* float: Ljudvolym
* APawn: den pawn som "äger" ljudet
* FVector: den plats ljudet ska komma från
* float: hur långt bort ljudet ska låta
* (FText: taggen ljudet ska ha och kunna identifieras med; typ "vad är det som låter")

## GetWorld()

Returnerar den [UWorld](../uworld.md) som actorn befinner sig i.

## RootComponent

En [USceneComponent](../komponenter/uscenecomponent.md) (eller någon av dess subklasser) som agerar "basen" för trädet av komponenter i objektet.

