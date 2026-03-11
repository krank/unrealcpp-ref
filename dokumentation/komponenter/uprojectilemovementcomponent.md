# UProjectileMovementComponent\*

En komponent för att förflytta ett objekt som en projektil.

{% code title="AProjectile.h" %}
```cpp
UProjectileMovementComponent* ProjectileMovement;
```
{% endcode %}

{% code title="AProjectile.cpp" %}
```cpp
ProjectileMovement = 
  CreateDefaultSubobject<UProjectileMovementComponent>(TEXT("Projectile Movement"));
```
{% endcode %}

## InitialSpeed

Projektilens initiala hastighet

## MaxSpeed

## bShouldBounce
