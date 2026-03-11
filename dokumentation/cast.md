# Cast

Cast används för att på ett säkert sätt använda casting i C++. Om casten misslyckas, returnerar Cast en nullptr, som man sedan kan kolla efter för att se till så allt gått rätt till.

```cpp
const APlayerController* PlayerController = Cast<APlayerController>(GetController());
if (!PlayerController) return;
```
