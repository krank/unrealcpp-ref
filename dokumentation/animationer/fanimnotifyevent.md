# FAnimNotifyEvent\*

## NotifyStateClass

En [TObjectPtr](../objektpekare.md#tobjectptr-less-than-greater-than) till det [UAnimNotifyState](uanimnotifystate.md) som skapade händelsen.

```cpp
if (Cast<AttackNotify>(EventReference.GetNotify()->NotifyStateClass))
{
    GEngine->AddOnScreenDebugMessage(-1, 1.0f, FColor::Green, TEXT("It was an attack!"));
}
```

