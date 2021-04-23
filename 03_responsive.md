# Responsive Design

Der [Viewport](https://responsivedesign.is/develop/responsive-html/viewport-meta-element/) des Browsers ist der Bereich des Fensters, in dem Webinhalte zu sehen sind. Dies ist oft nicht die gleiche Größe wie die komplette gerenderte Seite. Eine typische optimierte Website für "mobil-view" beinhaltet folgende Zeile in der __\<head>\</head>__ Sektion:

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Die width-Eigenschaft steuert die Größe des Viewports. Es kann auf eine bestimmte Anzahl von Pixeln  oder auf den speziellen Wert __device-width__ (e.q. Grösse des Bildschirms) gesetzt werden.

Die Eigenschaft __initial-scale__ steuert die Zoomstufe beim ersten Laden der Seite. Die Eigenschaften __maximum-scale__, __minimum-scale__, and __user-scalable__ steuern, wie Benutzer die Seite ein- oder auszoomen dürfen. Mehr Infos dazu bei [CSS-Tricks](https://css-tricks.com/snippets/html/responsive-meta-tag/).

## Media Queries

<img src="https://arambartholl.com/wwwppp/wp-content/uploads/2013/02/graphic-arrays-2-2000.jpg" width="640px"> Image (Graphic Arrays) by [Aram Bartholl](https://arambartholl.com/blog/graphic-arrays/), 2013

Mit Media Queries lassen sich verschiedene CSS Parameter in Abhängigkeit von Bildschirmauflösung und Orientierung der aktuellen Browsergrösse (z.B. Smartphone-Bildschirm vs. Computerbildschirm) anpassen. Es wurde im Juni 2012 vom W3C zum empfohlenen Standard und ist unumgänglich für das Arbeiten im Responsive Design. Das Ziel von Responsive Design ist Webseiten zu erstellen, die die Bildschirmgröße und Ausrichtung erkennen und das Layout entsprechend ändern. 

<img src="https://cdn-images-1.medium.com/max/2400/1*7YeOvzoYgUEDJdfQy2ERXg.png" width="640px">
Diagram taken from [David Gilbertson](https://medium.freecodecamp.org/the-100-correct-way-to-do-css-breakpoints-88d6a5ba1862)

Eine Media Query besteht aus einem Medientyp und einem oder mehreren Ausdrücken die wahr bzw. falsch sein können, je nach Endgerät. Das Ergebnis der Media Query ist wahr, wenn der in der Medienabfrage angegebene Medientyp mit dem Gerätetyp übereinstimmt. Wenn die Bedingung der Media Query wahr ist (true), dann werden die darinstehenden CSS Regeln angewandt.

Um z. B. ein bestimmtes CSS zu laden wenn ein Querformat vorliegt:

```css
@media all and (orientation: landscape) {
  /* der Code wird nur auf Querformat angewandt (Länge grösser als Breite */
}
```

Das zweite Wort nach __@media__ regelt welche Devices von der Media Query adressiert werden sollen. Es gibt __all__, __screen__, __print__ und __speech__. Hier die ganze [Liste](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) und ihre Bedeutungen.

```css
@media all and (orientation: landscape) {
  /* der Code wird nur auf Querformat angewandt (Länge grösser als Breite */
}

@media screen and (min-width: 640px) {
  /* das CSS wird nur geladen wenn das Gerät mind. 640px Breite hat */
}
```

Mit dem Wort __and__ kann man Media Queries auch verknüpfen:

```css
@media all and (min-width: 640px) and (max-width: 800px){
  /* das CSS wird nur geladen wenn das Gerät mind. 640px
  und maximal 800px breit ist */
}
```

Oder z. B. die Screengrösse und die Ausrichtung:

```css
@media all and (min-width: 640px) and (orientation: landscape) { 
   /* das CSS wird nur geladen wenn das Gerät mind. 640px Breite 
   und im Querformat ist */ 
}
```

## Weiterführende Links

  - [Breakpoints.css Beispiel](https://gist.github.com/caocaostudio/365a20e68daaf8e7bcba264523560201) Welcome to the world of mobile responsive Design
  - [MaintainableCSS](https://maintainablecss.com)
  - [What units (em vs. px) for media queries](https://zellwk.com/blog/media-query-units/)