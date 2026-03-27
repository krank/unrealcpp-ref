# UCapsuleComponent

## SetCapsuleSize()

Ändrar kapselns oskalade storlek. Tar emot två parametrar:

* float InRadius: kapselns radie.
* float InHalfHeight: kapselns halva höjd.

## SetCapsuleHalfHeight()

Ändrar kapselns halva höjd, inklusive halvkloten. Tar emot en float som parameter.

## SetCapsuleRadius()

Ändrar kapselns radie. Tar emot en float som parameter.

## GetScaledCapsuleHalfHeight()

Returnerar kapselns halva höjd som en float, med skalningen applicerad.

## GetScaledCapsuleHalfHeight\_WithoutHemisphere()

Returnerar kapselns halva höjd, minus halvklotet på toppen, med skalningen applicerad, som en float.

## GetScaledCapsuleRadius()

Returnerar kapselns radie, med skalningen applicerad, som en float.

## GetUnscaled…

Alla GetScaled-funktioner finns också i en Unscaled-version som ger värdena innan komponentens skalning applicerats.
