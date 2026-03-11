# UInputMappingContext

Ett objekt som knyter ihop [UInputActions](uinputaction/) med knapptryck från spelaren.

{% code title="PlayerPawn.h" %}
```cpp
UPROPERTY(EditAnywhere, Category="Input")
UInputMappingContext* MappingContext;
```
{% endcode %}

Själva Input Mapping Context-objektet skapas i regel i Unreal-editorn, och länkas in till en UInputMappingContext-variabel i klassen.
