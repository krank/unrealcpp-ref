# UGameplayStatics

En klass med användbara statiska hjälpfunktioner.

För att använda den måste man include:a den:

```cpp
#include "Kismet/GameplayStatics.h"
```

## GetPlayerController()

Returnerar en spelares [APlayerController](aplayercontroller.md). Tar emot två parametrar – ett spelvärldsobjekt och ett index. Index avgör vilken spelares controller som returneras.

```cpp
OurPlayerController = UGameplayStatics::GetPlayerController(this, 0);
```
