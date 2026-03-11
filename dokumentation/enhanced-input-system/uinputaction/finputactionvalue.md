# FInputActionValue

Ett värde som en [UInputActionInstance](finputactioninstance.md) levererar från en aktiverad [FInputAction](./).

## Get<>()

Returnera värdet. Mellan <> skrivs datatypen som önska; bör matcha FInputAction-objektet som aktiverats.

<pre class="language-cpp"><code class="lang-cpp">void APawnWithCamera::OnMove(const FInputActionInstance&#x26; Instance)
{
  FinputActionInstance value = Instance.GetValue();
<strong>  FVector2D vector = value.Get&#x3C;FVector2D>();
</strong>}
</code></pre>
