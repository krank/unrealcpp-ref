# FMath

## Lerp()

Skapar en linjär interpolering mellan två värden. Tar emot tre siffror: minvärdet, maxvärdet och ett värde mellan 0 och 1 som avgör hur långt mellan minvärdet och maxvärdet resultatet ska vara.

```cpp
float result = FMath::Lerp<float>(400.0f, 300.0f, 0.5f); // ger resultatet 350.0
```

## Clamp()

Begränsar ett värde så att det håller sig mellan ett min och ett maxvärde. Tar emot tre parametrar – nuvarande värde, minvärde och maxvärde.

Om värdet är under minvärdet så returneras minvärdet. Om det är högre än maxvärdet så returneras maxvärdet. Annars returneras värdet oförändrat.

{% code title="" lineNumbers="true" expandable="true" %}
```
float value = FMath::Clamp(value, -1.0f, 1.0f)
```
{% endcode %}
