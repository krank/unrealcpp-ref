# UInputComponent

En UInputComponent är en UActorComponent som tillhör det gamla inputsystemet och binder samman användare knapptryck och axlar med funktioner.

## BindAction()

Kopplar ihop en _action_ (anges som en string) med en funktion. Tar emot fyra parametrar:

* Namnet på den action som ska kopplas
* Den typ av händelse (event) som ska kopplas
* Objektet funktionen ska köras på
* Funktionen som som ska köras

Funktionen ska vara en enkel sådan, utan returtyp eller parametrar.

De två viktigaste eventen är **IE\_Pressed** och **IE\_Released**.

```cpp
InputComponent->BindAction("Jump", IE_Pressed, this, &AMyPawn::Jump);
```

## BindAxis()

Kopplar ihop en _axel_ (anges som en string) med en funktion. Tar emot fyra parametrar:

* Namnet på den axis som ska kopplas
* Objektet funktionen ska köras på
* Funktionen som som ska köras

Funktionen ska vara en enkel sådan, utan returtyp eller parametrar.

```cpp
InputComponent->BindAxis("MoveX", this, &APawnClass::Move_XAxis);
```
