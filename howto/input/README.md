# Input

## Det nya systemet: Enhanced Input

### Input Actions och Input Mapping Contexts

En **Input Action** är något karaktären ska kunna göra och som man vill kunna binda något till – t.ex. Move, Jump, Look osv.

En **Input Mapping Context** är en uppsättning bindningar mellan knappat och Input Actions

Båda dessa skapas i Unreal-editorn direkt. Högerklicka bland assets, tryck Input och Input Action resp. Input Mapping Context.

#### Input Actions

Det viktigaste är att bestämma en **Value Type**. Digital för knappar, Axis2D för sånt som ska styras av WASD, styrkors eller analoga spakar. Och Axis1D för t.ex. triggers om man vill kunna känna av hur mycket de är nedtryckta.

#### Input Mapping Contexts

Lägg till alla Input Actions som ska ingå.

För varje Input Action, lägg till de knappar som ska kopplas till den. För enkla grejer som Jump och Fire så behövs inget mer.

För 2D-axlar behöver man också lägga till Modifiers:

* Upp/ner behöver modifiern Negate.
* Vänster/ner behöver modifiern Swizzle Input Axis Values (YXZ).

<table><thead><tr><th width="136">Riktning</th><th>Modifiers</th></tr></thead><tbody><tr><td>Upp/W</td><td>Swizzle Input Axis Values</td></tr><tr><td>Ner/S</td><td>Negate, Swizzle Input Axis Values</td></tr><tr><td>Vänster/A</td><td>Negate</td></tr><tr><td>Höger/D</td><td>-</td></tr></tbody></table>

## Koppla rätt spelare till rätt Input Mapping Context

Har man tillgång till en ULocalPlayer-instans så kan man därifrån hämta en instans av det nya input-systemet, och sedan använda AddMappingContext för att koppla in rätt Input Mapping Context till just den spelaren.

Har man flera olika Input Action Contexts kopplade till samma spelare, så kan man ge dem olika prioritet; det är AddMappingContext-funktionens andra parameter.

### I en Pawn

Vill man samla allt i sin Pawn-klass så kan man göra kopplingen i klassens SetupPlayerInputComponent, eller i en egen metod som anropas från den.

{% code title="APawnClass.cpp" %}
```cpp
// Hämta PlayerControllern för den här Pawnen
const APlayerController* PlayerController = Cast<APlayerController>(GetController());
if (!PlayerController) return;

// Hämta spelaren som hör ihop med controllern
const ULocalPlayer* LocalPlayer = PlayerController->GetLocalPlayer();
if (!LocalPlayer) return;

// Hämta den instans av det nya input-subsystemet som är kopplat till spelaren
UEnhancedInputLocalPlayerSubsystem* InputSystem = LocalPlayer->GetSubsystem<UEnhancedInputLocalPlayerSubsystem>();
if (!InputSystem || InputMappingContext.IsNull()) return;

// Lägg till rätt Input Mapping Context till subsystemet.
InputSystem->AddMappingContext(InputMappingContext, 0);
```
{% endcode %}

### I en Player Controller

Man kan också skapa en subklass till UPlayerController och använda t.ex. en GameMode-blueprint för att koppla ihop UPlayern med den nya UPlayerControllern. Då kan bindningen göras i UPlayerControllerns konstruktor.

Då kommer man dock antingen behöva göra en blueprint-subklass till en UPlayerController för att kunna ange vilken Input Action Context som ska användas, eller används FObjectFinder för att hårdkoda en länk till rätt Input Action Context.

### Koppla Input Actions till funktioner

Börja med att override:a SetupPlayerInputComponent.

{% code title="APawnClass.h" %}
```cpp
virtual void SetupPlayerInputComponent(class UInputComponent* PlayerInputComponent) override;
```
{% endcode %}

{% code title="APawnClass.cpp" %}
```cpp
void APawnClass::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
	Super::SetupPlayerInputComponent(PlayerInputComponent);
	
	// Här skriver du sedan koden för att skapa kopplingar
}
```
{% endcode %}

Lägg också in variabler för din Input Mapping Context och för de Input Actions du vill koppla funktioner till.

{% code title="APawnClass.h" %}
```cpp
UPROPERTY(EditAnywhere, Category="Input")
UInputMappingContext* InputMappingContext;
	
UPROPERTY(EditAnywhere, Category="Input")
UInputAction* JumpInputAction;
	
UPROPERTY(EditAnywhere, Category="Input")
UInputAction* MoveInputAction;
```
{% endcode %}

När du sedan kompilerat så kan du koppla ihop dina assets med variablerna i editorn.

#### Funktioner att koppla till

Skapa funktioner som tar emot en `FInputActionInstance&`-parameter.

```cpp
void APawnClass::Move(const FInputActionInstance& Instance)
{
    FVector2d vector = Instance.GetValue().Get<FVector2D>();
    UE_LOG(LogTemp, Display, TEXT("Vector value: %s"), *vector.ToString());
}

void APawnClass::Jump(const FInputActionInstance& Instance)
{
    UE_LOG(LogTemp, Display, TEXT("Jump"));
}
```

#### FInputActionInstance

En Input Action som man bl.a kan läsa av värdet på. Praktiskt för att läsa av framför allt axlar.

{% code title="" %}
```cpp
float a = Instance.GetValue().Get<float>();
FVector b = Instance.GetValue().Get<FVector>();
FVector2D c = Instance.GetValue().Get<FVector2D>();
```
{% endcode %}

#### Skapa själva kopplingen

BindAction är funktionen i en UEnhancedInputComponent som används för att skapa en koppling mellan en Input Action och en metod.

Om Enhanced Input System är aktiverat så bör PlayerInputComponent-variabeln som skickas in som parameter i SetupPlayerInputComponent-funktionen vara just en UEnhancedInputComponent, men den behöver castas till den klassen.

{% code title="" %}
```cpp
EnhancedInputComponent* Input = Cast<UEnhancedInputComponent>(PlayerInputComponent);

Input->BindAction(JumpInputAction, ETriggerEvent::Started, this, &APawnClass::Jump);
Input->BindAction(MoveInputAction, ETriggerEvent::Triggered, this, &APawnClass::Move);
```
{% endcode %}

BindAction tar emot fyra parametrar: En UInputAction\*, den event som ska kopplas, och slutligen vilket objekts funktion som ska köras och vilken funktion som ska köras på det objektet.

De viktigaste event-typerna är **ETtriggerEvent::Started**, **ETtriggerEvent::Completed** och **ETtriggerEvent::Triggered**.

Started är när man trycker ner en knapp, Completed när man släpper upp den igen. Triggered körs varje frame som den är nedtryckt. De två första brukar användas för knappar, den sista för axlar t.ex. Move.

(Det finns en som heter Ongoing också, som gör nästan samma sak som Triggered – men Ongoing körs även om man lagt in någon form av delay eller annan modifikation).

## Det gamla systemet

### Axlar och actions

Axlar är lämpliga för inputs som ska ge variabla värden, alltså t.ex. vänster-höger eller upp-ner.

Actions är lämpliga för inputs som är mer omedelbara – en knapp som trycks ner. T.ex. hoppa, skjuta osv.

För att bestämma axlar och actions:

* Edit→Project settings
* Engine→Input
* Bindings; Action mappings och Axis mappings
* Skapa och döp axlar, actions
  * Axlar t.ex. MoveX, MoveY
  * Actions t.ex. Jump, Fire, Interact
* Koppla knappar till varje axel och action
  * Scale -1.0 för axlar vänster/ner

### Koppla axlar och actions till funktioner

Börja med att override:a SetupPlayerInputComponent.

{% code title="APawnClass.h" %}
```cpp
virtual void SetupPlayerInputComponent(class UInputComponent* PlayerInputComponent) override;
```
{% endcode %}

{% code title="APawnClass.cpp" %}
```cpp
void APawnClass::SetupPlayerInputComponent(UInputComponent* PlayerInputComponent)
{
	Super::SetupPlayerInputComponent(PlayerInputComponent);
	
	// Här skriver du sedan koden för att skapa kopplingar
}
```
{% endcode %}

#### Actions

Skapa en enkel metod – ingen returtyp, ingen parameter. Namnet spelar ingen roll.

{% code title="APawnClass.cpp" %}
```cpp
void APawnClass::StartPressing() // Och motsvarande i header-filen, såklart
{
    bGrowing = true;
}
```
{% endcode %}

Kör sedan BindAction i SetupPlayerInputComponent för att skapa kopplingen.

{% code title="" %}
```cpp
InputComponent->BindAction("Jump", IE_Pressed, this, &APawnClass::StartPressing);
```
{% endcode %}

Parametrarna är alltså namnet på actionen, vilken event som ska bindas, och slutligen vilket objekts funktion som ska köras och vilken funktion som ska köras på det objektet.

De två viktigaste eventen är **IE\_Pressed** och **IE\_Released**.

#### Axlar

Skapa en metod utan returtyp men som tar emot en floatparameter.

{% code title="APawnClass.cpp" %}
```cpp
void APawnClass::Move_XAxis(float AxisValue) // Och motsvarande i header-filen, såklart
{
	CurrentVelocity.X = FMath::Clamp(AxisValue, -1.0f, 1.0f) * 100.0f;
}
```
{% endcode %}

Kör sedan BindAxis i SetupPlayerComponent för att skapa kopplingen.

{% code title="APawnClass.cpp" %}
```cpp
InputComponent->BindAxis("MoveX", this, &APawnClass::Move_XAxis);
```
{% endcode %}

Parametrarna är alltså namnet på axeln, vilket objekts funktion som ska köras och slutligen vilken funktion som ska köras på det objektet.
