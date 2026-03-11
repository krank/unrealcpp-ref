# UPROPERTY

Används i header-filer för att ange exponera en _variabel_ till Unreal-editorn. Motsvarar \[SerializeField] i Unity.

{% code title="" %}
```cpp
UPROPERTY(EditAnywhere)
int32 HitPoints;
```
{% endcode %}

Mellan parenteserna anges en specifier och eventuella extra inställningar/tillval.

## Specifiers: Edit/Visible/Blueprint

<table><thead><tr><th width="177.99993896484375">Specifier</th><th>Effekt</th></tr></thead><tbody><tr><td><code>EditAnywhere</code></td><td>Kan redigeras både i asset-objektet och i instanser i scenen.</td></tr><tr><td><code>EditInstanceOnly</code></td><td>Kan bara redigeras i instanser i scenen.</td></tr><tr><td><code>EditDefaultsOnly</code></td><td>Kan bara redigeras i asset-objektet.</td></tr><tr><td><code>VisibleAnywhere</code></td><td>Kan ses (inte redigeras) både i asset-objektet och i instanser i scenen.</td></tr><tr><td><code>VisibleInstanceOnly</code></td><td>Kan bara ses (inte redigeras) i instanser i scenen.</td></tr><tr><td><code>VisibleDefaultsOnly</code></td><td>Kan bara ses (inte redigeras) i asset-objektet.</td></tr><tr><td><code>BlueprintReadOnly</code></td><td>Kan bara läsas, inte ändras på, i en blueprint (bara för publika variabler)</td></tr><tr><td><code>BlueprintReadWrite</code></td><td>Kan läsas och ändras på i en blueprint (bara för publika variabler)</td></tr></tbody></table>

## Category

Bestämmer ifall variabeln ska läggas i någon särskild kategori, dvs under någon rubrik, i editorn.

{% code title="" %}
```cpp
UPROPERTY(EditAnywhere, Category="Health")
int32 MaxHealth;

UPROPERTY(VisibleAnywhere, Category="Health")
int32 CurrentHealth;
```
{% endcode %}
