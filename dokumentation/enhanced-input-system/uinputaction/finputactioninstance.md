# FInputActionInstance

FInputActionInstances är objekt som kommer från [Input Actions](./) och som bl.a. innehåller information om deras nuvarande värde. De dyker oftast upp som parametervärden i funktioner som knutits till Input Actions via en [UEnhancedInputComponent](../uenhancedinputcomponent.md).

## GetValue()

Returnerar action-instansens nuvarande värde, som ett FinputActionValue.

<pre class="language-cpp"><code class="lang-cpp">void APawnWithCamera::OnMove(const FInputActionInstance&#x26; Instance)
{
<strong>    FInputActionValue value = Instance.GetValue();
</strong>}
</code></pre>
