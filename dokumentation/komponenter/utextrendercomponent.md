# UTextRenderComponent

En komponent som visar en text som ett objekt i spelvärlden (till skillnad från en text-widget, som visar en text i UI:t). Ärver från [USceneComponent](uscenecomponent.md).

## SetText()

Ändrar vilken text som visas av komponenten; tar emot en [FText](../datatyper/#strings) som parameter.

{% code title="" %}
```cpp
CountdownText->SetText(FText::FromString("GO!"));
```
{% endcode %}

## SetWorldSize()

Ändrar textens storlek i världen. Tar emot en [float](../datatyper/#grundlaggande) som parameter.

```cpp
CountdownText->SetWorldSize(150.0f);
```

## SetHorizontalAlignment()

Ändrar centreringen för texten. Alternativen är EHTA\_Left, EHTA\_Right och EHTA\_Center.

{% code title="" %}
```cpp
CountdownText->SetHorizontalAlignment(EHTA_Center);
```
{% endcode %}
