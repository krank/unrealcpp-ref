# FRotator

Används för att beskriva en _rotation_. När man skapar dem kan man ange deras initiala _pitch_, yaw och _roll_.

{% code title="" %}
```cpp
FRotator rotation (60.0f, 0.0f, 0.0f);
```
{% endcode %}

## Vector()

Returnerar en [FVector](fvector.md) som pekar i samma riktning som FRotatorn.

{% code title="" %}
```cpp
FVector Direction = Rotation.Vector();
```
{% endcode %}

## GetInverse()

Returnerar en FRotator som pekar i motsatt riktning.

## Pitch

Beskriver rotationens uppåt/neråtvinkel. ↕

```cpp
Rotation.Pitch += CameraInput.Y;
```

## Roll

Beskriver rotationens sida-till-sidavinkel. ↔

```cpp
Rotation.Roll += 4.0f;
```

## Yaw

Beskriver rotationens vänster/högervinkel. ⭮ ⭯

```cpp
Rotation.Yaw += CameraInput.X;
```

