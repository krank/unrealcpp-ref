# Ändra property-värden

I script kan man exponera klassvariablers värden till Unreal-editorn genom att använda UPROPERTY, men man kan inte sedan ändra de värdena hur som helst.

## Objekt i spelvärlden

För instanser av klasserna som lagts in i spelvärlden, så syns variablerna i Details-panelen.

## Klasser i Content Drawer

Bara Blueprint-klasser kan redigeras i unreal-editorn; Details-panelen hanterar inte klasser i Content Drawer.

Därför skapar man BP-klasser som ärver från sina C++-klasser – de funkar som "wrappers" och gör properties redigerbara.

## Hårdkodade referenser till assets

Vill man helt undvika blueprints så kan alla properties ges värden i koden istället. Problemet uppstår när man vill ha en referens till en annan asset. Kan man inte skapa referensen via Unreal-editorn så får man stå ut med hårdkodade länkar istället.

<pre class="language-cpp"><code class="lang-cpp"><strong>static ConstructorHelpers::FObjectFinder&#x3C;UStaticMesh> CubeVisualAsset(
</strong><strong>    TEXT("/Script/Engine.StaticMesh'/Game/StarterContent/Shapes/Shape_Cube.Shape_Cube'"));
</strong>
if (!CubeVisualAsset.Succeeded()) return;

VisualMesh->SetStaticMesh(CubeVisualAsset.Object);
</code></pre>

FObjectFinder-objekt letar rätt på något i Assets. Man anger länken till den asset man vill ha som parameter till konstruktorn. Om Succeeded() returnerar true så gick det att hitta det man länkade.

För att få fram länktexten så högerklickar man på grejen i Content Drawer och väljer "Copy reference".

Object-variabeln innehåller sedan en pekare till objektet.

{% hint style="warning" %}
**Detta är inte rekommenderat!** Det blir ganska skör kod, där saker lätt går sönder ifall man organiserar om saker i Content drawer.
{% endhint %}
