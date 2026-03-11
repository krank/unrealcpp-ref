# UInputAction

Beskriver en action – något som kan göras av spelaren i spelet, t.ex. Move, Jump, Look, Shoot. Knyts till knapptryck och andra kontroller via en [UInputMappingContext](../uinputmappingcontext.md), och till funktioner via en [UEnhancedInputComponent](../uenhancedinputcomponent.md).

{% code title="PlayerPawn.h" %}
```cpp
UPROPERTY(EditAnywhere, Category="Input")
UInputAction* MoveAction;
```
{% endcode %}

Själva Input Action-objektet skapas i regel i Unreal-editorn, och länkas in till en UInputAction-variabel i klassen.

När man kör spelet och Input Action-objektet aktiveras (av en [mapping context](../uinputmappingcontext.md)) så är det en [FInputActionInstance](finputactioninstance.md) som skickas till funktionen, med information om vad som hänt i Input Action-objektet.
