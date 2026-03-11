# UFUNCTION

Används i header-filer för att ange exponera en _funktion_ till Unreal-editorn.

{% code title="" %}
```cpp
UFUNCTION(BlueprintNativeEvent)
void CountdownHasFinished();
```
{% endcode %}

Mellan parenteserna anges en specifier och eventuella extra inställningar/tillval.

## Blueprint functions

I Blueprints så är funktioner block som kan _köras_. De utför ett arbete som antingen påverkar något i scenen eller där resultatet lämnas vidare till andra block.

<table><thead><tr><th width="256">Specifier</th><th>Effekt i blueprint</th></tr></thead><tbody><tr><td><code>BlueprintPure</code></td><td>Enkel statisk funktion; tar emot eventuella inputs, häver ur sig outputs, påverkar inte objektet. Funktioner som är const blir automatiskt BlueprintPure.</td></tr><tr><td><code>BlueprintCallable</code></td><td>Funktion som kan påverka objektet, och kan kedjas ihop med andra körbara funktioner.</td></tr></tbody></table>

## Events

I Blueprints så är events block som aktiverar andra block. Events är röda och ligger alltid i _början_ av kedjor av andra block. "När det här händer, så…"

<table><thead><tr><th width="256">Specifier</th><th>Effekt i blueprint</th></tr></thead><tbody><tr><td><code>BlueprintImplementableEvent</code></td><td>Event som kan anropas (aktiveras) från C++ för att sätta igång kedjor av händelser i Blueprints. Saknar implementation i C++.</td></tr><tr><td><code>BlueprintNativeEvent</code></td><td>Event som kan anropas (aktiveras) från C++ för att sätta igång kedjor av händelser i Blueprints. Kan ha en implementation i C++.</td></tr></tbody></table>

### BlueprintNativeEvent

För BlueprintNativeEvents så kan man, om man vill, ha en default-version av logiken som ska hända när funktionen körs. Denna kan sedan ersättas genom att man skapar en händelsekedja i en Blueprint istället. Med andra ord lite som virtual/override; man definierar en _default-version_ som kan skrivas över i subklassen (blueprint-versionen).

Deklarationen i headerfilen och implementationen i cpp-filen ges olika namn; implementationen döps till deklarationsnamnet plus "\_Implementation".

{% code title="Countdown.h" %}
```cpp
UFUNCTION(BlueprintNativeEvent)
void CountdownHasFinished();
```
{% endcode %}

{% code title="" %}
```cpp
void ACountdown::CountdownHasFinished_Implementation()
{
	
}
```
{% endcode %}
