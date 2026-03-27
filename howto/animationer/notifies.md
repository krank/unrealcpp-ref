# Notifies\*

AnimNotifies och AnimNotifyStates gör att man kan köra kod vid specifika tillfällen i en animation.

## AnimNotify

Skapa en subklass till UAnimNotify. Override:a Notify.

```cpp
class MYPROJECT_API UExperimentalAttackNotify : public UAnimNotifyState
{
    GENERATED_BODY()
    
    virtual void Notify(USkeletalMeshComponent* MeshComp, 
        UAnimSequenceBase* Animation, 
        const FAnimNotifyEventReference& EventReference) override;
}
```

Efter att koden kompilerats, lägg till den nya notify:en till animationens eller montagets tidslinje.

## AnimNotifyState

Skapa en subklass till [UAnimNotifyState](../../dokumentation/animationer/uanimnotifystate.md). Override:a NotifyBegin, NotifyEnd och/eller NotifyTick.

```cpp
class MYPROJECT_API UExperimentalAttackNotify : public UAnimNotifyState
{
    GENERATED_BODY()
    
    virtual void NotifyBegin(USkeletalMeshComponent* MeshComp, 
        UAnimSequenceBase* Animation, float TotalDuration, 
        const FAnimNotifyEventReference& EventReference) override;
        
    virtual void NotifyEnd(USkeletalMeshComponent* MeshComp, 
        UAnimSequenceBase* Animation, 
        const FAnimNotifyEventReference& EventReference) override;
        
    virtual void NotifyTick(USkeletalMeshComponent* MeshComp, 
        UAnimSequenceBase* Animation, float FrameDeltaTime, 
        const FAnimNotifyEventReference& EventReference) override;
};
```

Efter att koden kompilerats, lägg till det nya notify state:t till animationens eller montagets tidslinje.

## Skicka vidare till APawn:en

För att få tag på en referens till den [APawn](../../dokumentation/apawn.md) vars animation triggade Notify/NotifyBegin/NotifyEnd/NotifyTick; utgå från den [USkeletalMeshComponent](../../dokumentation/komponenter/uprimitivecomponent/uskeletalmeshcomponent.md)-referens som skickades in som parameter, och anropa dess GetOwner()-metod. [Casta](../../dokumentation/cast.md) den sedan till den klass den borde vara, och kör önskad funktion.

```cpp
void UExperimentalAttackNotify::NotifyBegin(USkeletalMeshComponent* MeshComp, 
                                            UAnimSequenceBase* Animation,
                                            float TotalDuration, 
                                            const FAnimNotifyEventReference& EventReference)
{
  UMyCharacterClass* Owner = Cast<UMyCharacterClass>(MeshComp->GetOwner());
  if (!Reactor) return;
  
  Reactor->StartAttack();
}
```

### Passthru via interface

Den här tekniken gör att man kan samla logiken i sin APawn-klass och i högre grad återanvända sina Animation Notifies och Animation Notify States. Exemplen nedan är för Animation Notify States.

#### Interfacet

Skapa en **interface-klass** (Unreal Interface) som har NotifyBegin, NotifyEnd och NotifyTick.

{% code expandable="true" %}
```cpp
UINTERFACE(MinimalAPI)
class UINotifyStateReactor : public UInterface
{
    GENERATED_BODY()
};

/* An interface for AActors and others capable of reacting to NotifyStates
 */
class MYPROJECT_API IINotifyStateReactor
{
    GENERATED_BODY()

public:
    virtual void NotifyBegin(USkeletalMeshComponent* MeshComp,
                             UAnimSequenceBase* Animation, float TotalDuration,
                             const FAnimNotifyEventReference& EventReference)
    {
    };

    virtual void NotifyEnd(USkeletalMeshComponent* MeshComp,
                           UAnimSequenceBase* Animation,
                           const FAnimNotifyEventReference& EventReference)
    {
    };

    virtual void NotifyTick(USkeletalMeshComponent* MeshComp,
                            UAnimSequenceBase* Animation, float FrameDeltaTime,
                            const FAnimNotifyEventReference& EventReference)
    {
    };
};
```
{% endcode %}

#### APawn-subklassen

Gör så att APawn-subklassen som ska reagera på händelserna _implementerar_ detta interface.

```cpp
class MYPROJECT_API AExperimentalCharacter : public ACharacter, 
    public IINotifyStateReactor
{
```

#### UAnimNotifyState-subklassen

I UAnimNotifyState-subklassen, cast:a ownern till interfacet och skicka vidare alla parametrar.

```cpp
void UExperimentalAttackNotify::NotifyBegin(USkeletalMeshComponent* MeshComp, 
                                            UAnimSequenceBase* Animation,
                                            float TotalDuration, 
                                            const FAnimNotifyEventReference& EventReference)
{
    IINotifyStateReactor* Reactor = Cast<IINotifyStateReactor>(MeshComp->GetOwner());

    if (!Reactor) return;
    Reactor->NotifyBegin(MeshComp, Animation, TotalDuration, EventReference);
}
```

#### Funktioner i APawn-subklassen

Lägg till de funktioner som ska aktiveras av NotifyState:t i Apawn-subklassen.

Från AnimNotifyEventReference-parametern kan man få tag i en pekare till AnimNotifyEvent-objektet som representerar händelsen, och därifrån kan man få tag på APawn:en vars animation triggade alltihop. Den i sin tur har en NotifyStateClass som man kan försöka Cast:a till UAnimNotifyState-subklassen för att se om det var den som triggades.

Då kan man ha flera olika animationer som aktiverar flera olika AnimNotifyStates och reagera olika på dem.

```cpp
void AExperimentalCharacter::NotifyBegin(USkeletalMeshComponent* MeshComp, 
                                         UAnimSequenceBase* Animation,
                                         float TotalDuration, 
                                         const FAnimNotifyEventReference& EventReference)
{
    if (Cast<UAttackNotify>(EventReference.GetNotify()->NotifyStateClass))
    {
       GEngine->AddOnScreenDebugMessage(-1, 1.0f, FColor::Green, TEXT("Have at ye!"));
       MeleeDamageCollider->SetCollisionEnabled(ECollisionEnabled::QueryOnly);
    }
}
```
