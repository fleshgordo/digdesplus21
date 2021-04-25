# Einführung jQuery

## Übersicht

jQuery ist lediglich ein "Framework", das JavaScript für Entwickler deutlich effizienter macht, und das dank zahlreicher fertiger Plugins arbeitsintensive und fehleranfällige Eigenentwicklungen häufig überflüssig macht. Beliebt ist es vor allem bei Interface Designer, um rasch Protoypen zu bauen, wobei Frontend-Ingenieure lieber mit anderen (für Einsteiger recht komplexe) Frameworks wie z. B. ReactJS oder AngularJS bevorzugen.

Auch die zahlreichen, teils mächtigen Plugins tragen zum Erfolg von jQuery bei. Egal ob Aufklappmenüs, Akkordeons, Diashows, Registerkarten, Wysiwyg-Editor oder HTML5-fähige Audio- und Video-Player – die Plugins sind meist so konzipiert, dass eine oder ein paar Zeilen Code zum Einbinden genügen.

## Einbindung

Man kann jQuery wahlweise herunterladen und dann wieder auf Ihren eigenen Web-Space hochladen, damit es Webseiten von dort aus lokal laden. Die Alternative ist, jQuery direkt über einen hochverfügbaren Google-Server einzubinden.
```html
<script src="/scripts/jquery/jquery-1.11.0.min.js"
type="text/javascript"></script>
```

Die Einbindung über einen Google Server würde wiefolgt aussehen:

```html
<script src="http://ajax.googleapis.com/ajax/libs/jquery/1.11.0/jquery.min.js"
  type="text/javascript"></script>
```

Mehr Infos zum Laden via einen CDN Server [hier](https://developers.google.com/speed/libraries#jquery)

## Das jQuery Objekt oder $

Als „typisch“ für jQuery gilt das $-Zeichen im Code. Es handelt sich dabei um gewöhnliches JavaScript. So ist unter anderem auch das $-Zeichen als Namensbestandteil erlaubt. Und genau davon macht jQuery Gebrauch. Das Framework fügt dem window Objekt eine globale Funktion und ein globales Objekt mit dem Namen $ hinzu. Über die globale jQuery-Funktion $() ist der Zugriff auf das HTML-Dokument möglich.

```js
var jetzt = $.now();
console.log(jetzt);
```

Mit $(document) spricht man das HTML-Dokument als Objekt an. Ein wichtige Methode, die jQuery für das document-Objekt bereit stellt, ist ready(). Es handelt sich um einen Ereignis-Handler. Damit erreicht man, dass der Code erst dann ausgeführt wird, wenn das DOM vollständig geladen ist.
Vergleiche die beiden Zeitpunkte:
```js
// A $( document ).ready() block.
$( document ).ready(function() {
    console.log( "ready!" );
});
```

## Auswahl von Elementen, Typ Selektoren

Bevor wir irgend etwas mit irgendwelchen Elementen anstellen können, müssen wir das gewünschte Element erst auswählen.

jQuery spielt seinen Bonus über das Auswählen (selektieren) von Elementen aus. Hier werden alle h1 Elemente innerhalb des HTML Dokuments ausgewählt und ihr Inhalt geändert.

```html
<html>
<head>
  <title>jQuery Beispiel</title>
  <script src="https://code.jquery.com/jquery-latest.js"></script>
  <script>
  $(document).ready(function(){
      $("h1").html("Hello cat!");
  });
  </script>
</head>

<body>
  <h1>Hello world!</h1>
</body>
</html>
```

Man kann aber auch Werte, Attribute und Eigenschaften von Elementen abrufen und verwenden:

```html
<html>
<head>
  <title>jQuery Beispiel</title>
  <script src="https://code.jquery.com/jquery-latest.js"></script>
  <script>
  $(document).ready(function(){
      var inhalt = $("p");
      $("h1").html(inhalt);
  });
  </script>
</head>

<body>
  <h1>Hello world!</h1>
  <p>Swap me!</p>
</body>
</html>
```

Je komplizierter die Seite wird, desto genauer muss man einzelne Elemente auswählen, indem man direkt auf ihre Klassen und/oder IDs zugreift. Wir wollen nun über jQuery auf IDs und Klassen zugreifen um gezielt Elemente auswählen zu können. Zur Erinnerung an die IDs. Eine ID ist eindeutig und kommt nur einmal pro HTML-Seite vor.

```html
<p id="absatz1">Erster Absatz</p>
<p id="absatz2">Zweiter Absatz</p>
```

Im Gegensatz zur ID können Klassen bei mehr als einem Element und gleichzeitig bei verschiedenen Elementen eingesetzt werden. Ein Element kann auch mehr als eine Klasse haben.

```html
<p class="absatz wichtig">
```
Klassenattribute werden bei CSS und jQuery mit einem . (Punkt) angesprochen.

Prinzipiell gibt es unterschiedliche Arten Objekte mit dem jQuery Selektor aufzurufen.

```js
$("#id")
$(".klasse")
$("div, p, a, span, li")
```

```html
<html>
<head>
  <title>jQuery Beispiel</title>
  <script src="https://code.jquery.com/jquery-latest.js"></script>
  <script>
  $(document).ready(function(){
      $('.abschnitt').text('Text der Klasse abschnitt ersetzt');
  });
  </script>
</head>

<body>
  <p class="abschnitt" id="absatz1">Erster <b>wichtiger</b> Absatz</p>
  <p class="abschnitt" id="absatz2">Zweiter Absatz</p>
  <p class="abschnitt">dritter Absatz</p>
  <p>vierter Absatz</p>
  <p class="abschnitt">fünfter Absatz</p>
</body>
</html>
```

Alle Elemente der Klassen „abschnitt“ (nicht der vierte Absatz, der ist nicht der Klasse „abschnitt“ zugehörig) wurde über jQuery mit einem neuen Inhalt ersetzt.

Wollen wir nun gezielt eine davon ansprechen, ist dies auch möglich über folgende Vorgehensweise:

- :first
- :last
- :even
- :odd
- :eq(x)	Beispiel :eq(2)
- :gt(x)	Beispiel :gt(2) -> größer als 2
- :lt(x)	Beispiel :lt(2) -> kleiner als 2
- :nth-child(3) - ist wirklich das 3. – bei :eq wird bei 0 angefangen zu zählen (sprich wir würden :eq(2) für dasselbe Ergebnis benötigen!)

In der Anwendung sieht das so aus:

```js
$('.abschnitt:first').text('Text der Klasse abschnitt ersetzt');
```

Aufgabe: jeder zweite Absatz soll geändert werden. Tipp :odd bedeutet alle ungeraden Elemente, also 1,3,5 etc. und :even alle geraden Elemente 0,2,4 etc.

## CSS per Javaskript verändern

Wir können auch direkt über jQuery auf die CSS-Eigenschaften zugreifen. Wollen wir beispielsweise alle p in rot anzeigen, funktioniert das über
die css() Funktion:
```js
$('p').css('background-color', 'rot');
```

Allerdings sollte man nicht CSS direkt in jQuery einbauen, da die Wartung sehr schnell sehr unübersichtlich wird. Die richtige Vorgehensweise ist, dass man die Designanweisungen von dem CSS File nimmt. Dies geschieht so z. B. in der CSS Datei definiert man eine Klasse:

```js
.fehler { color: red; }
```

Mit jQuery kann man nun diese CSS Klasse zuweisen:

```js
$('p').addClass('fehler');
```

Falls man nun diese Klasse wieder entfernen möchte, dann benutzt man die Funktion removeClass():

```js
$('p').removeClass('fehlerhinweise');
```

Das Ganze wird dann interessant, wenn man auf das User-Verhalten reagiert. Wir sehen uns nun an, wie man Mausklicks auswertet und darauf dann reagiert.

## Detektieren von Ereignissen

Sobald der User mit der Website interagiert, werden gewisse Events getriggert. Man kann diese Events nun an Elemente "binden"

```js
$('p').on('click', function() {
  $(this).toggleClass('fehler');
});
```

Hier eine Auflistung der Events, welche mit jQuery detektiert werden können:

 - **UI focus** blur, change
 - **KEYBOARD** input, keydown, keyup, keypress
 - **MOUSE** click, dblclick, mouseup, mousedown, mouseover, mousemove, mouseout, hover
 - **FORM** submit, select, change
 - **DOCUMENT** ready, load, unload
 - **BROWSER** error, resize , scroll


Jeder Event Trigger enthält zusätzlich noch Eigenschaften und Funktionen zu dem Event. Dieser wird automatisch der Funktion übergeben:

```js
$('p').on('click' function(e)
  eventType = e.type;
  console.log(e);
});
```

Seht euch die Eigenschaften und Methoden von e an. Es gibt eine Methode, die preventDefault() heisst, welche die normale Ausführung einer Interaktion verhindert (z. B. submit von einem Formular).

Versuche die Interaktion mit einem Element über den mouseover und mouseout Event Trigger zu gestalten. Was muss man dabei beachten?

## Animation und Sichtbarkeit von Elementen

Man kann mit jQuery auch Effekte auf einzelne Elemente anwenden. So kann man Elemente aus- und einfaden lassen, gänzlich verschwinden oder bewegen lassen. Die Grundfunktionen lauten:

```js
.show() //  Displays selected elements
.hide() // Hides selected elements
.toggle() // Toggles between showing and hiding selected elements
```

Folgende "fading" Effekte stehen zur Verfügung

```js
.fadeIn() // Fades in selected elements making them opaque
.fadeout() // Fades out selected elements making them transparent
.fadeTo() // Changes opacity of selected elements
.fadeToggle() // Hides or shows selected elements by changing their opacity (the opposite of their current state)
```

Und sliding Effekte
```js
.slideUp() // Shows selected elements with a sliding motion
.slideDown() // Hides selected elements with a sliding motion
.slidedeToggle() // Hides or shows selected elements with a sliding
motion (in the opposite direction to its current state)
```

Und spezielle Animationen:
```js
.delay()  // Delays execution of subsequent items in queue
.stop() // Stops an animation if it is currently running
.animate() // Creates custom animations
```

Mit dem letzten Befehl [animate](http://api.jquery.com/animate/) kann man CSS Regeln animieren lassen:

```
$("#target").animate({width : "200px"},500);
```

Achtet auf die geschwungenen Klammern {}. Der zweite Wert definiert die Zeit der Animation in Millisekunden (500ms = 0.5sec).

Man kann gleichzeitig mehrere Regeln verändern:
```js
$("#target").animate({
  width : "200px",
  opacity : 0.5,
  height: "50px"
}, 250);
```

Problematisch wird es manchmal, wenn man eine Animation an einen Event bindet (z.B. mouseover) und dieser mehrere Male hintereinander "feuert" bevor die Animation noch beendet ist. Dazu kann man einfach den Befehl [stop()](https://api.jquery.com/stop/) in die jQuery "Chain" hinzufügen.

```js
$("#target").stop().slideDown(250);
```

## Automatisiertes Scrollen

```js
$(document).ready(function() {
   $("body, html").animate({"scrollTop": $("#block").scrollTop()},2000);
});
```

Es gibt aber auch ein Plugin, dass einem die Arbeit und das Umrechnen ein wenig abnehmen kann.

http://stackoverflow.com/questions/6677035/jquery-scroll-to-element