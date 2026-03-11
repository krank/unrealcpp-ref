# Namngivning\*

**CamelCase** används för _all namngivning_, dvs första bokstaven i varje ord är versal.

**Undantaget är bool-variabler**, som ska ha ett litet b i början (`bool bHasFinished`).

**Klasser/typer** namnges med en extra bokstav i början, ett _prefix_, för att skilja dem från variabler.

<table><thead><tr><th width="200">Klass/typ</th><th width="91">Prefix</th><th>Exempel</th></tr></thead><tbody><tr><td>Template-klass</td><td>T</td><td><code>template &#x3C;typename T> class TAttribute {</code></td></tr><tr><td>Ärver från UObject</td><td>U</td><td>class UActorComponent</td></tr><tr><td>Ärver från AActor</td><td>A</td><td>class ASpaceShip</td></tr><tr><td>Ärver från SWidget</td><td>S</td><td>class SButtonWidget</td></tr><tr><td>Abstrakta interfaces</td><td>I</td><td>class IBuildable</td></tr><tr><td>Enum</td><td>E</td><td>enum class EAnimationState</td></tr><tr><td>Övriga</td><td>F</td><td>class F</td></tr></tbody></table>

