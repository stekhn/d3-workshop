# Hausaufgabe

Hier ein paar kleine Aufgaben, um eure Programmierkenntnisse wieder wachzurufen und euch auf die wichtigsten Programmpunkte des kommenden Seminars vorzubereiten. Viel Spaß!

## Javascript

JavaScript ist die wichtige Grundlage unseres Seminars. Um so wichtiger ist es, sich mit den verschiedenen Arten von Listen in Javascript auseinanderzusetzen: [Arrays](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Array) `[]` und [Objekte](https://developer.mozilla.org/de/docs/Web/JavaScript/Reference/Global_Objects/Object) `{}`. 

### 1. Arrays

Wir haben ein Array mit verschiedenen Namen. Deine Aufgabe ist es, eine Funktion zu schreiben, welche alle Personen einzeln begrüßt.

```javascript
var names = ['Philipp', 'Andrea', 'Sophie'];

var sayHello = function (array) {
  // dein Code
}

sayHello(names); // => Hallo Philipp. Hallo Andrea. Hallo Sophie.
```

### 2. Objekte

Objekte sind neben Arrays eine andere Möglichkeit digitale Listen zu führen. In diesem Beispiel wollen wir Philipps Alter wissen:

```javascript
var person = { name: 'Philipp', age: 31 };

var getAge = function (object) {
  // dein Code
}

getAge(person); // => Philipp ist 31 Jahre alt.
```

### 3. Object Arrays

Arrays bestehen nicht immer nur aus Buchstaben oder Zahlen, sondern manchmal auch aus mehreren Objekten. Das ist praktisch, um zum Beispiel Personen mit mehreren Eigenschaften zu speichern. Schaffst du es, alle Personen mit ihrem Namen und Herkunftsort zu begrüßen?

```javascript
var persons = [
  { name: 'Philipp', city: 'Stuttgart' },
  { name: 'Andrea', city: 'Hamburg' },
  { name: 'Sophie', city: 'Dresden' }
];

var sayHelloCity = function (objectArray) {
  // dein Code
}

sayHelloCity(persons); // => Hallo Philipp aus Stuttgart. Hallo Andrea aus Hamburg. Hallo Sophie aus Dresden.
```

### 4. Accessors

Manchmal möchte man aus einem Object Array nur ein bestimmtes Objekt haben. Hier geht es darum, für eine bestimmte Person (nach Namen) das Alter zu herauszufinden. 

```javascript
var persons = [
  { name: 'Philipp', city: 'Stuttgart' },
  { name: 'Andrea', city: 'Hamburg' },
  { name: 'Sophie', city: 'Dresden' }
];

var getCity = function (objectArray) {
  // dein Code
}

getCity('Philipp'); // => Philipp kommt aus Stuttgart.
```

Wenn du Probleme hast die Lösung zu finden, google doch einfach mal nach _javascript find object in object array_. Vermutlich findest du die Lösung auf der Seite [Stackoverflow](https://stackoverflow.com/questions/13964155/get-javascript-object-from-array-of-objects-by-value-or-property).

## SVG

In unserem Seminar werden wir mithilfe von [D3.js](https://d3js.org/) Diagramme auf Basis von SVG-Vektorgrafiken erstellen. [SVG](https://developer.mozilla.org/de/docs/Web/SVG) ist, genauso wie HTML, eine Auszeichnungssprache, welche aus verschiedenen Elementen besteht. Was in HTML `<h1>`, `<p>` oder `<div>` sind, sind in SVG grafische Elemente wie `<rect>`, `<polygon>` oder `<line>`. Diese Elemente haben Attribute, die ihre Position oder ihr Aussehen bestimmen. Ein Beispiel mit einem Rechteck, einem Dreieck, einer Linie, einem Pfad und einem Text:

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="600" height="400" viewBox="0 0 600 400">
  <rect x="10" y="10" width="150" height="150" fill="red"/>
  <polygon x="5" y="5" points="584 150 441 150 513 10 584 150" fill="blue"/>
  <line x1="10" y1="187" x2="584" y2="187" fill="none" stroke="aqua" stroke-miterlimit="10" stroke-width="5"/>
  <path d="M12,288s295-108,295,0,281-24,281-24" fill="none" stroke="violet" stroke-miterlimit="10" stroke-width="5"/>
  <text x="10" y="375" font-size="18" font-family="Arial">Das ist eine wunderschöne Grafik</text>
</svg>
```

Die Grafik kannst du [hier](https://github.com/stekhn/d3-workshop/blob/master/homework/example.svg) anschauen. Um die Grafik zu bearbeiten, kopiere dir einfach den oben stehenden Code in eine Datei `grafik.svg`. Diese Grafik kannst du nun mit einem Text-Editor, wie Sublime Text, bearbeiten.

### Element hinzufügen

Der Beispiel-Grafik fehlt aber noch ein wichtiges Element. Zwischen Rechteck und Dreieck ist ein hässlich Lücke, die nach einem grünen Kreis verlangt:

```svg
<svg xmlns="http://www.w3.org/2000/svg" width="600" height="400" viewBox="0 0 600 400">
  <rect x="10" y="10" width="150" height="150" fill="red"/>
  <!-- Hier fehlt noch ein grüner Kreis -->
  <polygon x="5" y="5" points="584 150 441 150 513 10 584 150" fill="blue"/>
  <line x1="10" y1="187" x2="584" y2="187" fill="none" stroke="aqua" stroke-miterlimit="10" stroke-width="5"/>
  <path d="M12,288s295-108,295,0,281-24,281-24" fill="none" stroke="violet" stroke-miterlimit="10" stroke-width="5"/>
  <text x="10" y="375" font-size="18" font-family="Arial">Das ist eine wunderschöne Grafik</text>
</svg>
```

Schaffst du es den grünen Kreis hinzufügen und das Meisterwerk zu vollenden? Wie man einen Kreis macht, kannst du [hier](https://developer.mozilla.org/de/docs/Web/SVG/Element/circle) nachlesen.

## Node.js

Eine letzte kleine Aufgabe: Bitte installiere vor dem Seminar [Node.js v6](https://nodejs.org/en/) auf deinem Laptop. Node.js ist praktisch JavaScript für die Kommandozeile und für alle Betriebssystem verfügbar. In unserem Seminar werden wir Node.js verwenden, um eine kleinen Web-Server für Entwicklungszwecke aufzusetzen. 

### Vielen Dank für deine Mühe und bis zum Seminar 🍻
