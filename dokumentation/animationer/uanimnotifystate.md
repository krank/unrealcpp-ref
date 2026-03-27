# UAnimNotifyState

Subklasser av denna beskriver Notify States, som kan läggas in i valfri animation.

```cpp
class MYSHOOTER_API UAttackNotify : public UAnimNotifyState
{
    GENERATED_BODY()
    
    virtual void NotifyTick(USkeletalMeshComponent* MeshComp, 
      UAnimSequenceBase* Animation, float FrameDeltaTime,
      const FAnimNotifyEventReference& EventReference) override;
      
    virtual void NotifyBegin(USkeletalMeshComponent* MeshComp, 
      UAnimSequenceBase* Animation, float TotalDuration,
      const FAnimNotifyEventReference& EventReference) override;
      
    virtual void NotifyEnd(USkeletalMeshComponent* MeshComp, 
      UAnimSequenceBase* Animation,
      const FAnimNotifyEventReference& EventReference) override;
    
};
```

## NotifyTick()

Anropas varje frame som State:t är aktivt.

Tar emot tre parametervärden:

* [USkeletalMeshComponent\*](../komponenter/uprimitivecomponent/uskeletalmeshcomponent.md) **MeshComp:** Det mesh som animationen körs på.
* UAnimSequenceBase\* **Animation:** Den animation som State:en aktiverats av.
* float **FrameDeltaTime:** Tiden som gått sedan förra ticken, i sekunder.
* const [FAnimNotifyEventReference](fanimnotifyeventreference.md)& **EventReference**: ???

## NotifyBegin()

Anropas när State:t först aktiveras.

Tar emot tre parametervärden:

* [USkeletalMeshComponent\*](../komponenter/uprimitivecomponent/uskeletalmeshcomponent.md) **MeshComp**: Det mesh som animationen körs på.
* UAnimSequenceBase\* **Animation**: Den animation som State:en aktiverats av.
* float **TotalDuration**: Hur lång State:t är, i sekunder.
* const [FAnimNotifyEventReference](fanimnotifyeventreference.md)& **EventReference**: ???

## NotifyEnd()

Anropas när State:t når sitt slut.

Tar emot två parametervärden:

* [USkeletalMeshComponent\*](../komponenter/uprimitivecomponent/uskeletalmeshcomponent.md) **MeshComp**: Det mesh som animationen körs på.
* UAnimSequenceBase\* **Animation**: Den animation som State:en aktiverats av.
* const FAnimNotifyEventReference& **EventReference**: ???
