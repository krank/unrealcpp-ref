# Logging

[UE\_LOG](https://dev.epicgames.com/documentation/en-us/unreal-engine/logging-in-unreal-engine) används för all loggning. Den tar emot 3+ parametrar – i tur och ordning kategori, verbositet, text att logga, och värde som ska stoppas in slutligen eventuella variabler som ska stoppas in i texten.

Kategorin är oftast LogTemp.

## Enkel loggning av text

```cpp
UE_LOG(LogTemp, Display, TEXT("Hello, World"));
```

## Loggning med templating

```cpp
UE_LOG(LogTemp, Warning, TEXT("Actor location: %s"), *vector.ToString());
```

## Verbositet

De fetmarkerade är de som oftast används för vanlig test-loggning.

<table><thead><tr><th width="174"></th><th></th></tr></thead><tbody><tr><td>Fatal</td><td>Skriver ut till konsolen och loggfil, och kraschar sedan (även om loggning är avstängt)</td></tr><tr><td>Error</td><td>Skriver ut som ett felmeddelande till konsolen och loggfil.</td></tr><tr><td>Warning</td><td>Skriver ut som en varning till konsolen och loggfil.</td></tr><tr><td><strong>Display</strong></td><td>Skriver ut till konsolen och loggfil</td></tr><tr><td><strong>Log</strong></td><td>Skriver ut till loggfil</td></tr><tr><td>Verbose</td><td>Skriver ut till loggfil om verbos loggning är inställd.</td></tr></tbody></table>

## GEngine->AddOnScreenDebugMessage()

Skriver ut ett meddelande till _skärmen_.

```cpp
GEngine->AddOnScreenDebugMessage(-1, 5.f, FColor::Red, TEXT("This is an on screen message!"));
```

De första fyra parametrerna är:

* int64: key – ett unikt index. Oftast -1; då ges texten ett eget index automatiskt.
* float: hur länge, i sekunder, texten ska visas.
* FColor: Den färg texten ska ha.
* FString: Den text som ska skrivas ut.
