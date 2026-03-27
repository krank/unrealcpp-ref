# UAnimInstance

Innehåller logik som driver en USkeletalMeshComponents animationer. Motsvaras av "Animation Blueprints" i Blueprintsystemet.

## Montage\_Play()

Spelar upp ett specifikt UAnimMontage.

```cpp
if (!Animator || !AttackMontage) return;
Animator->Montage_Play(AttackMontage);
```
