# UEnhancedInputLocalPlayerSubsystem

Ett alternativt Input Subsystem för den lokala spelaren.

## AddMappingContext()

Kopplar en [UInputMappingContext](uinputmappingcontext.md) till systemet. Första parametern är kontexten, andra är vilken prioritet data från kontexten ska ges jämfört med andra.

```cpp
InputSystem->AddMappingContext(MappingContext, 0);
```

