# USpringArmComponent

En komponent som skapar en flexibel "pistong" mellan två saker; oftast ett objekt och en kamera. Ärver från [USceneComponent](uscenecomponent.md).

## TargetArmLength

Pistongens maxlängd; längden den strävar efter att bli.

```cpp
SpringArmComp->TargetArmLength = 400.0f;
```

## Camera lag

Avgör ifall det ska finnas en fördröjning i hur kameran som sitter fast i pistongens "huvud" flyttas, och hur stor den fördröjningen ska vara. Fördröjningen ger en mjukare rörelse.

```cpp
SpringArmComp->bEnableCameraLag = true;
SpringArmComp->CameraLagSpeed = 3.0f;
```
