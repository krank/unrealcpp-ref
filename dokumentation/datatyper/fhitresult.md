# FHitResult

En struct som beskriver en kollisionspunkt mellan två former i spelvärlden.

## IsValidBlockingHit()

Returnerar true om kollisionen påbörjades denna frame.

## GetActor()

Returnerar den [AActor](../aactor/) som äger komponenten som kolliderades med.

## Time

En float mellan 0 och 1 som beskriver när under denna frame som kollisionen faktiskt inträffade.

## Normal

Kollisionens vinkel, i form av en [FVector](fvector.md).

