# Timers

## FTimerManager

Ett objekt som håller reda på ett antal timers.

{% code title="" %}
```cpp
FTimerManager& TimerManager = GetWorldTimerManager();
```
{% endcode %}

### SetTimer()

Skapar en timer, och gör så att en funktion körs när timern är klar.

{% code title="" %}
```cpp
TimerManager.SetTimer(CountdownTimerHandle, this, &ACountdown::AdvanceTimer, 1.0f, true);
```
{% endcode %}

Tar emot 4–6 parametrar:

* Ett FTimerHandle som kan användas för att t.ex. avbryta timern
* En referens till objektet som man ska köra funktionen på&#x20;
* Funktionen som ska köras
* Hur lång tid timern ska vänta innan den kör metoden
* (Om timern ska loopa)

### ClearTimer()

Nollställer och "tar bort" en timer, som anges genom ett FTimerHandle.

```cpp
TimerManager.ClearTimer(CountdownTimerHandle);
```

### ClearAllTimersForObject()

Nollställer och tar bort alla timers som knutits till ett specifikt objekt.

```cpp
TimerManager.ClearAllTimersForObject(this);
```

### GetTimerElapsed() / GetTimerRemaining()

Läs av hur mycket tid som gått, eller hur mycket tid som är kvar, av en timer som anges genom ett FTimerHandle.

```cpp
float timePassed = TimerManager.GetTimerElapsed(CountdownTimerHandle);
float timeLeft = TimerManager.GetTimerRemaining(CountdownTimerHandle);
```

### PauseTimer() / UnPauseTimer()

Pausa/avpausa en timer, som anges genom ett FTimerHandle.

```cpp
TimerManager.PauseTimer(CountdownTimerHandle);
TimerManager.UnPauseTimer(CountdownTimerHandle);
```

### IsTimerPaused()

Kolla om en timer, som anges genom ett FTimerHandle, är pausad just nu.

```cpp
bool isPaused = TimerManager.IsTimerPaused(CountdownTimerHandle);
```

## FTimerHandle

Ett objekt som kan användas för att komma åt en specifik timer.

```cpp
FTimerHandle CountdownTimerHandle;
```
