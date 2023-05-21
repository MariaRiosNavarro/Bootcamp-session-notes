REACT

1.[React basics](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/react-basics.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/challenges-react-basics.md)

2.[React props](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/react-props.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/challenges-react-props.md)

2.[React nesting](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-nesting/react-nesting.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-nesting/challenges-react-nesting.md)

2.[React setup](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-project-setup/react-project-setup.md) [Challenges](https://github.com/neuefische/web-exercises/tree/main/sessions/react-project-setup/journal-app)






### React Basics

1.[React basics](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/react-basics.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/challenges-react-basics.md)

Was ist React und warum verwenden wir es?

React ist eine ***JavaScript-Bibliothek*** mit dem Ziel, das Leben des Entwicklers zu erleichtern: In den meisten Fällen müssen Sie nicht direkt mit der DOM-API (z. B. createElement) arbeiten. Sie schreiben einfach einfacheren (deklarativen) Code, der beschreibt, wie die Benutzeroberfläche aussehen soll, und React kümmert sich um das DOM unter der Haube.

Um deklarativen Code für React zu schreiben, verwenden Sie JSX.

### Verwendung von JSX

JSX ist eine Syntaxerweiterung für JavaScript. JSX ist weder ein String noch HTML, wie wir es kennen. JSX-Ausdrücke können überall dort verwendet werden, wo ein JavaScript-Ausdruck verwendet werden kann.

```
const element = <p>Some Text</p>;
```

Wir verwenden JSX, um React-Elemente zu erstellen. React-Elemente sind ein Zwischenformat, das React während des Rendervorgangs in DOM-Elemente konvertiert. Dadurch können wir unsere Benutzeroberfläche deklarativ mit JSX beschreiben.

### Elemente erstellen

Genau wie in HTML werden JSX-Elemente durch öffnende und schließende Tags beschrieben. Das öffnende Tag enthält den Tag-Namen oder den Komponententyp (siehe Verwenden von Komponenten ) und etwaige Attribute. Das schließende Tag enthält denselben Tag-Namen oder denselben Komponententyp wie das öffnende Tag und sonst nichts. Die untergeordneten Elemente des Elements werden zwischen dem öffnenden und schließenden Tag platziert. Wenn das Element keine untergeordneten Elemente hat, kann das schließende Tag weggelassen werden und das Element ist selbstschließend.


```
// Element with children
//
//              opening tag         children
//              |  attributes       |        closing tag
//              |  |                |        |
const element = <p className="text">Some Text</p>;
//               | |         |                 |
//               | |         attribute value   |
//               | attribute name              |
//               tag name or component type ---+

// Self-closing element
//
//            self closing tag   slash denotes self closing
//            |      attributes  |
//            |      |           |
const input = <input type="text" />;
//             |     |    |
//             |     |    attribute value
//             |     attribute name
//             tag name or component type

```

💡Elemente, die keine schließenden Tags in HTML unterstützen, wie <br>oder <input>müssen in JSX selbstschließend sein (wie <br />oder <input type="text" />).


💡Im Gegensatz zu HTML, *** das gegenüber fehlenden schließenden Tags resistent ist, ist dies bei JSX nicht der Fall *** . Wenn Sie vergessen, ein Tag zu schließen, erhalten Sie eine Fehlermeldung.


### komponenten Verwenden

Um ein Element aus einer Komponente zu erstellen , können wir einfach über den Funktionsnamen in JSX darauf verweisen und es wie jede integrierte Komponente behandeln:

```
const element = <MyComponent />;
```

In Bezug auf Attribute und untergeordnete Elemente funktioniert das Erstellen von Elementen aus Komponententypen genauso wie bei jedem (HTML-)Tag-Namen.

💡JSX unterscheidet zwischen integrierten (HTML-)Tag-Namen und Komponenten anhand des ersten Zeichens im JSX-Tag. Wenn es in Kleinbuchstaben geschrieben ist, wird es als integrierter Tag-Name behandelt. Wenn es in Großbuchstaben geschrieben ist, wird nach einer definierten JavaScript-Funktion mit diesem Namen gesucht. Deshalb ist es wichtig, PascalCase für Komponentennamen zu verwenden.

📙Weitere Informationen zum Schreiben von Markup mit JSX finden Sie in den React Docs .


Attribute

Attribute für integrierte HTML-Elemente verwenden JavaScript-zentrierte Namen aus der DOM-API. In den meisten Fällen sind die Namen dieselben wie in HTML, es gibt jedoch einige Ausnahmen. Beispielsweise classwird das Attribut aus HTML in JSX aufgerufen className.

Die Übergabe von Zeichenfolgenwerten an Attribute erfolgt mithilfe doppelter Anführungszeichen. Um einen beliebigen JavaScript-Ausdruck zu übergeben, verwenden Sie geschweifte Klammern.

```
const element = <p className="text">Some Text</p>;

const myValue = "This is a string";
const input = <input type="text" value={myValue} minLength={5} />;

```
Verschachtelungselemente

React-Elemente können auf die gleiche Weise verschachtelt werden, wie wir unsere HTML-Elemente verschachtelt haben.

```
const element = (
  <div>
    <p>Some Text</p>
    <p>Some more Text</p>
  </div>
);

```

💡Mehrzeilige JSX-Ausdrücke werden zur besseren Lesbarkeit in Klammern gesetzt. Keine Sorge: Prettier übernimmt das für Sie.


Interpolierende Ausdrücke

Wir können jeden JavaScript-Ausdruck in JSX verwenden, indem wir ihn in geschweifte Klammern einschließen. Dies nennt man Interpolation. Es ähnelt der String-Interpolation in JavaScript-Vorlagen-Strings.

```
const name = "Pawtricia";
const element = <p>My cat's name is {name}</p>;
const a = 5;
const b = 10;

const element = (
  <p>
    {a} + {b} = {a + b}
  </p>
);

```

💡Sie können Ausdrücke nur innerhalb von JSX verwenden. Aussagen wie ifoder forsind nicht erlaubt.

💡Informationen zum Interpolieren von JavaScript-Ausdrücken innerhalb von JSX-Attributen finden Sie im Abschnitt „Attribute“ .


📙Lesen Sie mehr über JavaScript in JSX mit geschweiften Klammern in den React Docs .


### Komponenten reagieren

Reaktionsanwendungen werden mithilfe von Komponenten erstellt. Eine Komponente ist ein unabhängiger und wiederverwendbarer Teil der Benutzeroberfläche, der eine eigene Struktur, Logik und möglicherweise einen eigenen Stil enthält.

React-Komponenten sind JavaScript-Funktionen, die React-Elemente zurückgeben. Diese Elemente werden dann während des Rendervorgangs von React in DOM-Elemente umgewandelt.

Um eine React-Komponente zu erstellen, schreiben wir eine benannte Funktion (mit PascalCase) und lassen sie mit JSX die gewünschten Elemente zurückgeben.

```
function MyButton() {
  return (
    <button type="button" className="default-button">
      I'm a button
    </button>
  );
}
```

Dies ist ein sehr leistungsfähiges Konzept, da es uns ermöglicht, dieselbe Komponente an mehreren Stellen in unserer Anwendung wiederzuverwenden.

💡Weitere Informationen zur Verwendung von Komponenten in JSX finden Sie unter Komponenten verwenden .

💡Es gibt kaum Einschränkungen, wie „klein“ eine Komponente (z. B. eine Schaltfläche) oder wie „groß“ (z. B. eine ganze Seite) sein kann.

📙Lesen Sie mehr über Ihre erste Komponente in den React Docs .

Hinweis : Das Exportieren der Komponente sowie das Verschachteln und Organisieren von Komponenten sind in dieser ersten Sitzung nicht möglich.

Imperative vs. deklarative Programmierung

Der Hauptunterschied zwischen imperativem und deklarativem Code besteht darin, dass imperativer Code beschreibt, wie etwas erstellt werden soll, und deklarativer Code beschreibt, was erstellt werden muss.

💡Stellen Sie sich vor, Sie bauen einen Hocker. Imperativ „Code“ würde die Schritte beschreiben, die Sie zum Bau des Hockers unternehmen müssen. Der deklarative „Code“ würde den Stuhl selbst beschreiben.

Imperativ:

Nimm 4 Holzlatten
Nimm 1 Holzbrett
Nimm 4 Schrauben
nimm einen Schraubenzieher
Schrauben Sie die Lamellen senkrecht unter das Brett
Positionieren Sie Ihre Arbeit so, dass die Tafel oben liegt
Deklarativ:

ein Hocker mit 4 Beinen und einer Sitzfläche, aufrecht stehend
Bei der imperativen Programmierung führt Ihr Code eine Reihe von Aktionen aus.

Bei der deklarativen Programmierung beschreibt Ihr Code ein gewünschtes Ergebnis.

Die Art und Weise, wie wir in diesem Kurs bisher JavaScript verwendet haben, war größtenteils zwingend erforderlich. Wir haben beschrieben, was getan werden muss, um ein bestimmtes Ergebnis zu erzielen.

```
const p = document.createElement("p");
p.classList.add("introText");
p.textContent = "Hello World!";
rootElement.append(p);
```

Jetzt ermöglicht uns React die deklarative Verwendung von JavaScript. Wir beschreiben React, was wir wollen, und React findet heraus, wie das DOM gemäß unserer Beschreibung aktualisiert wird.

```
root.render(<p className="introText">Hello World!</p>);
```

// React could interpret this to do the following:
// const p = document.createElement("p");
// p.classList.add("introText");
// p.textContent = "Hello World!";
// rootElement.append(p);
// …

Wie React rendert

React muss wissen, wo die von ihm erstellten Elemente gerendert werden sollen. Wir wählen das DOM-Element aus, in das wir rendern möchten, indem wir verwenden document.querySelector(). Anschließend erstellen wir ein React-Root-Objekt. Das Root-Objekt verfügt über eine render()Methode, mit der wir React-Elemente im DOM rendern können.

HTML

<div id="root"></div>
JavaScript

const rootElement = document.querySelector("#root");
const root = ReactDOM.createRoot(rootElement);
root.render(<h1>Hello, world</h1>);

Sie müssen diesen Code wahrscheinlich nie selbst schreiben, da er bereits in allen Vorlagen und Startern enthalten ist. In der realen Welt sieht es normalerweise so aus:

const rootElement = document.getElementById("root");
const root = ReactDOM.createRoot();

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

Hier haben wir ein importiertes <App />Element, das in verpackt ist <React.StrictMode>.

💡 StrictModerichtet React so ein, dass es im strikten Modus ausgeführt wird. Im strikten Modus weist React auf potenzielle Probleme in einer Anwendung hin.

React funktioniert intelligent, nicht hart

React aktualisiert nur die DOM-Elemente, die sich im Vergleich zum letzten Rendering geändert haben. Dies ist sehr effizient und bietet eine großartige Benutzererfahrung (der Fokus bleibt konsistent, Eingaben behalten ihre Werte usw.) sowie eine großartige Entwicklererfahrung (deklarativer Code ist viel einfacher zu verstehen).

Gut zu wissen: React, JSX, Transpiler und Bundler

Da JSX keine Standard-JavaScript-Syntax ist, müssen wir einen Transpiler (ein Tool, das eine Variante einer Sprache in eine andere übersetzt) ​​verwenden, um es in Standard-JavaScript umzuwandeln, das vom Browser verstanden werden kann.

Ein Bundler ist ein Tool, das alle Dateien unserer Codebasis in einer Datei zusammenfasst, die wir in unseren HTML-Code einbinden können. Der Bundler kümmert sich bei Bedarf auch um den Betrieb des Transpilers.

Der Bundler erstellt einen Entwicklungsserver, wenn wir ihn npm run startlokal ausführen. CodeSandbox erledigt dies automatisch für uns.


### React Props

2.[React props](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/react-props.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/challenges-react-props.md)

Props ist die Abkürzung für Properties. Sie sind eine Möglichkeit, Daten an eine untergeordnete Komponente zu übergeben. Als ersten Funktionsparameter erhält eine Komponente ein Props-Objekt.

Props werden als Attribute an eine Komponente übergeben .

```

function UserCard(props) {
  return <div>{props.name}</div>;
}

```


Der Einfachheit halber wird das props-Objekt häufig im Funktionsparameter destrukturiert.

```

function UserCard({ name }) {
  return <div>{name}</div>;
}

```

Sie können beliebige Namen für Ihre Requisiten wählen.

💡Es gibt jedoch einige Namenskonventionen. Boolesche Requisiten werden oft mit is, has oder als Präfix versehen should. Zum Beispiel isDisabled, hasErroroder shouldShow. Props, die Funktionen übernehmen, wird oft das Präfix vorangestellt on. Zum Beispiel onClick, onSubmitoder onHover. Das Befolgen dieser Konventionen erleichtert das Verständnis des Zwecks der Requisite.

PROPS können jeden Typs haben (String, Zahl, Array, Objekt, Funktion, ...).

Sie sollten das Requisitenobjekt als unveränderlich und schreibgeschützt behandeln.

### Übergeben von Requisiten an eine Komponente

Requisiten werden als Attribute an eine Komponente übergeben.

<UserCard name="Alex" />

Sie können jede Art von Daten als PRops übergeben.

```
<UserCard
  name="Alex"
  age={25}
  onContact={() => console.log("let's chat!")}
  isFavorite={true}
  favoriteFoods={["Pasta", "Salad"]}
  contactDetails={{ email: "alex@neuefische.de", phone: "123456789" }}
/>
```

String-Requisiten können in doppelten Anführungszeichen übergeben werden. Alle anderen Requisiten müssen in geschweiften Klammern übergeben werden.

💡Beachten Sie die doppelten geschweiften Klammern für das Objekt. Dies liegt daran, dass die äußeren geschweiften Klammern zur Kennzeichnung eines JavaScript-Ausdrucks verwendet werden. Die inneren geschweiften Klammern werden zur Definition eines Objekts verwendet.

💡Es gibt eine Kurzsyntax für boolesche Requisiten. Wenn der Wert sein soll, truekönnen Sie den Wert weglassen.
  
  
```
<UserCard isFavorite /> 
```
  
Das Weglassen eines Attributs führt zum Wert undefineddieser Props.

📙Weitere Informationen zum Übergeben von PROPS an eine Komponente finden Sie in den React-Dokumenten .

Bedingtes Rendern
Sie können Requisiten verwenden, um Teile einer Komponente bedingt zu rendern.

  
```
  
function UserCard({ name, isFavorite }) {
  return (
    <div>
      {name}
      {isFavorite ? <span>🌟</span> : null}
    </div>
  );
}
  
```
💡In JSX nullgibt es eine Möglichkeit, nichts zu rendern.

Sie können keine ifAnweisung innerhalb von JSX verwenden, da nur Ausdrücke zulässig sind. Sie können ifjedoch eine Anweisung außerhalb von JSX verwenden.

  
```   
function UserCard({ name, isFavorite }) {
  let favoriteStar = null;
  if (isFavorite) {
    favoriteStar = <span>🌟</span>;
  }

  return (
    <div>
      {name}
      {favoriteStar}
    </div>
  );
}
  
```  
📙Weitere Informationen zum bedingten Rendering finden Sie in den React Docs .
  
  
[passing-props-to-a-component](https://react.dev/learn/passing-props-to-a-component)
  
[conditional-rendering](https://react.dev/learn/conditional-rendering)



### Verschachtelung reagieren


Lernziele
Das Konzept der Verschachtelung verstehen
Erstellen Sie mehrere benutzerdefinierte Komponenten, um eine Hierarchie zu erstellen
Verwenden der childrenRequisite zum Rendern von JSX aus der übergeordneten Komponente
Komposition als eine Möglichkeit zum Aufbau komplexer Komponenten verstehen
JSX als Requisiten übergeben
Von JSX erstellte Elemente sind nur Objekte. Sie können wie jedes andere Objekt herumgereicht werden: zum Beispiel als Requisiten.

function UserCard({ avatar }) {
  return <div className="card">{avatar}</div>;
}
function App() {
  return <UserCard avatar={<Avatar />} />;
}
Die childrenStütze
Mit der Verschachtelung integrierter Browser-Tags sind Sie bereits vertraut:

<div>
  <img />
</div>
Oft möchten Sie, dass auch Ihre eigenen Komponenten verschachtelbar sind.

<UserCard>
  <Avatar />
</UserCard>
Wenn Sie eine Komponente in einer anderen Komponente verschachteln, wird die verschachtelte Komponente als Requisite an die übergeordnete Komponente übergeben. Diese besondere Requisite heißt children.

function UserCard({ children }) {
  return <div className="card">{children}</div>;
}
Diese Komponente rendert die verschachtelten Elemente als untergeordnete Elemente des divElements.

💡Die verschachtelten Elemente können ein einzelnes Element, mehrere Elemente oder sogar eine Zeichenfolge oder Zahl sein.

📙Weitere Informationen zum Übergeben von JSX als untergeordnete Elemente finden Sie in den React Docs .

Fragmente
Manchmal möchten Sie mehrere Elemente von einer Komponentenfunktion zurückgeben, ohne sie in das eine divoder andere Element einzuschließen. Sie können hierfür ein Fragment( <></>oder ) verwenden.<Fragment></Fragment>

Dies ist notwendig, da React-Komponenten nur ein einzelnes Element aus einer Komponentenfunktion zurückgeben können.

function UserList() {
  return (
    <>
      <UserCard>
        <Avatar />
      </UserCard>
      <UserCard>
        <Avatar />
      </UserCard>
    </>
  );
}
Dies entspricht dem Folgenden, im Allgemeinen wird jedoch die obige Kurzfassung bevorzugt.

import { Fragment } from "react";

function UserList() {
  return (
    <Fragment>
      <UserCard>
        <Avatar />
      </UserCard>
      <UserCard>
        <Avatar />
      </UserCard>
    </Fragment>
  );
}
💡Die <Fragment></Fragment>Syntax ist nur erforderlich, wenn Sie die spezielle Requisite an das Fragment übergeben möchten key, was wichtig wird, wenn Sie mit der Arbeit mit Listen beginnen.

💡Wenn Sie recherchieren, sehen Sie manchmal <React.Fragment></React.Fragment>, was dasselbe ist.

📙Lesen Sie mehr über Fragment (<>...</>) in den React Docs .

Komposition
Wenn wir React-Anwendungen erstellen, möchten wir häufig komplexe Komponenten aus einfacheren Komponenten erstellen. Dies nennt man Komposition.

Dazu müssen Sie Ihre Anwendung in Komponenten zerlegen. Sie können diese Komponenten dann zusammenstellen, um komplexere Komponenten zu erstellen.

Es ist wichtig herauszufinden, welche Komponenten Sie benötigen und wie diese zusammengesetzt sein sollten. Dies nennt man Anwendungsdesign.

📙Lesen Sie Thinking in React in den React Docs bis einschließlich Schritt 2. Spätere Schritte erfordern einen Status, den wir in einer zukünftigen Sitzung behandeln werden.

Ressourcen
Übergabe von JSX als untergeordnete Elemente in den React Docs
Fragment (<>...</>) in den React Docs
Denken in React in den React Docs




Beschuldigen
82 Zeilen (55 Zeilen) · 3,47 KB
Projekt-Setup reagieren
Lernziele
Sie verfügen über ein allgemeines Verständnis für Projektgerüste
Erfahren Sie, wie Sie mit der Create React App arbeiten
Den Zweck eines Bundlers kennen
npmGängige Skripte verstehen
publicDen Unterschied zwischen und srcOrdner kennen
Projektgerüst
Unter Project Scaffolding versteht man den Prozess der Erstellung eines neuen Projekts. Sie verwenden das Tool „React App erstellen“ , um automatisch ein neues React-Projekt zu erstellen.

💡Im Prinzip könnten Sie ein neues React-Projekt von Grund auf erstellen. Allerdings wäre das mit viel Arbeit verbunden und wir müssten viele Dinge selbst einrichten. Beispielsweise müssten Sie einen Entwicklungsserver, einen Build-Prozess und einen Testläufer einrichten. Sie müssten außerdem einen Modul-Bündeler und einen Transpiler konfigurieren. Das ist eine Menge Arbeit und Sie müssten es jedes Mal tun, wenn Sie ein neues Projekt erstellen möchten.

💡Create React App funktioniert übrigens ganz ähnlich wie das ghcdTool, das Sie wahrscheinlich bereits verwendet haben.

Erstellen Sie eine Reaktions-App
Create React App ist ein Tool, mit dem Sie ein React-Projekt mit einem einzigen Befehl erstellen können. Es ist ein großartiges Tool, um mit React zu beginnen.

📙Lesen Sie „Erste Schritte“ in den Dokumenten zur „Create React App“, um zu erfahren, wie Sie ein neues Projekt mit erstellen npx.

Ordnerstruktur
Create React App erstellt für Sie eine Ordnerstruktur mit vielen Dateien und Ordnern.

📙Weitere Informationen zur Ordnerstruktur finden Sie in den Dokumenten zum Erstellen einer React-App .

Verfügbare Skripte
Create React App verfügt über ein paar weitere NPM-Skripte als die, die Sie bisher gesehen haben. Neben dem Starten eines Entwicklungsservers und dem Ausführen von Tests können Sie damit auch Ihre App erstellen.

💡Sie sollten das Skript niemals verwenden müssen eject. Es handelt sich um einen einseitigen Vorgang, den Sie nicht rückgängig machen können. Es wird verwendet, um die Konfiguration Ihrer App anzupassen.

📙Weitere Informationen zu verfügbaren Skripten finden Sie in den Create React App-Dokumenten .

Hinzufügen eines Stylesheets
Sie können CSS-Dateien direkt in Ihre JavaScript-Dateien importieren.

Es ist ein gängiges Muster, Ihr CSS zusammen mit Ihren Komponenten anzuordnen. Dies bedeutet, dass Sie über eine CSS-Datei mit demselben Namen wie die Komponente verfügen, die in die JavaScript-Komponentendatei importiert wird. Es empfiehlt sich, die BEM-Namenskonvention für Ihre CSS-Klassen zu verwenden, um Namenskonflikte zwischen Komponenten zu vermeiden.

📙Weitere Informationen zum Hinzufügen eines Stylesheets finden Sie in den Create React App-Dokumenten .

Hinzufügen von Bildern, Schriftarten und Dateien
Sie können Bilddateien oder Schriftarten direkt in Ihre JavaScript-Dateien importieren.

Dies ist besonders nützlich für SVG-Dateien, die Sie als React-Komponenten importieren können.

📙Weitere Informationen zum Hinzufügen von Bildern, Schriftarten und Dateien finden Sie in den Create React App-Dokumenten .

Ressourcen
Erste Schritte mit den Create React App-Dokumenten
Ordnerstruktur in den Create React App-Dokumenten
Verfügbare Skripte in den Create React App-Dokumenten
Hinzufügen eines Stylesheets zu den Create React App-Dokumenten
Hinzufügen von Bildern, Schriftarten und Dateien zu den Create React App-Dokumenten
