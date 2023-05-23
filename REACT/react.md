REACT

1.[React basics](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/react-basics.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/challenges-react-basics.md)

2.[React props](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/react-props.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/challenges-react-props.md)

3.[React nesting](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-nesting/react-nesting.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-nesting/challenges-react-nesting.md)

4.[React setup](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-project-setup/react-project-setup.md) [Challenges](https://github.com/neuefische/web-exercises/tree/main/sessions/react-project-setup/journal-app)

5.[React State](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state/react-state.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state/challenges-react-state.md)

6.[React with Arrays](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-with-arrays/react-with-arrays.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-with-arrays/challenges-react-with-arrays.md)

7.[React State 2](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-2/react-state-2.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-2/challenges-react-state-2.md)

8.[React State 3](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-3/react-state-3.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-3/challenges-react-state-3.md)

9.[React Effects and Fetch](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-effects-and-fetch/react-effects-and-fetch.md)[Challenges]

10.[React with Local Storage](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-with-local-storage/react-with-local-storage.md)[Challenges]



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

> 📙 Read more about [**Writing Markup with JSX**
> in the React Docs](https://react.dev/learn/writing-markup-with-jsx).


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

💡Sie können Ausdrücke nur innerhalb von JSX verwenden. Aussagen wie ```if``` oder ```for``` sind nicht erlaubt.

💡Informationen zum Interpolieren von JavaScript-Ausdrücken innerhalb von JSX-Attributen finden Sie im Abschnitt „Attribute“ .

> 📙 Read more about [**JavaScript in JSX with Curly Braces**
> in the React Docs](https://react.dev/learn/javascript-in-jsx-with-curly-braces).


### Komponenten reagieren

React Apps werden mithilfe von Komponenten erstellt. Eine Komponente ist ein unabhängiger und wiederverwendbarer Teil der Benutzeroberfläche, der eine eigene Struktur, Logik und möglicherweise einen eigenen Stil enthält.

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

[**Your First Component**
> in the React Docs](https://react.dev/learn/your-first-component).

Hinweis : Das Exportieren der Komponente sowie das Verschachteln und Organisieren von Komponenten sind in dieser ersten Sitzung nicht möglich.

### Imperative vs. deklarative Programmierung

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


## Resources

- [What is React: A Visual Introduction For Beginners on learnreact.design](https://learnreact.design/posts/what-is-react)
- [Writing Markup with JSX in the React Docs](https://react.dev/learn/writing-markup-with-jsx)
- [JavaScript in JSX with Curly Braces in the React Docs](https://react.dev/learn/javascript-in-jsx-with-curly-braces)
- [Your First Component in the React Docs](https://react.dev/learn/your-first-component)
- [Difference between a Framework and a Library on freecodecamp](https://www.freecodecamp.org/news/the-difference-between-a-framework-and-a-library-bd133054023f/)



---

###  React Props


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

Sie können beliebige Namen für Ihre Props wählen.

💡Es gibt jedoch einige Namenskonventionen. Boolesche Requisiten werden oft mit is, has oder als Präfix versehen should. Zum Beispiel isDisabled, hasErroroder shouldShow. Props, die Funktionen übernehmen, wird oft das Präfix vorangestellt on. Zum Beispiel onClick, onSubmit oder onHover. Das Befolgen dieser Konventionen erleichtert das Verständnis des Zwecks der Props.

PROPS können jeden Typs haben (String, Zahl, Array, Objekt, Funktion, ...).

Sie sollten das PROPS als unveränderlich und schreibgeschützt behandeln.

###  Übergeben von PROPS an eine Komponente

PROPS werden als Attribute an eine Komponente übergeben.

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

String-Props können in doppelten Anführungszeichen übergeben werden. Alle anderen Requisiten müssen in geschweiften Klammern übergeben werden.

💡Beachten Sie die doppelten geschweiften Klammern für das Objekt. Dies liegt daran, dass die äußeren geschweiften Klammern zur Kennzeichnung eines JavaScript-Ausdrucks verwendet werden. Die inneren geschweiften Klammern werden zur Definition eines Objekts verwendet.

💡Es gibt eine Kurzsyntax für boolesche Requisiten. Wenn der Wert sein soll, truekönnen Sie den Wert weglassen.
  
  
```
<UserCard isFavorite /> 
```
  
Das Weglassen eines Attributs führt zum Wert undefined dieser Props.

> 📙 Read more about [**Passing props to a Component**
> in the React Docs](https://react.dev/learn/passing-props-to-a-component).

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

> 📙 Read more about [**Conditional Rendering**
> in the React Docs](https://react.dev/learn/conditional-rendering).


## Resources

- [Passing props to a Component in the React Docs](https://react.dev/learn/passing-props-to-a-component)
- [Conditional Rendering in the React Docs](https://react.dev/learn/conditional-rendering)

---

### React NESTINGS


3.[React nesting](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-nesting/react-nesting.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-nesting/challenges-react-nesting.md)

JSX als Props übergeben

Von JSX erstellte Elemente sind nur Objekte. Sie können wie jedes andere Objekt herumgereicht werden: zum Beispiel als Props.

```
function UserCard({ avatar }) {
  return <div className="card">{avatar}</div>;
}
function App() {
  return <UserCard avatar={<Avatar />} />;
}

```

Die children Stütze

Mit der Verschachtelung integrierter Browser-Tags sind Sie bereits vertraut:

```
<div>
  <img />
</div>
```

Oft möchten Sie, dass auch Ihre eigenen Komponenten verschachtelbar sind.

```
<UserCard>
  <Avatar />
</UserCard>
```

Wenn Sie eine Komponente in einer anderen Komponente verschachteln, wird die verschachtelte Komponente als Requisite an die übergeordnete Komponente übergeben. Diese besondere Requisite heißt children.

```
function UserCard({ children }) {
  return <div className="card">{children}</div>;
}
```

Diese Komponente rendert die verschachtelten Elemente als untergeordnete Elemente des divElements.

💡Die verschachtelten Elemente können ein einzelnes Element, mehrere Elemente oder sogar eine Zeichenfolge oder Zahl sein.


> 📙 Read more about [**Passing JSX as children**
> in the React Docs](https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children).

### Fragmente

Manchmal möchten Sie mehrere Elemente von einer Komponentenfunktion zurückgeben, ohne sie in das eine divoder andere Element einzuschließen. Sie können hierfür ein Fragment( <></>oder ) verwenden.<Fragment></Fragment>

Dies ist notwendig, da React-Komponenten nur ein einzelnes Element aus einer Komponentenfunktion zurückgeben können.

```
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

```
Dies entspricht dem Folgenden, im Allgemeinen wird jedoch die obige Kurzfassung bevorzugt.


```
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

```


💡Die <Fragment></Fragment>Syntax ist nur erforderlich, wenn Sie die spezielle Requisite an das Fragment übergeben möchten key, was wichtig wird, wenn Sie mit der Arbeit mit Listen beginnen.

💡Wenn Sie recherchieren, sehen Sie manchmal <React.Fragment></React.Fragment>, was dasselbe ist.


> 📙 Read more about [**Fragment (<>...</>)**
> in the React Docs](https://react.dev/apis/react/Fragment).

### Komposition


Wenn wir React-Anwendungen erstellen, möchten wir häufig komplexe Komponenten aus einfacheren Komponenten erstellen. Dies nennt man Komposition.

Dazu müssen Sie Ihre Anwendung in Komponenten zerlegen. Sie können diese Komponenten dann zusammenstellen, um komplexere Komponenten zu erstellen.

Es ist wichtig herauszufinden, welche Komponenten Sie benötigen und wie diese zusammengesetzt sein sollten. Dies nennt man Anwendungsdesign (Aplication Design).



> 📙 Read [**Thinking in React**
> in the React Docs](https://react.dev/learn/thinking-in-react) up to and including Step 2. Later steps require state, which we will cover in a future session.

---

## Resources

- [Passing JSX as children in the React Docs](https://react.dev/learn/passing-props-to-a-component#passing-jsx-as-children)
- [Fragment (<>...</>) in the React Docs](https://react.dev/apis/react/Fragment)
- [Thinking in React in the React Docs](https://react.dev/learn/thinking-in-react)


---


### React Setup

4.[React setup](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-project-setup/react-project-setup.md) [Challenges](https://github.com/neuefische/web-exercises/tree/main/sessions/react-project-setup/journal-app)


Unter Project Scaffolding versteht man den Prozess der Erstellung eines neuen Projekts. Sie verwenden das Tool [Create React App](https://create-react-app.dev/docs/getting-started), um automatisch ein neues React-Projekt zu erstellen.

💡Im Prinzip könnten Sie ein neues React-Projekt von scratch auf erstellen. Allerdings wäre das mit viel Arbeit verbunden und wir müssten viele Dinge selbst einrichten. Beispielsweise müssten Sie einen Entwicklungsserver, einen Build-Prozess und einen Testläufer einrichten. Sie müssten außerdem einen Modul-Bündeler und einen Transpiler konfigurieren. Das ist eine Menge Arbeit und Sie müssten es jedes Mal tun, wenn Sie ein neues Projekt erstellen möchten.

💡Create React App funktioniert übrigens ganz ähnlich wie das `ghcd` Tool, das Sie wahrscheinlich bereits verwendet haben.

### Erstellen Sie eine React-App

Create React App ist ein Tool, mit dem Sie ein React-Projekt mit einem einzigen Befehl erstellen können. Es ist ein großartiges Tool, um mit React zu beginnen.

> 📙 Read
> [**Getting Started** on the Create React App Docs](https://create-react-app.dev/docs/getting-started)
> to learn how to create a new project using `npx`.

### Ordnerstruktur

Create React App erstellt für Sie eine Ordnerstruktur mit vielen Dateien und Ordnern.

> 📙 Read more about
> [**Folder Structure** on the Create React App Docs](https://create-react-app.dev/docs/folder-structure)..

### Verfügbare Skripte

Create React App verfügt über ein paar weitere NPM-Skripte als die, die Sie bisher gesehen haben. Neben dem Starten eines Entwicklungsservers und dem Ausführen von Tests können Sie damit auch Ihre App erstellen.

💡Sie sollten das Skript niemals verwenden müssen eject. Es handelt sich um einen einseitigen Vorgang, den Sie nicht rückgängig machen können. Es wird verwendet, um die Konfiguration Ihrer App anzupassen.

> 📙 Read more about
> [**Available Scripts** on the Create React App Docs](https://create-react-app.dev/docs/available-scripts)..

### Hinzufügen eines Stylesheets

Sie können CSS-Dateien direkt in Ihre JavaScript-Dateien importieren.

Es ist ein gängiges Muster, Ihr CSS zusammen mit Ihren Komponenten anzuordnen. Dies bedeutet, dass Sie über eine CSS-Datei mit demselben Namen wie die Komponente verfügen, die in die JavaScript-Komponentendatei importiert wird. Es empfiehlt sich, die BEM-Namenskonvention für Ihre CSS-Klassen zu verwenden, um Namenskonflikte zwischen Komponenten zu vermeiden.

> 📙 Read more about
> [**Adding a Stylesheet** on the Create React App Docs](https://create-react-app.dev/docs/adding-a-stylesheet)..

### Hinzufügen von Bildern, Schriftarten und Dateien
Sie können Bilddateien oder Schriftarten direkt in Ihre JavaScript-Dateien importieren.

Dies ist besonders nützlich für SVG-Dateien, die Sie als React-Komponenten importieren können.

> 📙 Read more about
> [**Adding Images, Fonts and Files** on the Create React App Docs](https://create-react-app.dev/docs/adding-images-fonts-and-files).


## Resources

- [Getting Started on the Create React App Docs](https://create-react-app.dev/docs/getting-started)
- [Folder Structure on the Create React App Docs](https://create-react-app.dev/docs/folder-structure)
- [Available Scripts on the Create React App Docs](https://create-react-app.dev/docs/available-scripts)
- [Adding a Stylesheet on the Create React App Docs](https://create-react-app.dev/docs/adding-a-stylesheet)
- [Adding Images, Fonts and Files on the Create React App Docs](https://create-react-app.dev/docs/adding-images-fonts-and-files)

---

###  React State

5.[React State](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state/react-state.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state/challenges-react-state.md)


Bei einem Zustand handelt es sich um Daten, die sich im Laufe der Zeit ändern. Denken Sie an die Lampe auf Ihrem Schreibtisch. Es kann ein- oder ausgeschaltet werden. Die Lampe befindet sich zu einem bestimmten Zeitpunkt in einem bestimmten Zustand und dieser Zustand kann sich im Laufe der Zeit ändern.

Ein anderes Beispiel könnte der Geldbetrag in Ihrer Handtasche sein. Sie haben jederzeit einen bestimmten Geldbetrag in Ihrer Handtasche, der Geldbetrag kann sich jedoch ändern. Der Zustand Ihres Geldbeutels kann sich ändern. Der Gang zum Lebensmittelgeschäft verringert den Geldbetrag, der Gang zum Geldautomaten hingegen erhöht ihn.

Dieses Konzept gilt auch für Software. Ihre App kann Daten enthalten, die sich im Laufe der Zeit ändern.

Denken Sie an einen Beitrag in einer Social-Media-App. Möglicherweise hat Ihnen ein bestimmter Beitrag gefallen oder auch nicht. Der „Gefällt mir“-Status eines Beitrags kann ein- oder ausgeschaltet sein, wie die Lampe auf Ihrem Schreibtisch.

Die Website Ihrer Bank verweist auf Ihre Geldbörse in der analogen Welt. Die Banking-Software zeigt jederzeit den aktuellen Kontostand, den aktuellen Stand, an. Sie können diesen Status mithilfe der Banking-Software ändern. Sie könnten beispielsweise Geld auf ein anderes Konto überweisen, um den im Status „Saldo“ gespeicherten Betrag zu verringern.

Oftmals ändern sich solche zustandsbehafteten Daten nach einer Benutzerinteraktion, beispielsweise einem Klick auf eine Schaltfläche.

### State


In React arbeiten wir mit dem State, indem wir die Hook-Funktion verwenden useState.

Wir rufen die useState Funktion auf und übergeben den Anfangszustandswert als Argument. Dies ist der Wert, der in unserer App verwendet wird, ***bis sich etwas ändert***.

Der Aufruf der useStateFunktion gibt uns im Gegenzug zwei Dinge:

eine Variable mit dem aktuellen Zustand als Wert
Die setFunktion zum Festlegen eines neuen Status

```
import { useState } from "react";

function SocialMediaPost() {
  const [liked, setLiked] = useState(false);

  function toggleLiked() {
    setLiked(!liked);
  }

  return (
    <article>
      <p>Liked: {liked ? "Yes" : "No"}</p>
      <button type="button" onClick={toggleLiked}>
        {liked ? "Remove like" : "Add like"}
      </button>
    </article>
  );
}

```

💡Es gibt eine Namenskonvention für React-Apps, dass die Zustandsvariable und die Funktion immer dem Muster von ```x``` und folgen ```setX```

> 📙 Read more about the
> [**concept of state** in the React Docs](https://react.dev/learn/adding-interactivity).

Im React-Status wird jede Instanz einer Komponente gekapselt. Stellen Sie sich einen Feed in einer Social-Media-App vor. Der Feed ist eine Liste von Beiträgen. Jeder Beitrag ist eine einzelne Instanz der SocialMediaPostKomponente mit jeweils eigenem Status. Wenn Sie den „Gefällt mir“-Status eines bestimmten Beitrags ändern, bleiben alle anderen Beiträge unverändert.

Eine React-Komponente kann mehrere Zustände haben. ```useState``` Sie können die Funktion so oft nutzen , wie Sie benötigen.

Sie können alle Arten von Daten im Zustand speichern (wie boolesche Werte, Zahlen, Zeichenfolgen, Objekte oder Arrays).

```
import { useState } from "react";

function SocialMediaPost() {
  const [liked, setLiked] = useState(false);
  const [comments, setComments] = useState([]);
  const [views, setViews] = useState(0);

  /* ... */

  return <article>{/* ... */}</article>;
}
```

### Was passiert, wenn sich der Zustand ändert?

Um den Status in React zu verwalten, können wir nicht einfach eine „normale“ Variable verwenden und einen neuen Wert zuweisen. React muss darüber informiert werden, dass die Daten geändert wurden.

Dies hängt mit dem Renderzyklus von React-Komponenten zusammen.

Wenn React eine Komponente rendert, führt es die Komponentenfunktion aus, die JSX zurückgibt. Wenn die JSX eine Statusvariable enthält, verwendet sie den Wert der Variablen zu diesem Zeitpunkt, um sie in der JSX zu platzieren. Durch den Aufruf der setFunktion mit einem neuen Wert wird React darüber informiert, dass sich der Status geändert hat.

💡Das Ändern eines Status löst ein erneutes Rendern der Komponente aus.

Beim erneuten Rendern der Komponente führt React die Komponentenfunktion erneut von oben nach unten aus, wodurch erneut JSX zurückgegeben wird. Diesmal hat die Variable jedoch einen neuen Wert – den Wert, der beim Aufruf der setFunktion übergeben wurde. Dies bedeutet, dass der zurückgegebene JSX den neuen Wert enthält.

> 📙 Read more about
> [**state updates and re-rendering** in the React Docs](https://react.dev/learn/render-and-commit).

---

## Resources

- [React Docs: Adding Interactivity](https://react.dev/learn/adding-interactivity)
- [React Docs: Responding to Events](https://react.dev/learn/responding-to-events)
- [React Docs: A simple variable is not enough](https://react.dev/learn/state-a-components-memory#when-a-regular-variable-isnt-enough)
- [React Docs: Render and commit](https://react.dev/learn/render-and-commit)
- [MDN: react events and state](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_interactivity_events_state)

INFO von Resaurces:

Sobald die Komponente zum ersten Mal gerendert wurde, können Sie weitere Renderings auslösen, indem Sie ihren Status mit der setFunktion aktualisieren. Durch die Aktualisierung des Status Ihrer Komponente wird automatisch ein Rendering in die Warteschlange gestellt.

Bei nachfolgenden Renderings ruft React die Funktionskomponente auf, deren Statusaktualisierung das Rendering ausgelöst hat.

hier weiter:

https://react.dev/learn/state-a-components-memory

---


###  React with Arrays

6.[React with Arrays](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-with-arrays/react-with-arrays.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-with-arrays/challenges-react-with-arrays.md)

Reagieren Sie mit Arrays
Lernziele
Wissen, wie man .map()Listen in JSX rendert
Verstehen, wie Elemente aus einem Array von Objekten gerendert werden
Wissen, wie man einen eindeutigen Schlüssel für Listenelemente hinzufügt
Arrays in JSX
Um Elemente aus einem Array in React zu rendern, verwenden wir die Array-Methode .map().

Die Array-Methode .map()wird verwendet, um eine Transformation auf alle Elemente eines Arrays anzuwenden. Beim Rendern eines Arrays in JSX möchten wir genau das tun. Wir wandeln gerne jedes Element eines Arrays in ein JSX-Tag um. Aus diesem Grund verwenden wir .map().

```
function Drinks() {
  const drinks = ["water", "lemonade", "coffee", "tee"];

  return (
    <ul>
      {drinks.map((drink) => (
        <li>{drink}</li>
      ))}
    </ul>
  );
}
```

Schlüsseleigenschaft

Im obigen Beispiel fehlt ein kleiner, aber sehr wichtiger Teil: die keyRequisite!

Ohne die keyRequisite wird in der Konsole ein Fehler angezeigt:

Warning: Each child in a list should have a unique "key" prop.

Beim Rendern eines Arrays in JSX müssen Sie einen eindeutigen Bezeichner als Wert für die keyRequisite des ersten zurückgegebenen JSX-Tags übergeben .map(). Dies ist wichtig, damit React Änderungen verfolgen kann, die beim erneuten Rendern an den Daten auftreten.

Daher müssen Sie immer sicherstellen, dass Ihr Array eine eindeutige ID pro Element enthält. Sie können dies sicherstellen, indem Sie Objekte verwenden, um die Daten in Ihren Arrays zu definieren.

```
function Drinks() {
  const drinks = [
    { id: 0, name: "water" },
    { id: 1, name: "lemonade" },
    { id: 2, name: "coffee" },
    { id: 3, name: "tea" },
  ];

  return (
    <ul>
      {drinks.map(({ id, name }) => (
        <li key={id}>{name}</li>
      ))}
    </ul>
  );
}

```

> 📙 If you are interested in understanding the details behind this, you can read about
> [**the `key` prop** in the React Docs](https://react.dev/learn/rendering-lists#keeping-list-items-in-order-with-key).

💡Wenn Sie die key Prop an eine Komponente übergeben, können Sie in der Komponente nicht darauf zugreifen. Es handelt sich um eine spezielle Prop, die React nur intern verwendet.

function Drink({ name, key }) {
  console.log(key); // → undefined
  return <li>{name}</li>;
}

```
function Drinks() {
  const drinks = [
    { id: 0, name: "water" },
    { id: 1, name: "lemonade" },
    { id: 2, name: "coffee" },
    { id: 3, name: "tea" },
  ];

  return (
    <ul>
      {drinks.map(({ id, name }) => (
        <Drink key={id} name={name} />
      ))}
    </ul>
  );
}

```
Wenn Sie in diesem Beispiel auf das zugreifen möchten, idkönnen Sie es erneut als Requisite übergeben:
```<Drink key={id} id={id} name={name} />.```

Schlüsselfragmente

Wenn Sie eine Liste von Elementen rendern, die nicht in ein einzelnes JSX-Tag eingeschlossen sind, können Sie <Fragment>die Elemente mit a umschließen.

```
import { Fragment } from "react";

function Drinks() {
  const drinks = [
    { id: 0, name: "water", description: "very wet" },
    { id: 1, name: "lemonade", description: "quite sweet" },
    { id: 2, name: "coffee", description: "cold brew" },
    { id: 3, name: "tea", description: "earl grey, hot" },
  ];

  return (
    <dl>
      {drinks.map(({ id, name, description }) => (
        <Fragment key={id}>
          <dt>{name}</dt>
          <dd>{description}</dd>
        </Fragment>
      ))}
    </dl>
  );
}
```
  
💡<>…</>Hier können Sie nicht die kurze Syntax ( ) für verwenden, da Sie die Requisite an <Fragment>übergeben müssen . Die kurze Syntax erlaubt keine Übergabe von Requisiten.key<Fragment>
  
  
## Resources

- [React Docs: Rendering Lists](https://react.dev/learn/rendering-lists)
  
  
---
  
### React State 2
  
7.[React State 2](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-2/react-state-2.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-2/challenges-react-state-2.md)
  
## Learning Objectives

Status zwischen Komponenten teilen
  
Den Staat weitergeben
  
Der Wert einer Zustandsvariablen und die Setter-Funktion können als Props an untergeordnete Komponenten weitergegeben werden. Da es sich um Funktionen und Werte handelt, können sie wie alle anderen Daten weitergegeben werden.

```
function Parent() {
  const [count, setCount] = useState(0);

  function handleIncrement() {
    setCount(count + 1);
  }

  return <Child count={count} onIncrement={handleIncrement} />;
}
```

```
function Child({ count, onIncrement }) {
  return (
    <>
      <p>Count: {count}</p>
      <button onClick={onIncrement}>increment</button>
    </>
  );
}
```

### Lifting State Up

Wenn wir über mehrere Komponenten verfügen, die einen gemeinsamen Status benötigen, können wir den Status auf die übergeordnete Komponente übertragen und ihn als Requisiten weitergeben. Dies wird als „Anheben des Status nach oben“ bezeichnet, da Sie normalerweise mit dem Status direkt in der untergeordneten Komponente beginnen und ihn dann bei Bedarf in immer mehr Komponenten in die übergeordneten Komponenten verschieben.

Eine Zustandsvariable kann an mehrere untergeordnete Komponenten weitergegeben werden. Die untergeordneten Komponenten können dann die Statusvariable aktualisieren, indem sie die Setter-Funktion aufrufen.

Jede Zustandsvariable sollte so niedrig wie möglich im Komponentenbaum liegen, aber bei Bedarf hoch sein. Wenn das Ganze Appüber die Zustandsvariable Bescheid wissen muss, sollte diese in der AppKomponente vorhanden sein. Wenn nur untergeordnete Komponenten Articleüber die Zustandsvariable Bescheid wissen müssen, sollte diese in der ArticleKomponente leben.

Betrachten Sie das folgende Beispiel:
  
<img src="lifting-state-up.png" width="616" height="694" />

Here we find that a `Link` in the `Navigation` component needs to know about a state that previously
existed in the `Article` component. We can lift the state up to the `App` component and pass it down
to the `Article` component as a prop.

> 📙 Read more about
> [**Sharing State Between Components** in the React docs](https://react.dev/learn/sharing-state-between-components).

## Umgang mit Formulardaten
  
Formulardaten verwenden onSubmit
  
Wir können den onSubmitEvent-Handler verwenden, um Formulardaten zu verarbeiten. Der onSubmitEvent-Handler wird aufgerufen, wenn der Benutzer das Formular absendet. Wir können die Formulardaten (genau wie bei normalem JavaScript) vom eventObjekt abrufen.

```js
function SearchForm() {
  function handleSubmit(event) {
    event.preventDefault();
    const form = event.target;
    const searchTerm = form.elements.searchTerm.value;
    console.log("A new search term was submitted:", searchTerm);
  }
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="searchTerm">Search</label>
      <input name="searchTerm" id="searchTerm" />
      <button>Search</button>
    </form>
  );
}
```
  
  


In diesem Beispiel wird der Wert des Eingabeelements nicht manuell von React gesteuert: Die Eingabe ist eine „unkontrollierte Eingabe“. Der Wert wird vom Browser verwaltet. Im Submit-Event-Handler „schauen“ wir einfach auf das Eingabefeld und lesen den Wert aus dem DOM.

### Verwendung kontrollierter Eingaben
  
Wir können React verwenden, um den Wert eines Eingabeelements zu steuern. Dies wird als „kontrollierte Eingabe“ bezeichnet. Das bedeutet, dass wir das Wertattribut des Eingabeelements manuell festlegen. Wir können eine Zustandsvariable mit dem Wertattribut des Eingabeelements verbinden. Auf diese Weise hat das Eingabeelement immer den gleichen Wert wie die Zustandsvariable. In Kombination mit dem onChangeEvent-Handler können wir die Statusvariable aktualisieren, wenn der Benutzer etwas in das Eingabefeld eingibt

```js
function SearchForm() {
  const [searchTerm, setSearchTerm] = useState("");

  function handleSubmit() {
    event.preventDefault();
    console.log("A new search term was submitted:", searchTerm);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="searchTerm">Search</label>
      <input
        name="searchTerm"
        id="searchTerm"
        value={searchTerm}
        onChange={(event) => setSearchTerm(event.target.value)}
      />
      <button>Search for {searchTerm}</button>
    </form>
  );
}
```
  
In diesem Beispiel kennen Sie immer den Wert des eingegebenen Suchbegriffs. Da es sich um eine Zustandsvariable handelt, können Sie sie an anderen Stellen in Ihrer Anwendung verwenden. Wenn möglich, sollten Sie unkontrollierte Eingaben bevorzugen, manchmal müssen Sie jedoch eine kontrollierte Eingabe verwenden.

## Möglicherweise benötigen Sie eine kontrollierte Eingabe, wenn

Suchergebnisse anzeigen, während der Benutzer tippt,
Automatische Vervollständigung der Benutzereingaben oder
Validierung der Benutzereingaben.
Statusaktualisierungen erfolgen nicht sofort
Wenn wir die Setter-Funktion einer Zustandsvariablen aufrufen, aktualisiert React die Zustandsvariable nicht sofort. Stattdessen wird der interne Wert aktualisiert und ein erneutes Rendern der Komponente geplant.

```js
// ⚠️ This code is broken!
function Counter() {
  const [count, setCount] = useState(0); // count is 0 initially

  function handleIncrement() {
    // when this is first called, count is still 0
    console.log(count); // → 0

    // this will set reacts internal state to 1,
    // but does not update the count variable
    setCount(count + 1);
    console.log(count); // → 0

    // the count variable is still 0, thus count + 1 is still 1,
    // so react's internal state will still be 1
    setCount(count + 1);
    console.log(count); // → 0

    // since setter functions were called
    // react will schedule a re-render of
    // the component with the new count value of 1
  }

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>increment by 2</button>
    </>
  );
}
```
Dieses Verhalten kann unerwartet sein, es ist jedoch wichtig zu verstehen, dass Zustandsvariablen nicht sofort aktualisiert werden.

Es gibt verschiedene Möglichkeiten, den obigen Code zu beheben. In diesem Beispiel könnten wir anrufen setCount(count + 2)und fertig. Wenn wir aus irgendeinem Grund zweimal aufrufen müssen setCount, können wir die funktionale Form der Setter-Funktion verwenden, die den aktuellen internen Wert der Zustandsvariablen als Argument bereitstellt.

``` 
// ⚠️ This code is unnecessary complicated, but it works!
function Counter() {
  const [count, setCount] = useState(0); // count is 0 initially

  function handleIncrement() {
    // when this is first called, count is still 0
    console.log(count); // → 0

    // this will set reacts internal state to 1,
    // but does not update the count variable
    setCount((prevCount) => prevCount + 1);
    console.log(count); // → 0

    // the internal value of count is 1,
    // we get it as the the first parameter of the function we pass to the setter.
    // 1 + 1 is 2, so react's internal state will now be _2_
    setCount((prevCount) => prevCount + 1);
    console.log(count); // → 0

    // since setter functions were called
    // react will schedule a re-render of
    // the component with the new count value of _2_
  }

  return (
    <>
      <p>Count: {count}</p>
      <button onClick={handleIncrement}>increment by 2</button>
    </>
  );
}


💡Hier wird das Präfix prevverwendet, um anzuzeigen, dass der Wert der vorherige Wert der Zustandsvariablen ist. Eine weitere gängige Konvention besteht darin, nur den ersten Buchstaben der Statusvariablen als Parameternamen zu verwenden: setCount(c => c + 1).

📙Lesen Sie mehr über das Aktualisieren des Status basierend auf dem vorherigen Status. Ich habe den Status aktualisiert, aber durch die Protokollierung erhalte ich den alten Wert in den React-Dokumenten.

### Reagieren Sie auf Hooks

Die useStateFunktion ist Teil einer breiteren Reihe von React-Funktionen, die Komponenten zusätzliche Kräfte verleihen.

Hooks sind Funktionen, die es Komponentenfunktionen ermöglichen, sich in React-Funktionen (wie den Zustand) einzubinden und es Komponenten ermöglichen, mehr zu tun, als eine herkömmliche JavaScript-Funktion kann. Sie folgen der Namenskonvention useXzy.

Häufige Haken, auf die Sie stoßen werden, sind useStateund useEffect.

Bei der Verwendung von Hooks müssen Sie einige Regeln beachten:

Rufen Sie Hooks nur auf der obersten Ebene auf. Rufen Sie Hooks nicht innerhalb von Schleifen, Bedingungen oder verschachtelten Funktionen auf.
Rufen Sie Hooks nur von React-Funktionskomponenten oder benutzerdefinierten Hooks auf. Rufen Sie Hooks nicht über reguläre JavaScript-Funktionen auf.

> 📙 Read more about [**Hooks** in the React Docs](https://reactjs.org/docs/hooks-overview.html)
> from when they were introduced to React.

---

## Resources

- [Sharing State Between Components in the React Docs](https://react.dev/learn/sharing-state-between-components)
- [Updating state based on the previous state in the React Docs](https://react.dev/apis/react/useState#updating-state-based-on-the-previous-state)
- [I’ve updated the state, but logging gives me the old value in the React Docs](https://react.dev/apis/react/useState#ive-updated-the-state-but-logging-gives-me-the-old-value)
- [Hooks at a Glance in the React Docs](https://reactjs.org/docs/hooks-overview.html)  
  
  

---  
  
8.[React State 3](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-3/react-state-3.md) [Challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-state-3/challenges-react-state-3.md)

### REACT STATE 3

Wissen, wie mit Arrays und Objekten im Status umgegangen wird
Wissen, was eine Zustandsmutation ist und wie man sie vermeidet
Vermeidung von Zustandsmutationen
Unabhängig davon, wie komplex der Zustand Ihrer Anwendung (Objekt, Array, Array von Objekten) ist, müssen Sie den Zustand immer als unveränderlich behandeln. Das bedeutet, dass Sie den Status nicht direkt ändern sollten, indem Sie ihm beispielsweise einen neuen Wert zuweisen.

Um Mutationen beim Aktualisieren des Status zu vermeiden, müssen Sie dies tun

ein neues Objekt/Array erstellen (oder eine Kopie des vorhandenen erstellen) und
Verwenden Sie die Setter-Funktion mit der kürzlich erstellten/aktualisierten Kopie, um ein erneutes Rendern zu veranlassen.
Objekte im Status aktualisieren
Um eine Kopie eines Objekts zu erstellen und nur einige Eigenschaften zu ändern, können Sie die Spread-Syntax verwenden:

```
const [person, setPerson] = useState({
  firstName: "John",
  lastName: "Doe",
});

function handleChangeFirstName(firstName) {
  setPerson({ ...person, firstName });
}

// Somewhere else:
handleChangeFirstName("Jane");
```

❗️Wenn Sie einen neuen Wert direkt zuweisen würden, würden Sie den Zustand ändern. Das ist schlecht, weil wir den Staat als unveränderlich behandeln müssen. Dies kann zu schwer zu findenden Fehlern führen.

// ⚠️ NEVER DO THIS
function handleChangeFirstName(firstName) {
  person.firstName = firstName;
  setPerson(person);
}
> 📙 Learn more about [**Updating Objects in State** in the React Docs](https://react.dev/learn/updating-objects-in-state)..

### Arrays im Status aktualisieren

Wie Sie wissen, gibt es mehrere Möglichkeiten, Arrays zu aktualisieren. Einige von ihnen verändern jedoch das Array, andere nicht.


|           | avoid (mutates the array)           | prefer (returns a new array) |
| --------- | ----------------------------------- | ---------------------------- |
| adding    | `push`, `unshift`                   | `[...arr]` spread syntax     |
| removing  | `pop`, `shift`, `splice`            | `filter`                     |
| replacing | `splice`, `arr[i] = ...` assignment | `map`                        |
| sorting   | `reverse`, `sort`                   | copy the array first         |

> 💡 It does not matter whether your array state contains only primitives or other objects / arrays;
> in all cases, you should only use the preferred array methods.


Zu einem Array hinzufügen

Um einem Array ein Element hinzuzufügen, können Sie die Spread-Syntax verwenden:

const [numbers, setNumbers] = useState([0, 1, 2]);

function handleAppendNumber(number) {
  setNumbers([...numbers, number]);
}

// Somewhere else:
handleAppendNumber(3);

function handlePrependNumber(number) {
  setNumbers([number, ...numbers]);
}

// Somewhere else:
handlePrependNumber(-1);
Aus einem Array entfernen
Um ein Element aus einem Array zu entfernen, können Sie die filterMethode verwenden:

const [numbers, setNumbers] = useState([0, 1, 2]);

function handleRemoveNumber(numberToRemove) {
  setNumbers(numbers.filter((number) => number !== numberToRemove));
}

// Somewhere else:
handleRemoveNumber(1);
Ersetzen eines Array-Elements
Um ein Element in einem Array zu ersetzen, können Sie die mapMethode verwenden:

const [numbers, setNumbers] = useState([0, 1, 2]);

function handleReplaceNumber(oldNumber, newNumber) {
  setNumbers(
    numbers.map((number) => {
      if (number === oldNumber) return newNumber;
      return number;
    })
  );
}

// Somewhere else:
handleReplaceNumber(1, 1337);
> 📙 Learn more about [**Updating arrays without mutation** in the React Docs](https://react.dev/learn/updating-arrays-in-state#updating-arrays-without-mutation).

Aktualisieren von Arrays von Objekten im Status
Meistens werden Sie in Ihrem Bundesstaat auf Arrays von Objekten stoßen.

Ein neues Objekt hinzufügen
Sie können dem Statusarray ein neues Objekt hinzufügen, indem Sie die Spread-Syntax verwenden:

const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleAddTree(tree) {
  setTrees([...trees, tree]);
}

// Somewhere else:
handleAddTree({id: 3, name: "Spruce", height: 13})
Entfernen eines Objekts
Um ein Objekt zu entfernen, können Sie filterdas Array nach einer eindeutigen Kennung suchen. In den meisten Fällen liegt dieser Bezeichner im Gültigkeitsbereich, da das relevante Objekt über gerendert wird map.

const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleRemoveTree(idToRemove) {
  setTrees(trees.filter((tree) => tree.id !== idToRemove));
}

// Somewhere else:
handleRemoveTree(0);
Ersetzen eines Objekts
Um ein Objekt zu ersetzen, können Sie mapmit dem aktualisierten Objekt ein neues Array erstellen. Denken Sie daran, zuerst eine Kopie des Objekts zu erstellen, da sonst der Status geändert wird.

const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleSetNewHeightForTree(id, height) {
  setTrees(
    trees.map((tree) => {
      if (tree.id === id) return { ...tree, height };
      return tree;
    })
  );
}

// Somewhere else:
handleSetNewHeightForTree(0, 8);
Sortieren eines Arrays von Objekten
Um ein Array von Objekten zu sortieren, können Sie sorteine Kopie des Arrays mit einer benutzerdefinierten Vergleichsfunktion verwenden. Die Vergleichsfunktion gibt eine Zahl zurück, die zur Bestimmung der Reihenfolge der Elemente verwendet wird.

const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

function handleSortTreesByHeight() {
  setTrees([...trees].sort((a, b) => a.height - b.height));
}
> 📙 Learn more about [**Updating objects inside Arrays** in the React Docs](https://react.dev/learn/updating-arrays-in-state#updating-objects-inside-arrays).

Wahl der Staatsstruktur
Bei der Wahl Ihrer Staatsstruktur gibt es einige häufige Fallstricke.

Gruppenbezogener Status
Wenn Sie einen Status haben, der zusammengehört (und aktualisiert wird), gruppieren Sie ihn in einem einzigen Objekt. Dies erleichtert die Aktualisierung des Status.

// ❌ MEH
const [userName, setUserName] = useState("Alex");
const [userAge, setUserAge] = useState(28);

// ✅ BETTER
const [user, setUser] = useState({ name: "Alex", age: 28 });
Vermeiden Sie einen redundanten Zustand
Wenn Sie einen Wert haben, der von einem Status abgeleitet ist, sollten Sie es vermeiden, ihn im Status zu speichern. Verwenden Sie stattdessen einfach eine normale Variable.

Das Problem mit dem redundanten Status besteht darin, dass er nicht mehr mit der Quelle der Wahrheit synchronisiert sein kann, wenn Sie vergessen, ihn korrekt zu aktualisieren.

// ❌ BAD
const [user, setUser] = useState({ name: "Alex", age: 28 });
const [isAdult, setIsAdult] = useState(user.age >= 18);

// ✅ GOOD
const [user, setUser] = useState({ name: "Alex", age: 28 });
const isAdult = user.age >= 18;
Vermeiden Sie Duplikate im Bundesstaat
Vermeiden Sie es, denselben Wert an mehreren Stellen im Bundesstaat zu speichern. Dies kann zu Fehlern führen und die Aktualisierung des Status erschweren.

// ❌ BAD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [selectedTree, setSelectedTree] = useState(trees.find((tree) => tree.id === 0));

// Somewhere else:
setSelectedTree(trees.find((tree) => tree.id === 2));


// ✅ GOOD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [selectedTreeId, setSelectedTreeId] = useState(0);

const selectedTree = trees.find((tree) => tree.id === selectedTreeId);

// Somewhere else:
setSelectedTreeId(2);
Vermeiden Sie doppelte Listen im Bundesstaat
Wenn Sie eine Liste von Elementen im Status haben, sollten Sie es vermeiden, eine abgeleitete Version davon in einer anderen Statusvariablen zu speichern. Dies ist ein häufiger Fehler, wenn Sie eine gefilterte Version der Liste anzeigen möchten.

// ❌ BAD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [filteredTrees, setFilteredTrees] = useState(trees.filter((tree) => tree.height > 7));

// Somewhere else:
setFilteredTrees(trees.filter((tree) => tree.height > 9));

// ✅ GOOD
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height 7.5},
  { id: 1, name: "Beech", height 6},
  { id: 2, name: "Pine", height 10}
]);

const [minHeight, setMinHeight] = useState(7);

const filteredTrees = trees.filter((tree) => tree.height > minHeight);

> 📙 Read more about [**Choosing the State Structure** in the React Docs](https://react.dev/learn/choosing-the-state-structure). The Docs have many more examples and explanations.

---

## Resources

- [Updating Objects in State (React Docs)](https://react.dev/learn/updating-objects-in-state)
- [Updating Arrays in State (React Docs)](https://react.dev/learn/updating-arrays-in-state)



9. [React Effects and Fetch](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-effects-and-fetch/react-effects-and-fetch.md)[Challenges]

10. [React with Local Storage](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-with-local-storage/react-with-local-storage.md)[Challenges]
