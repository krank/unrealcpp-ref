# Enhanced Input System

Detta är Unreal Engines "nya" input-system, som är modulärt och nu ska ersätta det gamla helt och hållet.

Strukturen ser ut så här:

* _Spelare_ har [UEnhancedInputLocalPlayerSubsystems](uenhancedinputlocalplayersubsystem.md), som är knutna till [UInputMappingContexts](uinputmappingcontext.md).
* UInputMappingContexts samlar ett antal [UInputActions](uinputaction/), som motsvarar handlingar spelaren kan göra (Jump, Move etc) och kopplar dem till knapptryck och andra kontroller (WASD, vänster styrspak, mellanslag).
* Spelare har kontrollen över [pawns](../apawn.md), och när något händer i en spelares input-subsystem så skickas detta till pawnens input-komponent.
* _Pawns_ har [UEnhancedInputComponents](uenhancedinputcomponent.md), som knyter UInputActions till specifika funktioner.
* Så när en spelare trycker på en knapp (mellanslag), så ser dess input-subsystem till, så att den Input Action (Jump) som är kopplad till den knappen i dess mapping context, aktiveras – och då den aktiveras så känner pawn:ens input-komponent av detta och kör rätt funktion.
  * Så Knapp → Subsystem (Context) → Action → Component → funktion

