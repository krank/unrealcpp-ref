# FVector

Används oftast för att ange något som ska ha X, Y och Z-värden, t.ex. en position eller en förflyttning i 3D.

{% code title="" %}
```cpp
FVector Vec = FVector(0.0f, 45.0f, 60.0f);
```
{% endcode %}

### FVector2D

En variant av FVector som bara har X- och Y-komponenter.

```cpp
FVector2D Vec2d = FVector2D(0.0f, 45.0f);
```

### X, Y, Z

Vektorns X, Y och Z-komponenter

### Size/Length

```cpp
int32 t = Vec.Size()
```

### Normalize()

Normalisera vektorn (går så att den pekar i samma riktning, men så dess längd blir 1).

```cpp
Vec.Normalize();
```

### GetSafeNormal()

Skapa en normaliserad kopia av vektorn.

{% code title="" %}
```cpp
FVector vec2 = Vec.GetSafeNormal();
```
{% endcode %}

### GetClampedToMaxSize()

Skapa en kopia vars längd är begränsad till ett givet värde.

{% code title="" %}
```cpp
FVector vec3 = vec2.GetClampedToMaxSize(2.0f);
```
{% endcode %}

### IsNormalized()

Returnerar true om vektorns magnitud är 1.

### IsZero()

Returnerar true om vektorns magnitud är 0.

### IsNearlyZero()

Returnerar true om vektorns magnitud är 0 eller väldigt nära.

### Rotation()

Returnerar en FRotator som pekar i samma riktning som vektorn.
