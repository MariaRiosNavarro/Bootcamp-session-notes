# TEST

Abfragen sind die Methoden, die Testing Library Ihnen zur Verfügung stellt, um Elemente auf der Seite zu finden. 
Es gibt verschiedene Arten von Abfragen ("get", "find", "query");

der Unterschied zwischen ihnen besteht darin, ob die Abfrage einen Fehler wirft,

wenn kein Element gefunden wird, 

oder ob sie ein Promise zurückgibt und erneut versucht wird. 


Je nachdem, welchen Seiteninhalt Sie auswählen, können verschiedene Abfragen mehr oder weniger geeignet sein. In der Prioritätsanleitung finden Sie Empfehlungen dazu, wie Sie semantische Abfragen verwenden können, um Ihre Seite auf die zugänglichste Weise zu testen.

Nachdem Sie ein Element ausgewählt haben, können Sie die Events-API oder user-event verwenden, um Ereignisse auszulösen und Benutzerinteraktionen mit der Seite zu simulieren, oder Sie können Jest und jest-dom verwenden, um Aussagen über das Element zu treffen.

Es gibt Testing Library-Helfermethoden, die mit Abfragen arbeiten. Da sich Elemente als Reaktion auf Aktionen ein- und ausblenden, können asynchrone APIs wie waitFor oder findBy-Abfragen verwendet werden, um auf Änderungen im DOM zu warten. Um nur Elemente zu finden, die Kinder eines bestimmten Elements sind, können Sie das "within"-Konzept verwenden. Bei Bedarf können Sie auch einige Optionen konfigurieren, z. B. den Timeout für erneute Versuche und das StandardtestID-Attribut.

Beispiel

```js
import {render, screen} from '@testing-library/react' // (oder /dom, /vue, ...)

test('sollte das Anmeldeformular anzeigen', () => {
  render(<Login />)
  const input = screen.getByLabelText('Benutzername')
  // Ereignisse und Aussagen...
})

````


### Arten von Abfragen

### Einzelne Elemente

getBy...:

Gibt das übereinstimmende Element für eine Abfrage zurück und wirft einen aussagekräftigen Fehler, wenn kein Element gefunden wird oder wenn mehrere Übereinstimmungen gefunden werden (verwenden Sie stattdessen getAllBy, wenn mehr als ein Element erwartet wird).
queryBy...: 

Gibt das übereinstimmende Element für eine Abfrage zurück und gibt null zurück, wenn keine Übereinstimmungen gefunden werden. Dies ist nützlich, um ein nicht vorhandenes Element zu überprüfen. Wirft einen Fehler, wenn mehrere Übereinstimmungen gefunden werden (verwenden Sie stattdessen queryAllBy, wenn dies akzeptabel ist).
findBy...: 

Gibt ein Promise zurück, das aufgelöst wird, wenn ein Element gefunden wird, das der angegebenen Abfrage entspricht. Das Promise wird abgelehnt, wenn kein Element gefunden wird oder wenn nach einem Standard-Timeout von 1000ms mehr als ein Element gefunden wird. Wenn Sie mehr als ein Element finden müssen, verwenden Sie findAllBy.

### Mehrere Elemente

getAllBy...: 

Gibt ein Array aller übereinstimmenden Elemente für eine Abfrage zurück und wirft einen Fehler, wenn keine Elemente gefunden werden.

queryAllBy...: 

Gibt ein Array aller übereinstimmenden Elemente für eine Abfrage zurück und gibt ein leeres Array ([]) zurück, wenn keine Übereinstimmungen gefunden werden.

findAllBy...:

Gibt ein Promise zurück, das aufgelöst wird, wenn mindestens ein Element gefunden wird, das der angegebenen Abfrage entspricht. Das Promise wird abgelehnt, wenn kein Element gefunden wird.

### By-Abfragen verwenden

### Abfragen nach Text

getByText: 

Sucht ein Element anhand seines Textinhalts (Textknoten).

queryByText: 

Sucht ein Element anhand seines Textinhalts (Textknoten) und gibt null zurück, wenn keine Übereinstimmung gefunden wird.

findByText: 

Sucht ein Element anhand seines Textinhalts (Textknoten) und gibt ein Promise zurück.

Beispiel:

```js
import {render, screen} from '@testing-library/react'

test('sollte den Text "Willkommen" anzeigen', () => {
  render(<Greeting />)
  const textElement = screen.getByText(/Willkommen/)
  // Ereignisse und Aussagen...
})

````


### Abfragen nach Label

getByLabelText: 

Sucht ein Element anhand seines Label-Textinhalts.

queryByLabelText: 

Sucht ein Element anhand seines Label-Textinhalts und gibt null zurück, wenn keine Übereinstimmung gefunden wird.

findByLabelText: 

Sucht ein Element anhand seines Label-Textinhalts und gibt ein Promise zurück.

Beispiel

```js
import {render, screen} from '@testing-library/react'

test('sollte das Eingabefeld mit dem Label "Benutzername" anzeigen', () => {
  render(<LoginForm />)
  const inputElement = screen.getByLabelText('Benutzername')
  // Ereignisse und Aussagen...
})
````

getByPlaceholderText: 

Ein Platzhalter ist kein Ersatz für ein Label. Aber wenn das alles ist, was du hast, ist es besser als Alternativen.

getByText: 

Außerhalb von Formularen ist der Textinhalt der Hauptweg, wie Benutzer Elemente finden. Diese Methode kann verwendet werden, um nicht-interaktive Elemente (wie Divs, Spans und Absätze) zu finden.

getByDisplayValue: 

Der aktuelle Wert eines Formularelements kann nützlich sein, um auf einer Seite mit ausgefüllten Werten zu navigieren.


### Semantische Abfragen: HTML5- und ARIA-konforme Selektoren. 

Beachte, dass die Benutzererfahrung beim Interagieren mit diesen Attributen je nach Browser und unterstützender Technologie stark variieren kann.

getByAltText: 

Wenn Ihr Element Alt-Text unterstützt (img, area, input und jedes benutzerdefinierte Element), können Sie dies verwenden, um das Element zu finden.

getByTitle: 

Das title-Attribut wird von Bildschirmlesegeräten nicht konsistent gelesen und ist standardmäßig für sehende Benutzer nicht sichtbar.

### Test-IDs

getByTestId: 

Der Benutzer kann diese nicht sehen (oder hören), daher wird dies nur für Fälle empfohlen, in denen eine Übereinstimmung nach Rolle oder Text nicht möglich ist oder keinen Sinn ergibt (z. B. wenn der Text dynamisch ist).
Verwendung von Abfragen



Die grundlegenden Abfragen von DOM Testing Library erfordern, dass Sie einen Container als ersten Argument übergeben. Die meisten Framework-Implementierungen von Testing Library bieten eine vorab gebundene Version dieser Abfragen an, wenn Sie Ihre Komponenten mit ihnen rendern. Dies bedeutet, dass Sie keinen Container bereitstellen müssen. Wenn Sie nur document.body abfragen möchten, können Sie den "screen"-Export verwenden, wie unten gezeigt (die Verwendung von "screen" wird empfohlen).

Das Hauptargument für eine Abfrage kann ein String, ein regulärer Ausdruck oder eine Funktion sein. Es gibt auch Optionen, um anzugeben, wie der Knotentext analysiert wird. Weitere Informationen dazu finden Sie in der Dokumentation zu "TextMatch".

Gegeben die folgenden DOM-Elemente (die von React, Vue, Angular oder normalem HTML-Code gerendert werden können):

<body>
  <div id="app">
    <label for="username-input">Benutzername</label>
    <input id="username-input" />
  </div>
</body>
Sie können eine Abfrage verwenden, um ein Element zu finden (hier getByLabelText):

```js
import {screen, getByLabelText} from '@testing-library/dom'

// Mit screen:
const inputNode1 = screen.getByLabelText('Benutzername')

// Ohne screen müssen Sie einen Container bereitstellen:
const container = document.querySelector('#app')
const inputNode2 = getByLabelText(container, 'Benutzername')

````



### queryOptions

Sie können ein queryOptions-Objekt mit dem Abfragetyp übergeben. In den Dokumentationen für jeden Abfragetyp finden Sie verfügbare Optionen, z. B. die byRole-API.

### screen

Alle von DOM Testing Library exportierten Abfragen akzeptieren einen Container als erstes Argument. Da die Abfrage des gesamten document.body sehr häufig ist, exportiert DOM Testing Library auch ein screen-Objekt, das jede Abfrage enthält, die vorab an document.body gebunden ist (unter Verwendung der "within"-Funktionalität). Wrapper wie React Testing Library exportieren ebenfalls screen, sodass Sie es auf die gleiche Weise verwenden können.

So verwenden Sie es:

```js
import {screen} from '@testing-library/dom'

document.body.innerHTML = <label for="example">Beispiel</label> <input id="example" />

const exampleInput = screen.getByLabelText('Beispiel')

`````

Hinweis:

Sie benötigen eine globale DOM-Umgebung, um "screen" verwenden zu können. Wenn Sie jest verwenden und die testEnvironment auf "jsdom" festgelegt ist, steht Ihnen eine globale DOM-Umgebung zur Verfügung.

Wenn Sie Ihren Test mit einem Skript-Tag laden, stellen Sie sicher, dass es nach dem Body erscheint. Ein Beispiel finden Sie hier.

### TextMatch

Die meisten Abfrage-APIs akzeptieren einen TextMatch als Argument, was bedeutet, dass das Argument entweder ein String, ein Regex oder eine Funktion mit der Signatur (content?: string, element?: Element | null) => boolean sein kann. Diese Funktion gibt true für eine Übereinstimmung und false für eine Nichtübereinstimmung zurück.

Beispiele für TextMatch:

Angenommen, der folgende HTML-Code liegt vor:

```js

<div>Hallo Welt</div>
Um das div-Element zu finden:

// Übereinstimmung mit einem String:
screen.getByText('Hallo Welt') // vollständige Übereinstimmung
screen.getByText('llo Worl', {exact: false}) // Teilübereinstimmung
screen.getByText('hello world', {exact: false}) // Groß-/Kleinschreibung ignorieren

// Übereinstimmung mit einem Regex:
screen.getByText(/World/) // Teilübereinstimmung
screen.getByText(/world/i) // Teilübereinstimmung, Groß-/Kleinschreibung ignorieren
screen.getByText(/^hello world$/i) // vollständige Übereinstimmung, Groß-/Kleinschreibung ignorieren
screen.getByText(/Hello W?oRlD/i) // Teilübereinstimmung, Groß-/Kleinschreibung ignorieren, sucht nach "hello world" oder "hello orld"

// Übereinstimmung mit einer benutzerdefinierten Funktion:
screen.getByText((content, element) => content.startsWith('Hello'))

Um das div-Element nicht zu finden:

// vollständiger String stimmt nicht überein
screen.getByText('Auf Wiedersehen Welt')

// Regex ist groß-/kleinschreibungssensitiv und hat eine andere Groß-/Kleinschreibung
screen.getByText(/hello world/)

// Funktion sucht nach einem span, es handelt sich jedoch um ein div:
screen.getByText((content, element) => {
return element.tagName.toLowerCase() === 'span' && content.startsWith('Hello')
})

````


### Präzision

Abfragen, die ein TextMatch akzeptieren, akzeptieren auch ein Objekt als letzten Parameter, das Optionen enthält, die die Genauigkeit der Zeichenfolgenübereinstimmung beeinflussen:

exact: Standardmäßig true; stimmt mit vollständigen Zeichenfolgen überein, beachtet die Groß-/Kleinschreibung. Bei false werden Teilübereinstimmungen gemacht und die Groß-/Kleinschreibung wird ignoriert.

exact hat keine Auswirkungen auf Regex- oder Funktionsargumente.

exact hat keine Auswirkungen auf zugängliche Namen, die mit der name-Option von *byRole-Abfragen angegeben sind. Sie können einen Regex verwenden, um eine ungenaue Übereinstimmung der zugänglichen Namen zu erzielen.
In den meisten Fällen bietet ein Regex im Vergleich zu einem String eine größere Kontrolle über ungenaue Übereinstimmungen und sollte { exact: false } vorgezogen werden.
normalizer: Eine optionale Funktion, die das Normalisierungsverhalten überschreibt. Siehe Normalization (Normalisierung).
Normalization (Normalisierung)
Bevor jegliche Übereinstimmungslogik gegen Text im DOM ausgeführt wird, normalisiert DOM Testing Library automatisch diesen Text. Standardmäßig besteht die Normalisierung darin, führende und abschließende Leerzeichen vom Text zu entfernen und mehrere aufeinanderfolgende Leerzeichen innerhalb der Zeichenfolge in ein einzelnes Leerzeichen zu reduzieren.

Wenn Sie diese Normalisierung verhindern oder alternative Normalisierung bereitstellen möchten (z. B. zum Entfernen von Unicode-Steuerzeichen), können Sie eine Normalisierungsfunktion im Optionsobjekt bereitstellen. Diese Funktion erhält eine Zeichenfolge und gibt eine normalisierte Version dieser Zeichenfolge zurück.

Hinweis:

Die Angabe eines Werts für "normalizer" ersetzt die integrierte Normalisierung, aber Sie können "getDefaultNormalizer" aufrufen, um einen integrierten Normalisierer zu erhalten, entweder um diese Normalisierung anzupassen oder um sie aus Ihrem eigenen Normalisierer heraus aufzurufen.

getDefaultNormalizer akzeptiert ein Optionsobjekt, das die Auswahl des Verhaltens ermöglicht:

trim: Standardmäßig true. Entfernt führende und abschließende Leerzeichen.
collapseWhitespace: Standardmäßig true. Reduziert inneren Whitespace (Zeilenwechsel, Tabs, wiederholte Leerzeichen) auf ein einzelnes Leerzeichen.
Beispiele für Normalisierung:

Um eine Übereinstimmung ohne Abschneiden durchzuführen:

```js
screen.getByText('text', {
normalizer: getDefaultNormalizer({trim: false}),
})
````

Um die Normalisierung zu überschreiben und einige Unicode-Zeichen zu entfernen, während einige (aber nicht alle) der integrierten Normalisierungsverhalten beibehalten werden:

```js
screen.getByText('text', {
normalizer: str =>
getDefaultNormalizer({trim: false})(str).replace(/[\u200E-\u200F]*/g, ''),
})

```

### Debugging

screen.debug()

Zu Ihrer Bequemlichkeit stellt "screen" neben den Abfragen auch eine Debug-Methode bereit. Diese Methode ist im Wesentlichen eine Abkürzung für console.log(prettyDOM()). Sie unterstützt das Debuggen des Dokuments, eines einzelnen Elements oder eines Arrays von Elementen.

```js
import {screen} from '@testing-library/dom'

document.body.innerHTML = `
<button>Test</button>
<span>Mehrfachtest</span>

  <div>Mehrfachtest</div>
`
// Dokument debuggen
screen.debug()
// Einzelnes Element debuggen
screen.debug(screen.getByText('Test'))
// Mehrere Elemente debuggen
screen.debug(screen.getAllByText('Mehrfachtest'))

screen.logTestingPlaygroundURL()
````

Für das Debuggen mit testing-playground bietet "screen" diese praktische Methode an, die eine URL generiert, die den aktuellen Testzustand repräsentiert. Rufen Sie screen.logTestingPlaygroundURL() auf und öffnen Sie die generierte URL in einem Browser. Das Fenster zeigt eine Miniaturansicht des DOMs mit einem Snapshot der Komponente, die Sie gerade testen. Sie können interaktiv im DOM navigieren, Anweisungen eingeben und den DOM-Code und den Snapshot vergleichen, um den Testfall zu erstellen oder zu validieren.
