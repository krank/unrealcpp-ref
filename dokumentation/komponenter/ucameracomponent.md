# UCameraComponent

En komponent som visar spelvärlden från ett visst perspektiv; agerar "kamera". Ärver från [USceneComponent](uscenecomponent.md).

## bUsePawnControlRotation

En bool som avgör ifall kameran ska följa rotationen för den [APawn](../apawn.md) den sitter på.

```cpp
FirstPersonCameraComponent->bUsePawnControlRotation = true;
```

## FieldOfView

En float som avgör kamerans FOV i grader.

```cpp
CameraComp->FieldOfView = 90.0f;
```

## Förstapersonsperspektiv

Kamerakomponenten har ett inbyggt system för att göra skillnad på sådant som ska vara väldigt nära kameran och sådant som ska tillhöra "världen". Detta gör bl.a att vapen inte glider in i väggar.

Man markerar vilka [UPrimitiveComponents](uprimitivecomponent/) som ska räknas som förstapersonsobjekt genom att ge dem First Person som FirstPersonPrimitiveType.

### bEnableFirstPersonFieldOfView

En bool som avgör ifall kameran ska använda olika FOV för förstapersonsobjekt.

```cpp
FirstPersonCameraComponent->bEnableFirstPersonFieldOfView = true;
```

### bEnableFirstPersonScale

En bool som avgör ifall kameran ska använda olika skalning för förstapersonsobjekt.

```cpp
FirstPersonCameraComponent->bEnableFirstPersonScale = true;
```

### FirstPersonFieldOfView

En float som beskriver vilken FOV som ska användas för förstapersonsobjekt (om bEnableFirstPersonFieldOfView är true).

```cpp
FirstPersonCameraComponent->FirstPersonFieldOfView = 70.0f;
```

### FirstPersonScale

En float som beskriver vilken skalning som ska användas för förstapersonsobjekt (om bEnableFirstPersonScale är true).

```cpp
FirstPersonCameraComponent->FirstPersonScale = 0.6f;
```

