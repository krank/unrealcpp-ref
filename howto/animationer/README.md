# Animationer\*

## Påverka animationer från C++

Varje USkeletalMeshComponent har normalt ett USkeletalMesh och sedan en UAnimInstance (Animation Blueprint) som driver dess animationer.

I Animation Blueprints används ofta variabler för att driva övergångar mellan animationer. De kan man normalt inte komma åt från C++.

För att det ska funka, skapa en subklass till UAnimInstance som har variablerna som ska påverkas, och skapa sedan en Animation Blueprint baserat på den subklassen.

{% code title="UArmsAnimInstance.h" %}
```cpp
UCLASS()
class MYPROJECT_API UArmsAnimInstance : public UAnimInstance
{
    GENERATED_BODY()
    
public:
    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category="Variables")
    float Speed;
};
```
{% endcode %}

Sedan kan man använda Cast och GetAnimInstance för att få tag på UAnimInstance:n och ändra variablerna.

```cpp
UArmsAnimInstance* Animator = Cast<UArmsAnimInstance>(FirstPersonMesh->GetAnimInstance());
Animator->Speed = GetVelocity().Length();
```
