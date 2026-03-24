# UEnhancedInputComponent

En UEnhancedInputComponent är en UActorComponent som tillhör det nya inputsystemet och binder samman [UInputActions](uinputaction/) (händelser) med funktioner. Den ärver från [UInputComponent](../komponenter/uinputcomponent.md).

## BindAction()

Knyter ihop en UInputAction med en funktion – så när en viss händelse sker (t.ex. att en användare trycker på hoppknappen, så att Jump-Input Action:en aktiveras) så körs funktionen.

Har fyra parametrar:

* Den UInputAction som ska kopplas
* Den typ av händelse som ska aktivera kopplingen
* Objektet funktionen ska köras på
* En referens till funktionen som ska köras

```cpp
Input->BindAction(MoveAction, ETriggerEvent::Triggered, this, &APawnWithCamera::OnMove);
```

De viktigaste event-typerna är:

* **ETriggerEvent::Triggered** som körs varje frame som eventen pågår
* **ETriggerEvent::Started** som körs den frame eventen startar (t.ex. då en knapp först trycks ner)
* **ETriggerEvent::Completed** som körs den frame eventen avslutas (t.ex. då en knapp släpps upp)

Funktionen bör inte ha någon returtyp, men ta emot en referens till en [FInputActionInstance](uinputaction/finputactioninstance.md) eller ett [FInputActionValue](uinputaction/finputactionvalue.md). Det senare är bättre om man ändå bara vill åt värdet.

```cpp
void APawnWithCamera::OnMove(const FInputActionInstance& Instance)
{
    UE_LOG(LogTemp, Warning, TEXT("Moving!"));
}

void APawnWithCamera::OnLook(const FInputActionValue& Value)
{
    UE_LOG(LogTemp, Warning, TEXT("Moving!"));
}
```
