# ULocalPlayer

Alla spelare som finns på den lokala klienten har ett eget unikt ULocalPlayer-objekt.

## GetSubsystem<>()

Returnerar en referens till ett av spelarens subsystem. Är en template-funktion och det som ska anges mellan <> är datatypen för det subsystem som ska returneras.

```cpp
UEnhancedInputLocalPlayerSubsystem* InputSystem = 
  Player->GetSubsystem<UEnhancedInputLocalPlayerSubsystem>();
```
