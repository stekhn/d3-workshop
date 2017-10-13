# D3-Workshop

## Was ist D3

D3 = Data-Driven Documents

D3 ist eine JavaScript-Bibliothek zur Visualisierung von Daten. D3 hilft dabei, Datensätze mit SVG, Canvas und HTML zum Leben zu erwecken. Im Gegensatz zu vielen anderen Bibliotheken ermöglicht D3 eine große Kontrolle über das endgültige visuelle Ergebnis.

D3 wird auf Hunderten von Tausenden von Webseiten verwendet. Typische Anwendungsfälle sind das Erstellen von interaktiven Grafiken, Dashboards und Karten. Darüber hinaus ermöglicht das Grafikformat SVG die Weiterverwendung und Nachbearbeitung von Grafiken für den Druck.

D3 erfordert viel Erfahrung im Umgang mit modernen Webstandards und Funktionen der Bibliothek. Daher ist die Produktion von Grafiken teilweise recht aufwendig.

- Offizielle Webseite: https://d3js.org/
- Dokumentation: https://github.com/d3/d3/blob/master/API.md
- Beispiele: https://github.com/d3/d3/wiki/Gallery
- Tutorials: https://github.com/d3/d3/wiki/Tutorials

## Installation

Um die Beispiele verwenden und verändern zu können, empfiehlt es sich [Node.js](https://nodejs.org/en/) zu installieren. Node.js ist eine JavaScript-Umgebung für die Kommandozeile und für alle Betriebssystem verfügbar. In diesem Workshop werden wir Node.js verwenden, um eine kleinen Webserver für Entwicklungszwecke aufzusetzen. 

1. [Node.js](https://nodejs.org/en/) installieren. Wenn alles geklappt hat, sollte man in der Kommandozeile den Befehl `node --version` aufrufen können.
2. Erforderliche Pakete mit dem Node.js-Paketmanager [NPM](https://www.npmjs.com/) installieren. Dazu in das Hauptverzeichnis dieses Projekts gehen und `npm install` ausführen. Welche Pakete Node.js installieren soll, ist in der Datei `package.json` festgelegt.
3. Webserver starten mit `npm start`. Jetzt sollte ein Browserfenster unter der Addresse http://127.0.0.1:8080/ aufgehen. Die Beispiele zu diesem Workshop finden sich im Ordner `examples`.

Optional:
4. Einen sogenannten *Linter* installieren, der JavaScript-Fehler schon im Code-Editor anzeigt. Für diesen Workshop verwenden wir ESLint. Für Sublime Text muss man nur noch die Erweiterungen [SublimeLinter](https://packagecontrol.io/packages/SublimeLinter) und [SublimeLinter-contrib-eslint](https://packagecontrol.io/packages/SublimeLinter-contrib-eslint) installieren. Am einfachsten geht das mit dem Sublime-Paketmanager [Packagecontrol](https://packagecontrol.io/installation).

## D3 einbinden

Man kann D3 entweder von einer externen Seite oder lokal einbinden.

Einbinden von der offiziellen Seite:

```html
<script src="https://d3js.org/d3.v4.min.js"></script>
```

Einbinden von einem CDN (Content Delivery Network), welches auf die schnelle Bereitstellung von Paketen optimiert ist:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/d3/4.11.0/d3.min.js"></script>
```

Einbinden einer lokalen Version von D3:

```html
<script src="../node_modules/d3/build/d3.min.js"></script>
```

In diesem Fall wurde die D3 mithilfe des Paketmanagers NPM installiert `npm install d3`. Man könnte aber D3 auch einfach herunterladen.

Üblicherweise bindet man Bibliotheken im `<head></head>` Bereich einer Website ein. So stellt man sicher, dass die durch die Bibliothek bereitgestellten Funktionen von Anfang verfügbar sind.


## Selektoren

D3 verfügt über zwei Methoden, wie man Elemente in einem Dokument auswählen kann. Wenn man ein Element ausgewählt hat, kann man dieses beispielsweise mit Inhalten befüllen, löschen oder ein Klickverhalten festlegen.

Ein Element auswählen:

```javascript
var chart = d3.select('#chart')
```

Mehrere Elemente auswählen:

```javascript
var charts = d3.selectAll('.chart')
```

Die wichtigsten Selektoren:

- `body`: Element über Tag auswählen
- `#chart`: Element/e über ID auswählen
- `.chart`: Element/e über Klasse auswählen
- `[chart=bar]`: Element/e über Attribut auswählen
- `#chart.bar`: Element/e über ID und Klasse auswählen
- `#chart .bar`: Element/e über Parent-ID und Klasse auswählen


Vergleichbar mit den nativen Methoden `document.querySelector('#chart')` und `document.querySelectorAll('.chart')`, die jeder moderne Browser unterstützt.

Diese Selektoren würde man auch verwenden, um Elemente mit CSS zu stylen:

```css
.chart {
  background: beige;
}
```

## Attribute erstellen

Um ein Element zu erstellen, verwendet man die Funktion `d3.append()`. Diese wird auf einen Selektion angewandt, der das neue Element hinzugefügt wird. Damit kann man alle Arten von DOM-Elementen erstellen.

Einfaches HTML-Beispiel.

```javascript
d3.select('body')
  .append('h1')
    .text('Überschrift');
```

Das resultierende Markup sieht folgendermaßen aus:

```html
<body>
  <h1>Überschrift</h1>
</body>
```

Mit dem sogenannten *Method Chaining*, lassen sich mehrere Elemente hintereinander hinzufügen und Attribute setzen. In diesem SVG-Beispiel Wird erste der `<body></body>` eines HTML-Dokuments ausgewählt, dann eine SVG hinzugefügt. Diesem SVG wird wiederum ein rotes Dreieck hinzugefügt:  

```javascript
d3.select('body')
  .append('svg')
    .attr('width', 160)
    .attr('height', 160)
  .append('rect')
    .attr('x', 5)
    .attr('y', 5)
    .attr('width', 150)
    .attr('height', 150)
    .attr('fill', 'red');
```

Das resultierende Markup sieht folgendermaßen aus:

```html
<body>
  <svg width="600" height="160">
    <rect x="5" y="5" width="150" height="150" fill="red"></rect>
  </svg>
</body>
```

## SVG Elemente und Attribute

Hier eine kleine Übersicht über die wichtigsten SVG-Elemente:

```svg
<rect x="0" y="0" width="100" height="100" />
<circle cx="100" cy="100" r="100" />
<ellipse cx="100" cy="100" rx="100" ry="50" />
<polygon points="128,0 256,256 0,256" />
<line x1="0" y1="0" x2="256" y2="256" />
<path d="M100,160 Q128,190 156,160" />
<text x="100" y="100" text-anchor="start">Text</text>
```

Die Attribute `x`, `y`, `cx`, `cy`, `r` und so weiter sind vor allem dazu da, die Position und Größe einen Elements festzulegen.

Außerdem gibt es noch die Möglichkeit Elemente zu gruppieren. Das hilft dabei Ordnung zu schaffen, ein Style auf mehrere Elemente anzuwenden oder eine Gruppe von Elemente zu verschieben:

```svg
<g fill="red" style="transform: translate(10,10);">
  <circle cx="10" cy="10" r="10" />
  <circle cx="30" cy="10" r="10" />
  <circle cx="50" cy="10" r="10" />
</g>
```

Die meisten dieser Elemente können außerdem Attribute haben, die das Design festlegen:
- `fill`: Füllfarbe, zum Beispiel `red`
- `fill-opacity`: Deckkraft zwischen `1` und `0`
- `stroke`: Konturfarbe, zum Beispiel `green`
- `stroke-width`: Dicke der Kontur, zum Beispiel `2` 
- `stroke-opacity`: Deckkraft der Kontur zwischen `1` und `0`

Außerdem können SVG-Elemente, wie HTML auch, mit CSS gestylt werden:

```css
.axis line {
  fill: none;
  stroke: #6c3;
  stroke-width: 2;
}
```

Ein praktisches SVG-Cheat-Sheet gibt es [hier](https://learn-the-web.algonquindesign.ca/topics/svg-cheat-sheet/).

## Dynamische Attribute setzen

D3 ermöglicht es die Attribute von Elementen (Inhalt, Position, Größe oder Aussehen) dynamisch zu setzen.

In diesem Beispiel wird eine neuer Paragraph erzeugt, dessen Inhalt eine zufällig Zahl zwischen 1 und 10 ist:

```javascript
d3.select('body')
  .append('p')
    .text(function () {
      return 'Zufällige Zahl: ' + Math.round((Math.random() * 10) + 1);
    });
```

Diese Eigenschaft ist sehr praktisch, wenn man programmatisch Elemente hinzufügt, deren Eigenschaften sich entsprechend der zugrundeliegenden Daten verändern sollen.

## Daten verwenden

Die Fähigkeit Daten in Elemente zu verwandeln ist die große Stärke von D3. Das grundlegende Muster dafür ist immer das gleiche.


Alles beginnt mit einem Array, einer sortierten Liste, welches die Daten enthält:

```javascript
var data = [5, 10, 25, 40];
```

Für jede Zahle im Array `data` wird ein neuer Paragraph erstellt, der diese Zahl beinhaltet:

```javascript
var data = [5, 10, 25, 40];

d3.select('body').selectAll('p')
    .data(data)
    .enter()
  .append('p')
    .text(function (d) {
      return 'Wert: ' + d;
    });
```

**Hinweis**: Das `.selectAll('p')` am Anfang wird benötigt, obwohl es noch gar keine Paragraphen gibt.

Wir können die Werte aus dem Array `data` auch verwenden, um ein einfaches Diagramm zu zeichnen:

```javascript
var data = [5, 10, 25, 40];

d3.select('body')
  .append('svg').selectAll('circle')
    .data(data)
    .enter()
  .append('circle')
    .attr('cx', function (d) {
      return 15 + d;
    })
    .attr('cy', 15)
    .attr('r', 10); 
```

Die verwendete Funktion ist ein sogenannte *Accessor*. Wenn ein oder mehrere Elemente mit einem Datensatz verbunden sind, liefert uns der Accessor immer den jeweiligen Datensatz und Index des zu erzeugenden Elements:

```javascript
function (d, i) {
  console.log('Werte:', d)
  console.log('Index:', i)

  return d;
} 
```

Die Funktion `console.log()` kann praktisch sein, um Fehler im Programmcode zu finden (*debuggen*). Werden überhaupt Werte ausgegeben und wenn ja, sind es die richtigen?

## Daten aus externen Quellen laden
Mithilfe von D3 kann man auch Daten aus CSV- oder JSON-Dateien laden. Wichtig dabei ist, dass diese Dateien korrekt formatiert sind.

CSV-Datei laden:

```javascript
d3.csv('data.csv', function (data) {
  console.log(data);
});
```

Da das CSV-Format keine Informationen beinhaltet, ob einen Spalte Zahlen (*Integers*, *Floats*) oder Zeichenfolgen (*String*) enthält muss man diese zuerst in richtige Format konvertieren:

```javascript
d3.csv('data.csv', function (data) {
  data = data.map(function (d) {
    return {
      name: d.name,
      age: parseInt(d.age) 
    };
  });
});
```

JSON-Datei laden:

```javascript
d3.json('data.json', function (data) {
  console.log(data);
});
```

Das Laden der Daten passiert asynchron. Deshalb kann man nur innerhalb des *Callbacks* (`function (data) {}`) mit den Daten arbeiten. Diese Callback-Funktion kann man auch getrennt definieren:

```javascript
d3.json('data.json', drawCircles);

function drawCircles(data) {

  d3.select('body')
    .append('svg').selectAll('circle')
      .data(data)
      .enter()
    .append('circle')
      .attr('cx', function (d) {
        return 15 + d;
      })
      .attr('cy', 15)
      .attr('r', 10); 
}
```

**Hinweis:** Um Daten dynamisch nachladen zu können, muss die Anwendung über einen (lokalen) Webserver ausgeliefert werden. Wird die HTML-Datei einfach so im Browser geöffnet, für das zu einem so genannten *Cross origin error*. 

## Statistische Funktionen

D3 biete ein paar grundlegende statistische Funktion, welche das Arbeiten mit Daten erleichtern: 

Minimum, Maximum, Bereich:

```javascript
var data = [5, 10, 25, 40];

d3.min(data); // => 5
d3.max(data); // => 40
d3.extent(data) // => [5, 40]
```

Summe, Durchschnitt, Median:

```javascript
var data = [5, 10, 25, 40];

d3.sum(data); // => 80
d3.mean(data); // => 20
d3.median(data); // => 17.5
```

Ein Übersicht über alle statistische Funktionen findet sich in der [D3-Dokumentation](https://github.com/d3/d3-array/blob/master/README.md#statistics).

Sind die Daten verschachtelt, braucht man einen **Accessor**:

```javascript
var data = [
  { 'name': 'Michael', 'age': 39 },
  { 'name': 'Sandra', 'age': 24 },
  { 'name': 'Jakob', 'age': 32 }
]

d3.extent(data, function (d) { return d.age; } ); // => [24, 39]
```

Diese statistischen Funktion sind sehr nützlich, um damit die Skalen für ein Diagramm zu berechnen:

## Skalen

Skalen sind Funktion, welche für jeden Wert in einem Wertebereich (*Domain*), den entsprechenden Wert in einem anderen Wertebereich (*Range*) zurückgeben.

In diesem Beispiel haben die Daten eine Domäne von 5 bis 40. Für jeden Wert in diesem Bereich soll bestimmt, welche Wert sie in einem anderen Wertebereich hätte, in diesem Fall zwischen 0 und 100:

```javascript
var data = [5, 10, 25, 40];

var scale = d3.scaleLinear()
  .domain([5, 40])
  .range([0, 100]);

scale(10); // => 14.285714285714285  
scale(15); // => 28.57142857142857
```

In D3 werden diese Funktionen vor allem dafür genutzt, um Werte auf einer Zeichenfläche darzustellen und Achsen zu zeichnen. Dabei werden die Skalen-Funktionen oft mit statistischen Funktionen kombiniert:

```javascript
var data = [5, 10, 25, 40];
var width = 200; // Breite der Grafik

var domain = d3.extent(data); // => [5, 40]

var xScale = d3.scaleLinear()
  .domain(domain)
  .range([0, width]);
```

Hier ein Überblick über die wichtigsten Skalen:

- `d3.scaleLinear()`: Lineare Skala, transformiert einen Wert im Domänenintervall in einen Wert im Bereichsintervall
- `d3.scalePow()`, `d3.scaleLog()`: Exponential- und logarithmische Skalen werden für exponentiell oder logarithmisch steigende Werte (Wachstum) verwendet
- `d3.scaleTime()`: Zeit,
- `d3.scaleQuantize()`: Quantisierung, eine lineare Skala mit diskreten Werten für den Ausgabebereich, um Daten zu klassifizieren.
- `d3.scaleQuantile()`: Quantile, eine lineare Skala mit diskreten Werten für den Eingabedomäne, wenn Daten bereits klassifiziert sind
- `d3.scaleOrdinal`: Ordinalskala, für nicht quantitative Daten wie Namen oder Kategorien

Alle Skalen und ihre Funktion werden in der [D3-Dokumentation](https://github.com/d3/d3-scale) erklärt.

## Achsen

Achsen sind ein wichtiges visuelles Werkzeug, um dem Betrachter das Verstehen und Einordnen eines Diagramms zu erleichtern. Achsel helfen dabei einzelne Datenpunkte bestimmten Werten zuzuordnen und die zugrundeliegende Skala zu verstehen.

Um eine Achse in D3 zu konstruieren braucht es immer eine Skala. Optional können verschiedene Eigenschaft, wie die Markerlänge oder das Zahlenformat, definiert werden:


```javascript
var xAxis= d3.axisBottom(xScale)
  .tickValues([10, 20, 30, 40, 50])
  .tickFormat(function (d) {
    return d + ' %';
  })
  .tickSize(3);
```

Alle Funktionen des Achsenkonstruktors werden in der [D3-Dokumentation](https://github.com/d3/d3-axis/blob/master/README.md) erklärt.

Ein Problem bei der Verwendung der Achsen ist ihrer Positionierung. Die linke Achse `d3.axisLeft()` wird standardmäßig entlang des linken Bildschirms gezeichnet. Um die Achsen-Labels zu sehen, muss man die Achse nach rechts verschieben. Das gleiche gilt für die untere Achse `d3.axisBottom()`, welche erst nach unten verschoben werden muss. Dabei hilft die das SVG-Attribut [transform](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) und vordefinierte Seitenabstände:


```javascript
var data = [
  { 'name': 'Michael', 'age': 39, 'income': 52000 },
  { 'name': 'Sandra', 'age': 23, 'income': 32000 },
  { 'name': 'Jakob', 'age': 32, 'income': 46000 }
];

var margin = { top: 10, right: 10, bottom: 20, left: 45 };

var width = 400;
var height = 400;

var xExtent = d3.extent(data, function (d) { return d.age; } );
var yExtent = d3.extent(data, function (d) { return d.income; } );

var xScale = d3.scaleLinear()
  .domain(xExtent)
  .range([0, width]);
var yScale = d3.scaleLinear()
  .domain(yExtent)
  .range([height, 0]);

var xAxis = d3.axisBottom(xScale);
var yAxis = d3.axisLeft(yScale);

var svg = d3.select('#chart')
  .append('svg')
  .attr('width', width + margin.left + margin.right)
  .attr('height', height + margin.top + margin.bottom);

var group = svg.append('g')
  .attr('transform', 'translate(' + margin.left + ',' + margin.top + ')');

group.append('g')
  .attr('transform', 'translate(0,' + height + ')')
  .call(xAxis);

group.append('g')
  .call(yAxis);
```

In diesem Beispiel zeigt sich der Vorteil der Verwendung von SVG-Gruppen `<g>`, um mehrere Elemente auf einmal zu verschieben.

## Farben

Alle Farbskalen und wie man sie verwendet steht in der [D3-Dokumentation](https://github.com/d3/d3-color/blob/master/README.md).

## Events
Um Interaktionen mit den Inhalten einer Grafik zu ermöglichen, kann man so genannte *Event Listener* registrieren. Diese rufen eine bestimmte Aktion aus, wenn der Benutzer beispielsweise mit der Maus über ein Element klickt.

```javascript
var chart = d3.select('body')
  .append('svg')
    .attr('width', 160)
    .attr('height', 160)
  .append('rect')
    .attr('x', 5)
    .attr('y', 5)
    .attr('width', 150)
    .attr('height', 150)
    .attr('fill', 'red')
    .on('click', function (d, i) {
      console.log('Rechteck wurde angeklickt!');
      console.log('Die Breite des Rechtecks ist:', d3.select(this).attr('width'));
    });
```

Event Listener in Verbindung mit einem `console.log()` können sehr praktisch beim *Debuggen* einer Anwendung sein. Wir das richtige Element ausgewählt? Passiert überhaupt etwas?

Mehr Infos zu *Event Listener* sich in der [D3-Dokumentation](https://github.com/d3/d3-selection/blob/master/README.md#handling-events).

## Responsivität
D3 hat von sich aus keine Funktionen eingebaut, die es ermöglichen Grafiken *responsive* zu erstellen. Die Grafiken passen sich daher nicht automatisch an die Breite des Benutzergeräts (oder iFrames) an. 

Um zumindest beim ersten Aufruf die Grafik in der passenden Größe zu erstellen, kann man dafür die Höhe und Breite des Elterncontainers `#chart` verwenden: 

```javascript
var chart = d3.select('#chart');

var width = parseFloat(chart.style('width'));
var height = parseFloat(chart.style('height'));

var svg = chart
  .append('svg')
    .attr('width', width)
    .attr('height', height);
```

Wenn den Benutzer jedoch die Breite des Browserfensters verändert, zum Beispiel durch Maximieren oder Drehen des mobilen Endgeräts, passt sich die Grafik nicht an. Um auf diese Veränderungen zu reagieren, kann man einen *Event Listener* registrieren, der bei Bedarf den Chart neuzeichnet:

```javascript
var timeout;

d3.select(window).on('resize', function () {
  clearTimeout(timeout);

  timeout = setTimeout(function () {
    d3.select('#chart > svg').remove();
    draw(cachedData);
  }, 200);
});
```

Die Timeout-Funktion in diesem Beispiel verhindert, dass die Grafik zu oft neu gezeichnet wird oder zumindest erst dann, wenn die Größenänderung des Containers abgeschlossen ist.

Eine weitere Möglichkeit Grafiken *responsive* zu gestalten, ist das proportionale Skalieren der Grafik in alle Richtungen. Diese Methode wird [hier](https://brendansudol.com/writing/responsive-d3) beschrieben, funktioniert aber nur bei Grafiken, die sich sinnvoll in alle Richtungen skalieren lassen. Oft führt das zum Überlaufen einer Grafiken in den Text hinein.

## Animationen

Alle Möglichkeiten Animationen und Übergänge zu erstellen finden sich in der [D3-Dokumentation](https://github.com/d3/d3-transition/blob/master/README.md)

## Geodaten

Mehr dazu wie man Geodaten einbinden und welche Projektionen steht in der [D3-Dokumentation](https://github.com/d3/d3-geo/blob/master/README.md).

## Exportieren

D3-Grafiken im SVG-Format lassen sich recht einfach mit dem Bookmarklet [SVG Crowbar](https://nytimes.github.io/svg-crowbar/) abspeichern. Das ermöglicht zum Beispiel eine Nachbearbeitung mit Adobe Illustrator.

## Einbetten
Das Einbetten von D3-Grafiken funktioniert am besten mit einem HTML-iFrame:

```html
<iframe style="width: 100%; height: 460px; border: 0;" width="100%" height="100%" frameborder="0" src="https://web.br.de/interaktiv/milchpreise/"></iframe>
```

Das funktioniert aber nur dann, wenn sich bei Größenänderung die Höhe nicht verändert. Andernfalls kann es sein, dass Teile der Grafik abgeschnitten werden oder weiße Lücken entstehen.

Für das Einbetten von Grafiken mit variabler Höhe empfiehlt sich die JavaScript-Bibliothek [pym.js](http://blog.apps.npr.org/pym.js/). 
