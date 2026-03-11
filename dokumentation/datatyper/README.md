# Datatyper

## Grundläggande

Nedan är de som används _oftast_. Man _får_ använda andra också.

| Datatyp   | Används för |
| --------- | ----------- |
| **int32** | Heltal      |
| **float** | Decimaltal  |

### Strings

I UE används olika datatyper för strings beroende på användningsområde.

| Datatyp     | Används för                                             |
| ----------- | ------------------------------------------------------- |
| **FName**   | Snabba, lättviktiga strings                             |
| **FText**   | Strings som ska visas för användaren; kan lokaliseras   |
| **FString** | Strings som ska manipuleras; är lite tyngre/långsammare |

Man kan [konvertera mellan dem](https://dev.epicgames.com/documentation/en-us/unreal-engine/string-handling-in-unreal-engine#conversions).

#### Konvertera till FText

Eftersom det är FText som används när man ska visa saker för användaren, så är det oftast till FText man vill konvertera.

{% code title="" %}
```cpp
// Från FString
FString Name = TEXT("Bilbo");
FText NameDisplay = FText::FromString(Name);

// Från int/float
int32 Hitpoint = 100;
FText HitpointDisplay = FText::AsNumber(Hitpoint);
```
{% endcode %}

### TEXT()

När man ska skriva in bokstavlig text i sin kod så använder man makrot TEXT() för att se till så texten sparas med unicode-kodning (så t.ex. åäö funkar som de ska).

{% code title="" %}
```cpp
FString Name = TEXT("Bilbo");
```
{% endcode %}

