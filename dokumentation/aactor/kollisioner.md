# Kollisioner\*

## NotifyHit()

Anropas när en av AActorns fysiska komponenter ([USphereComponent](../komponenter/uprimitivecomponent/uspherecomponent.md), [UStaticMeshComponent](../komponenter/uprimitivecomponent/ustaticmeshcomponent.md), [USkeletalMeshComponent](../komponenter/uprimitivecomponent/uskeletalmeshcomponent.md)) kolliderar med något, t.ex. som resultat av förflyttning eller fysiksimulering.

{% code title="MyProjectile.h" %}
```cpp
virtual void NotifyHit(class UPrimitiveComponent* MyComp, 
  AActor* Other, UPrimitiveComponent* OtherComp, 
  bool bSelfMoved, 
  FVector HitLocation, 
  FVector HitNormal, FVector NormalImpulse, 
  const FHitResult& Hit) override;
```
{% endcode %}

Tar emot _åtta_ parametrar.

* [UPrimitiveComponent](../komponenter/uprimitivecomponent/)\* **MyComp**: Den av AActorns komponenter som kände av kollisionen.
* [AActor](./)\* **Other**: Den AActor som kolliderades med.
* [UPrimitiveComponent](../komponenter/uprimitivecomponent/)\* **OtherComp**: Den av den andra AActorns komponenter som kolliderades med.
* bool **bSelfMoved:** huruvida AActorn själv förflyttade sig.
* [FVector](../datatyper/fvector.md) **HitLocation:** Positionen där kollisionen ägde rum.
* [FVector](../datatyper/fvector.md) **HitNormal:** Riktningen kollisionen hade.
* [FVector](../datatyper/fvector.md) **NormalImpulse:** ???
* [FHitResult](../datatyper/fhitresult.md)& **Hit:** Extra data om kollisionen.

