# Grids
Bislang hatten wir die Positionierung der einzelnen Block-Elemente mit __float__ kontrolliert. Für aufwändigere Layouts welche sich auf unterschiedlichen Screensizes ausrichten müssen, ist die Arbeit mit __float__ eher [mühsam](https://i.imgur.com/Q3cUg29.gif). Anfangs musste man Tabellen, dann Floats, Inline-Block usw. verwenden, aber alle diese Methoden waren im Wesentlichen Hacks und Funktionen wie z.B. vertikale Zentrierung waren äusserst aufwendig. 

[Grid CSS](https://www.w3schools.com/css/css_grid.asp) ist ein zweidimensionales Raster-System, d.h. es kann sowohl Spalten als auch Zeilen verarbeiten, im Gegensatz zu [Flexbox](https://www.w3schools.com/css/css3_flexbox.asp), welches weitgehend für eindimensionale Layouts verwendet werden -> sprich für einzeilige horizontale oder vertikale Layouts. 

Man kann die Eigenschaft __display: grid__ auf ein Container Element anwenden, wie z. B.

Hier findet ihr das [Starter-File](https://gist.github.com/fleshgordo/dea794faad8fd8c5b2849f1911ad9b84).

```html
<div class="container">
	  <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
</div> 
```

Das CSS dazu sieht so aus:

```css
.container {
    display: grid;
    grid-gap: 0px; /* definiert den Abstand zwischen den einzelnen Zellen */ 
}
```

Um nun Spalten und Zeilen zu definieren, gibt es die CSS Regeln [grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns) und [grid-template-rows](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows).

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
    grid-row-gap: 15px; /* definiert den Abstand zwischen den einzelnen Zeilen */ 
    grid-column-gap: 15px; /* definiert den Abstand zwischen den einzelnen Spalten */ 
}
```

Für die Spalten- sowie Zeilenhöhe können alle gängigen CSS Einheiten verwendet werden (%, px, pt, em, usw.). Für das Responsive Design ist die neue Einheit __fr__ recht praktisch. Sie teilt den verfügbaren Platz in proportionale Einheiten. Man kann Einheiten auch bunt durcheinandermischen:

```css
grid-template-columns: 100px 25% 1fr;
```

Folgendes Beispiel teilt den verfügbaren Platz in vier Blöcke, wobei der erste und letzte jeweils 25%, der mittlere 50% an Platz beanspruchen.

```css
grid-template-columns: 1fr 2fr 1fr;
```

Mit __repeat()__ ist es möglich ein Raster mit vielen Spalten (in diesem Fall 12) verkürzt zu schreiben:

```css
grid-template-columns: repeat(12,1fr);
```

Das Verhalten der einzelnen Zellen im Raster-System ist mit den CSS Eigenschaften __grid-column__ and __grid-row__ steuerbar. Einzelne Elemente können z. B. über mehrere Spalten "spannen". Das Grundgerüst sieht so aus:

```css
.item {
  grid-column: <start-line> / <end-line>;
  grid-row: <start-line> / <end-line>;
}
```

Dieses Item würde von der ersten Spalte bis zur vierten Spalten spannen:

```css
.item {
  grid-column: 1 / 4;
}
```

Die alternative Schreibweise wäre:

```css
.item {
  grid-column: 1 / span 2;
}
```

Beginne bei der ersten Spalte und "spanne" über zwei weitere Spalten.
Dasselbe kann natürlich auch auf die Zeilen angewandt werden:

```css
.item {
    grid-row: 1 / span 5;
}
```

Mit [align-items](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-align-items) und [justify-items](https://css-tricks.com/snippets/css/complete-guide-grid/#prop-justify-items) kann der Content innerhalb der Zelle (item) positioniert werden:
Mögliche Parameter sind durch das __|__ Zeichen getrennt:

```css
.item {
    align-items: start | end | center | stretch;
    justify-items: start | end | center | stretch;
}
```

## Weiterführende Links

  - [Wes Bos Online Kurs](http://cssgrid.io)
  - [CSS Grid Garden Game](https://cssgridgarden.com/)
  - [Rachel Andrew - GET READY FOR CSS GRID LAYOUT](https://abookapart.com/products/get-ready-for-css-grid-layout)
  - [CSS Tricks Artikel](https://css-tricks.com/snippets/css/complete-guide-grid/)