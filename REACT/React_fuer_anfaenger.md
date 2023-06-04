### React für anfänger

# Was sind Props in React:


Props, oder Eigenschaften, sind eine Möglichkeit, Daten an ein untergeordnetes Komponente zu übergeben. Eine Komponente erhält ein Props-Objekt als ersten Funktionsparameter.

Hier ist ein Beispiel, wie Props in einer Komponente verwendet werden:


```js

function UserCard(props) {
  return <div>{props.name}</div>;
}
````

Das Props-Objekt enthält die übergebenen Eigenschaften. In diesem Fall greifen wir auf die Eigenschaft name zu, indem wir props.name verwenden.

Um die Verwendung von Props einfacher zu machen, können wir das Props-Objekt auch in den Funktionsparametern destrukturieren:

```js
function UserCard({ name }) {
  return <div>{name}</div>;
}
````


In diesem Fall greifen wir direkt auf die Eigenschaft name zu, ohne props zu verwenden.


Du kannst beliebige Namen für deine Props verwenden. Es gibt jedoch einige Namenskonventionen. 
Beispielsweise werden boolesche Props häufig mit "is", "has" oder "should" als Präfix verwendet, z. B. isDisabled, hasError oder shouldShow. 
Props, die Funktionen enthalten, werden häufig mit "on" als Präfix verwendet, z. B. onClick, onSubmit oder onHover. 
Wenn du diese Konventionen befolgst, wird es einfacher, den Zweck der Prop zu verstehen.

Props können jeden Typ haben, z. B. Zeichenkette, Zahl, Array, Objekt, Funktion usw.

Um Props an eine Komponente zu übergeben, verwendest du Attribute. Hier ist ein Beispiel:

```js
<UserCard name="Alex" />
```


Du kannst verschiedene Arten von Daten als Props übergeben:


```js

<UserCard
  name="Alex"
  age={25}
  onContact={() => console.log("let's chat!")}
  isFavorite={true}
  favoriteFoods={["Pasta", "Salad"]}
  contactDetails={{ email: "alex@neuefische.de", phone: "123456789" }}
/>

```
Beachte, dass Zeichenketten-Props(Strings) mit doppelten Anführungszeichen übergeben werden müssen, während alle anderen Props mit geschweiften Klammern übergeben werden.

Es gibt eine verkürzte Syntax für boolesche Props. Wenn der Wert true sein soll, kannst du den Wert weglassen:

```js
<UserCard isFavorite />

```

Wenn du ein Attribut auslässt, wird der Wert undefined für diese Prop sein.


Du kannst Props verwenden, um Teile einer Komponente bedingt zu rendern. Hier ist ein Beispiel:

```js
function UserCard({ name, isFavorite }) {
  return (
    <div>
      {name}
      {isFavorite ? <span>🌟</span> : null}
    </div>
  );
}

```

In diesem Fall wird das Sternchen (🌟) nur gerendert, wenn isFavorite true ist.

Du kannst keine if-Anweisungen direkt in JSX verwenden, da nur Ausdrücke erlaubt sind.
Du kannst jedoch eine if-Anweisung außerhalb des JSX verwenden, 
um bedingte Logik durchzuführen.


# Hook

Ein Hook in React ist eine Funktion, die es dir ermöglicht, zusätzliche Funktionen und Eigenschaften in Funktionskomponenten zu verwenden. Hooks wurden mit React 16.8 eingeführt, um die Verwendung von Zustand(useState) und anderen React-Funktionen in Funktionskomponenten zu erleichtern.

Hooks dienen dazu, den Zustand und das Verhalten in Funktionskomponenten zu verwalten, ohne dass eine Klasse verwendet werden muss. Sie ermöglichen es dir, den Zustand zu speichern, Lebenszyklusmethoden zu verwenden, Nebeneffekte auszuführen und vieles mehr. Mit Hooks können Funktionskomponenten ähnliche Fähigkeiten wie Klassenkomponenten erlangen, während sie gleichzeitig einfacher und lesbarer bleiben.

Einige der häufig verwendeten Hooks in React sind:

- useState: Verwendet, um den Zustand in Funktionskomponenten zu speichern und zu aktualisieren.  

- useEffect: Verwendet, um Nebeneffekte auszuführen, wie das Abonnieren von Ereignissen oder das Laden von Daten, nachdem die Komponente gerendert wurde.

- useContext: Verwendet, um den aktuellen Wert eines React-Kontexts in einer Komponente zu erhalten.

- useRef: Verwendet, um eine mutable Referenz auf ein DOM-Element oder einen anderen Wert zu erstellen, der über den Rendervorgang hinweg erhalten bleibt.

- useMemo: Verwendet, um teure Berechnungen zu memoisieren und ihre Ergebnisse zwischen Rendervorgängen zu speichern.

- useCallback: Verwendet, um eine memoisierte Version einer Callback-Funktion zu erstellen, die nur bei Bedarf neu erstellt wird.

Es gibt noch weitere Hooks, die spezifische Funktionalitäten in React bieten. Hooks ermöglichen es Entwicklern, den Zustand und das Verhalten von Komponenten auf eine übersichtliche und deklarative Weise zu verwalten und erleichtern die Wiederverwendung von Logik zwischen verschiedenen Komponenten.

Es ist wichtig zu beachten, dass Hooks in Funktionskomponenten verwendet werden müssen und nicht in Klassenkomponenten. Sie bieten eine moderne und flexible Alternative zur Verwendung von Zustand und Lifecycle-Methoden in React


Die useState-Funktion (useState) ist Teil einer umfassenderen Funktionssammlung in React, die den Komponenten zusätzliche Funktionen ermöglicht. Hooks sind Funktionen, die Komponentenfunktionen erlauben, sich in React-Funktionen einzuklinken und ihnen ermöglichen, mehr zu tun als eine traditionelle JavaScript-Funktion. Sie folgen der Namenskonvention "useXyz".

Beim Verwenden von Hooks müssen wir ein paar Regeln beachten:

Rufe Hooks nur auf der obersten Ebene auf. Rufe Hooks nicht in Schleifen, Bedingungen oder verschachtelten Funktionen auf.
Rufe Hooks nur in React-Funktionskomponenten oder benutzerdefinierten Hooks auf. Rufe Hooks nicht in regulären JavaScript-Funk


# Hooks Beispiele um die zu verstehen

Hier sind sehr einfache Beispiele für jeden der genannten Hooks:

useState:

```js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
````

In diesem Beispiel wird der Zustand "count" mit einem anfänglichen Wert von 0 erstellt. Durch Klicken auf den Button wird der Zustand inkrementiert und die Komponente wird erneut gerendert, wobei der aktualisierte Wert angezeigt wird.


useEffect:

```js
import React, { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);

  return <p>Data: {data}</p>;
}
```

In diesem Beispiel wird der Effekt verwendet, um Daten von einer API abzurufen. Beim ersten Rendern der Komponente wird die Fetch-Anfrage durchgeführt und die erhaltenen Daten in den Zustand "data" gesetzt. Der leere Array als zweites Argument gibt an, dass der Effekt nur einmal nach dem ersten Rendern ausgeführt werden soll.


useContext:

```js
import React, { useContext } from 'react';
import ThemeContext from './ThemeContext';

function ThemeSwitcher() {
  const theme = useContext(ThemeContext);

  return (
    <div>
      <p>Current Theme: {theme}</p>
      {/* weitere JSX-Komponenten */}
    </div>
  );
}
````

In diesem Beispiel wird der aktuelle Wert eines React-Kontexts mit dem Namen "ThemeContext" in der Komponente verwendet. Der Wert kann dann in der Komponente verwendet werden, um das Thema der Benutzeroberfläche dynamisch anzupassen.

useRef:

```js
import React, { useRef } from 'react';

function InputFocus() {
  const inputRef = useRef();

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Focus Input</button>
    </div>
  );
}
````

In diesem Beispiel wird ein ref mit dem Namen "inputRef" erstellt und dem Eingabefeld zugewiesen. Durch Klicken auf den Button wird das Eingabefeld mit der "focus()" Methode des ref fokussiert.

useMemo:

```js
import React, { useMemo } from 'react';

function ExpensiveCalculation({ num1, num2 }) {
  const result = useMemo(() => {
    // Teure Berechnungen basierend auf num1 und num2
    return num1 * num2;
  }, [num1, num2]);

  return <p>Result: {result}</p>;
}
````

In diesem Beispiel wird die useMemo-Hook verwendet, um teure Berechnungen nur dann durchzuführen, wenn sich die abhängigen Werte (hier: num1 und num2) ändern. Der berechnete Wert wird zwischengespeichert und bei nachfolgenden Rendervorgängen wiederverwendet, solange sich die abhängigen Werte nicht ändern.

useCallback:

```js
import React, { useCallback } from 'react';

function Button({ onClick }) {
  const handleClick = useCallback(() => {
    onClick('Button clicked');
  }, [onClick]);

  return <button onClick={handleClick}>Click Me</button>;
}

````

In diesem Beispiel wird die useCallback-Hook verwendet, um eine memoisierte Version einer Callback-Funktion zu erstellen. Dadurch wird sichergestellt, dass die Callback-Funktion nur dann neu erstellt wird, wenn sich das abhängige Argument (hier: onClick) ändert. Dies kann die Leistung optimieren, indem unnötige Re-Renders vermieden werden.

Diese Beispiele sollen dir einen grundlegenden Eindruck von den verschiedenen Hooks geben und wie sie in React funktionieren. Beachte jedoch, dass Hooks vielfältige Einsatzmöglichkeiten haben und in komplexeren Szenarien noch weitere Funktionen bieten können.




# useState 

Ein Zustand (useState) ist eine Datenquelle, die sich im Laufe der Zeit ändert. Stell dir eine Schreibtischlampe vor. Sie kann ein- oder ausgeschaltet sein. Die Lampe befindet sich zu einem bestimmten Zeitpunkt in einem bestimmten Zustand, und dieser Zustand kann sich im Laufe der Zeit ändern.

Ein weiteres Beispiel könnte der Geldbetrag in deinem Portemonnaie sein. Zu jedem gegebenen Zeitpunkt hast du einen bestimmten Geldbetrag in deinem Portemonnaie, aber dieser Betrag kann sich ändern. Der Zustand deines Portemonnaies kann sich ändern. Wenn du zum Lebensmittelgeschäft gehst, nimmt der Geldbetrag ab, während er sich erhöht, wenn du zum Geldautomaten gehst.
Dieses Konzept gilt auch für Software. Deine App kann Daten enthalten, die sich im Laufe der Zeit ändern.

Denke an einen Beitrag in einer Social-Media-App. Du könntest einen bestimmten Beitrag mögen oder nicht mögen. Der "Gefällt mir"-Zustand (useState) eines Beitrags kann an oder aus sein, ähnlich wie bei der Lampe auf deinem Schreibtisch.

Die Website deiner Bank entspricht deinem Portemonnaie in der analogen Welt. Zu jedem Zeitpunkt zeigt die Banksoftware den aktuellen Kontostand, den aktuellen Zustand, an. Du kannst die Banksoftware verwenden, um diesen Zustand zu ändern. Zum Beispiel könntest du Geld auf ein anderes Konto überweisen, um die im "Kontostand"-Zustand gespeicherte Zahl (useState) zu verringern.


### Zustand in React:

In React arbeiten wir mit dem Zustand (useState), indem wir die Funktion "useState" verwenden.

Wir rufen die Funktion "useState" auf und übergeben den Wert des anfänglichen Zustands als Argument. Dies ist der Wert, der in unserer App verwendet wird, bis etwas geändert wird.
Das Aufrufen der Funktion "useState" gibt uns zwei Dinge zurück:

-eine Variable mit dem aktuellen Zustand als Wert (z. B. const [liked, setLiked] = useState(false);) 

-die "set"-Funktion, um einen neuen Zustand festzulegen (z. B. setLiked(!liked);)

Hier ist ein Beispiel, wie "useState" in einer React-Komponente verwendet wird:

```js

import { useState } from "react";

function SocialMediaPost() {
  const [liked, setLiked] = useState(false);

  function toggleLiked() {
    setLiked(!liked);
  }

  return (
    <article>
      <p>Gefällt mir: {liked ? "Ja" : "Nein"}</p>
      <button type="button" onClick={toggleLiked}>
        {liked ? "Gefällt mir entfernen" : "Gefällt mir hinzufügen"}
      </button>
    </article>
  );
}
````
In diesem Beispiel verwenden wir "useState", um einen Zustand (liked) mit dem anfänglichen Wert "false" zu erstellen. Die Funktion "toggleLiked" wird aufgerufen, wenn auf den Button geklickt wird, und ändert den Zustand von "liked" mit Hilfe der "setLiked"-Funktion.

Beachte, dass es eine Namenskonvention für React-Apps gibt, bei der die Zustandsvariable und die Funktion immer dem Muster "x" und "setX" folgen.

Eine React-Komponente kann mehrere Zustände haben. Du kannst die "useState"-Funktion so oft verwenden, wie du möchtest. Du kannst alle Arten von Daten im Zustand speichern, wie z. B. boolesche Werte, Zahlen, Zeichenketten, Objekte oder Arrays.

### Was passiert, wenn sich der Zustand ändert?

Um den Zustand in React zu handhaben, können wir nicht einfach eine "normale" Variable verwenden und ihr einen neuen Wert zuweisen. React muss darüber informiert werden, dass die Daten geändert wurden.

Dies hängt mit dem Renderzyklus von React-Komponenten zusammen.
Wenn React eine Komponente rendert, führt es die Komponentenfunktion aus, die JSX zurückgibt. Wenn das JSX eine Zustandsvariable enthält, verwendet es den Wert der Variablen zu diesem Zeitpunkt, um ihn in das JSX einzufügen. 

### ***Das Aufrufen der "set"-Funktion mit einem neuen Wert informiert React darüber, dass sich der Zustand geändert hat.***

Das Ändern eines Zustands (useState) löst eine erneute Rendervorgang der Komponente aus. Bei der erneuten Rendervorgang führt React die Komponentenfunktion erneut von oben nach unten aus, die dann JSX zurückgibt. Diesmal hat die Variable jedoch einen neuen Wert - den Wert, der mit dem Aufruf der "set"-Funktion übergeben wurde. Dies bedeutet, dass das zurückgegebene JSX den neuen Wert enthält.

Beispiel 1

```js
import React, { useState } from 'react';

export default function Parent() {
  const [countState, setCountState] = useState(0);

  function incrementCount() {
    setCountState(countState + 1);
  }

  return (
    <div>
      <h2>Parent Component</h2>
      <Child count={countState} increment={incrementCount} />
    </div>
  );
}

function Child({ count, increment }) {
  return (
    <div>
      <h3>Child Component</h3>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}


```
In diesem Beispiel wird der Zustand "countState" in der Parent-Komponente mit dem useState-Hook initialisiert. Die Parent-Komponente gibt den Wert von "countState" und die Funktion "incrementCount" als Props an die Child-Komponente weiter.

Die Child-Komponente verwendet die übergebenen Props, um den Wert von "count" anzuzeigen und die "increment"-Funktion auszuführen, wenn der Button geklickt wird.

Beispiel 2

```js
import React, { useState } from 'react';

export default function Parent() {
  const [nameState, setNameState] = useState(''); // Zustand "nameState" wird mit einem leeren String initialisiert

  function updateName(newName) {
    setNameState(newName); // Funktion zum Aktualisieren des Namenszustands
  }

  return (
    <div>
      <h2>Parent Component</h2>
      <Child name={nameState} changeName={updateName} /> {/* Übergibt den Namenszustand und die "updateName"-Funktion als Props an das Child */}
    </div>
  );
}

function Child({ name, changeName }) {
  function handleInputChange(event) {
    const newName = event.target.value; // Liest den neuen Namen aus dem Texteingabefeld
    changeName(newName); // Ruft die "changeName"-Funktion auf, um den Namen zu aktualisieren
  }

  return (
    <div>
      <h3>Child Component</h3>
      <input type="text" value={name} onChange={handleInputChange} /> {/* Das Texteingabefeld zeigt den aktuellen Namen an und ruft die "handleInputChange"-Funktion auf, wenn sich der Wert ändert */}
      <p>Name: {name}</p> {/* Zeigt den aktuellen Namen an */}
    </div>
  );
}

````
Die Parent-Komponente verwendet den Zustand nameState, um den aktuellen Namen zu speichern. Durch die Funktion updateName kann der Name aktualisiert werden, indem sie den neuen Namen an setNameState übergibt.

In der Parent-Komponente werden nameState und updateName als Props an das Child weitergegeben.

Das Child-Komponente nutzt die übergebenen Props, um den aktuellen Namen anzuzeigen und die Funktion changeName aufzurufen, wenn sich der Wert im Texteingabefeld ändert. Die Funktion handleInputChange extrahiert den neuen Namen aus dem Event-Objekt und ruft dann changeName auf, um den Namen zu aktualisieren.

In diesem Code wird die Funktion changeName in der Parent-Komponente definiert und anschließend als Prop an das Child übergeben. Die Funktion handleInputChange im Child ruft diese übergebene changeName-Funktion auf, um den Namen zu aktualisieren.

Die changeName-Funktion kann beispielsweise wie folgt aussehen:

```js

function updateName(newName) {
  // Hier kannst du deine eigene Logik zur Aktualisierung des Namens implementieren
  console.log("Neuer Name:", newName);
  // ...
}
````


# Das Handling von Formulardaten: Verwendung von `onSubmit` für Formulardaten:

Wir können das `onSubmit` -Ereignis verwenden, um Formulardaten zu handhaben. Das `onSubmit` -Ereignis wird aufgerufen, wenn der Benutzer das Formular absendet. Wir können die Formulardaten (genau wie in regulärem JavaScript) aus dem Event-Objekt erhalten.

```js
function SearchForm() {
  function handleSubmit(event) {
    event.preventDefault();
    const form = event.target;
    const searchTerm = form.elements.searchTerm.value;
    console.log("Eine neue Suchanfrage wurde abgeschickt:", searchTerm);
  }
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="searchTerm">Suche</label>
      <input name="searchTerm" id="searchTerm" />
      <button>Suchen</button>
    </form>
  );
}
````

In diesem Beispiel wird der Wert des Eingabefelds nicht von React kontrolliert: Das Eingabefeld ist ein "uncontrolled input". Der Wert wird vom Browser verwaltet. Im onSubmit-Ereignishandler schauen wir uns einfach den Wert des Eingabefelds an und lesen ihn aus dem DOM.

Wir können jedoch auch React verwenden, um den Wert eines Eingabefelds zu kontrollieren. Dies wird als "controlled input" bezeichnet. Das bedeutet, dass wir das value-Attribut des Eingabefelds manuell festlegen. Wir können eine Zustandsvariable mit dem value-Attribut des Eingabefelds verbinden. Dadurch hat das Eingabefeld immer den gleichen Wert wie die Zustandsvariable. In Kombination mit dem onChange-Ereignishandler können wir die Zustandsvariable aktualisieren, wenn der Benutzer in das Eingabefeld tippt.

```js
function SearchForm() {
  const [searchTerm, setSearchTerm] = useState("");

  function handleSubmit(event) {
    event.preventDefault();
    console.log("Eine neue Suchanfrage wurde abgeschickt:", searchTerm);
  }

  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="searchTerm">Suche</label>
      <input
        name="searchTerm"
        id="searchTerm"
        value={searchTerm}
        onChange={(event) => setSearchTerm(event.target.value)}
      />
      <button>Nach {searchTerm} suchen</button>
    </form>
  );
}
````

In diesem Beispiel kennen Sie immer den Wert des Suchbegriffs-Eingabefelds. Da es sich um eine Zustandsvariable handelt, können Sie sie auch an anderen Stellen in Ihrer Anwendung verwenden. Wenn möglich, sollten Sie uncontrolled inputs verwenden, aber manchmal ist die Verwendung eines controlled inputs erforderlich.

Ein controlled input kann benötigt werden, wenn:

1.- Suchergebnisse während der Eingabe des Benutzers angezeigt werden sollen,

2.- die Eingabe des Benutzers automatisch vervollständigt wird oder

3.- die Eingabe des Benutzers validiert werden soll.





# State-Updates erfolgen nicht sofort:

Wenn wir die Setter-Funktion einer Zustandsvariable aufrufen, aktualisiert React die Zustandsvariable nicht sofort. Stattdessen aktualisiert es den internen Wert und plant eine erneute Renderung der Komponente.

```js
function Counter() {
  const [count, setCount] = useState(0); // count ist anfangs 0

  function handleIncrement() {
    // wenn dies zum ersten Mal aufgerufen wird, ist count immer noch 0
    console.log(count); // → 0

    // dies setzt den internen Zustand von React auf 1,
    // aktualisiert jedoch nicht die count-Variable
    setCount(count + 1);
    console.log(count); // → 0

    // die count-Variable ist immer noch 0, daher ist count + 1 immer noch 1,
    // also wird der interne Zustand von React immer noch 1 sein
    setCount(count + 1);
    console.log(count); // → 0

    // da Setter-Funktionen aufgerufen wurden,
    // plant React eine erneute Renderung
    // der Komponente mit dem neuen count-Wert von 1
  }

  return (
    <>
      <p>Zähler: {count}</p>
      <button onClick={handleIncrement}>um 2 erhöhen</button>
    </>
  );
}

````
Dieses Verhalten kann überraschend sein, aber es ist wichtig zu verstehen, dass Zustandsvariablen nicht sofort aktualisiert werden.

Es gibt einige Möglichkeiten, den obigen Code zu korrigieren. In diesem Beispiel könnten wir setCount(count + 2) aufrufen und fertig sein. Wenn wir aus irgendeinem Grund setCount zweimal aufrufen müssen, können wir die funktionale Form der Setter-Funktion verwenden, die den aktuellen internen Wert der Zustandsvariable als Argument bereitstellt.

```js
function Counter() {
  const [count, setCount] = useState(0); // count ist anfangs 0

  function handleIncrement() {
    // wenn dies zum ersten Mal aufgerufen wird, ist count immer noch 0
    console.log(count); // → 0

    // dies setzt den internen Zustand von React auf 1,
    // aktualisiert jedoch nicht die count-Variable
    setCount((prevCount) => prevCount + 1);
    console.log(count); // → 0

    // der interne Wert von count ist 1,
    // wir erhalten ihn als ersten Parameter der Funktion, die wir dem Setter übergeben.
    // 1 + 1 ist 2, daher ist der interne Zustand von React jetzt _2_
    setCount((prevCount) => prevCount + 1);
    console.log(count); // → 0

    // da Setter-Funktionen aufgerufen wurden,
    // plant React eine erneute Renderung
    // der Komponente mit dem neuen count-Wert von _2_
  }

  return (
    <>
      <p>Zähler: {count}</p>
      <button onClick={handleIncrement}>um 2 erhöhen</button>
    </>
  );
}


 

````
💡 Hier wird das Präfix "prev" verwendet, um anzuzeigen, dass der Wert der vorherige Wert der Zustandsvariable ist. Eine andere gängige Konvention besteht darin, nur den ersten Buchstaben der Zustandsvariable als Parametername zu verwenden: setCount(c => c + 1).


# Arrays in JSX:
Um Elemente aus einem Array in React zu rendern, verwenden wir die Array-Methode .map().

Die Array-Methode .map() wird verwendet, um eine Transformation auf alle Elemente eines Arrays anzuwenden. Beim Rendern eines Arrays in JSX möchten wir genau das tun. Wir möchten jedes Element eines Arrays in ein JSX-Tag umwandeln. Deshalb verwenden wir .map().


```js
function Drinks() {
  const drinks = ["Wasser", "Limonade", "Kaffee", "Tee"];

  return (
    <ul>
      {drinks.map((drink) => (
        <li>{drink}</li>
      ))}
    </ul>
  );
}
````

Schlüssel-Propertie ```KEY```:

Das obige Beispiel hat einen kleinen, aber sehr wichtigen Teil vergessen, nämlich das Schlüssel-Prop- ```key```!

Ohne das Schlüssel-Prop ```key``` erhältst du eine Fehlermeldung in der Konsole:

Warnung: Jedes Element in einer Liste sollte ein eindeutiges "key"-Prop haben.

Beim Rendern eines Arrays in JSX musst du einen eindeutigen Bezeichner als Wert für das Schlüssel-Prop des ersten JSX-Tags übergeben, das in .map() zurückgegeben wird. Dies ist wichtig, damit React Änderungen verfolgen kann, die an den Daten beim erneuten Rendern vorgenommen werden.

Daher müssen Sie immer sicherstellen, dass Ihr Array eine eindeutige ID pro Element enthält. Dies können Sie sicherstellen, indem Sie Objekte verwenden, um die Daten in Ihren Arrays zu definieren.

```js
function Drinks() {
  const drinks = [
    { id: 0, name: "Wasser" },
    { id: 1, name: "Limonade" },
    { id: 2, name: "Kaffee" },
    { id: 3, name: "Tee" },
  ];

  return (
    <ul>
      {drinks.map(({ id, name }) => (
        <li key={id}>{name}</li>
      ))}
    </ul>
  );
}
````

💡 Wenn du das Schlüssel-Prop ```key``` an eine Komponente übergibst, kannst du nicht darauf zugreifen. Es handelt sich um ein spezielles Prop, das von React nur intern verwendet wird

```js
function Drink({ name, key }) {
  console.log(key); // → undefined
  return <li>{name}</li>;
}

function Drinks() {
  const drinks = [
    { id: 0, name: "Wasser" },
    { id: 1, name: "Limonade" },
    { id: 2, name: "Kaffee" },
    { id: 3, name: "Tee" },
  ];

  return (
    <ul>
      {drinks.map(({ id, name }) => (
        <Drink key={id} name={name} />
      ))}
    </ul>
  );
}
````
Wenn du in diesem Beispiel auf die ID zugreifen möchtest, kannst du sie erneut als Prop übergeben:

```js
<Drink key={id} id={id} name={name} />.
````

Schlüsselhafte Fragmente:

Wenn du eine Liste von Elementen renderst, die nicht in einem einzigen JSX-Tag umschlossen sind, kannst du ein <Fragment> verwenden, um die Elemente zu umschließen.
  

```js
import { Fragment } from "react";

function Drinks() {
  const drinks = [
    { id: 0, name: "Wasser", description: "sehr nass" },
    { id: 1, name: "Limonade", description: "ziemlich süß" },
    { id: 2, name: "Kaffee", description: "Cold Brew" },
    { id: 3, name: "Tee", description: "Earl Grey, heiß" },
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
  
Hier kannst du die Kurzschreibweise (<>...</>) für das <Fragment> nicht verwenden, da du das Schlüssel-Prop an das <Fragment> übergeben musst. Die Kurzschreibweise erlaubt das Übergeben von Props nicht.

---

# useState 2

### Das Teilen von Zuständen zwischen Komponenten:

### lifting state up

Wenn mehrere Komponenten denselben Zustand nutzen müssen, können wir den Zustand zur Elternkomponente "hochziehen" (lifting state up) und ihn als Prop an die Kindkomponenten weitergeben. Das bedeutet, dass der Zustand zunächst in der Kindkomponente vorhanden ist und dann nach oben in die Elternkomponenten verschoben wird, je nachdem, in welchen Komponenten er benötigt wird.

Ein Zustandsvariablen (z.B. useState) kann an mehrere Kindkomponenten weitergegeben werden. Die Kindkomponenten können den Zustand dann aktualisieren, indem sie die Setter-Funktion (z.B. setCount) aufrufen.

Es ist wichtig, dass eine Zustandsvariable so weit wie möglich unten im Komponentenbaum (component tree) leben sollte, aber so weit wie nötig nach oben. Wenn der gesamte "App"-Komponente über die Zustandsvariable Bescheid wissen muss, sollte sie in der "App"-Komponente leben. Wenn nur Kindkomponenten des "Article"-Komponente über die Zustandsvariable Bescheid wissen müssen, sollte sie in der "Article"-Komponente leben.

<img src="lifting-state-up.png" width="616" height="694" />

Der Wert einer Zustandsvariablen und die Setter-Funktion können auch als Props an untergeordnete Komponenten weitergegeben werden. Da es sich um Funktionen und Werte handelt, können sie wie alle anderen Daten weitergegeben werden.

```js

function Parent() {
  const [count, setCount] = useState(0);

  function handleIncrement() {
    setCount(count + 1);
  }

  return <Child count={count} onIncrement={handleIncrement} />;
}


function Child({ count, onIncrement }) {
  return (
    <>
      <p>Count: {count}</p>
      <button onClick={onIncrement}>increment</button>
    </>
  );
}
```

### Wie mache ich ein lifting state up:

1.- Um zwei Komponenten miteinander abzustimmen, kannst du ihren Zustand in das übergeordnete Element verschieben, das sie gemeinsam haben.

2.- Dann gibst du die Informationen über Props an die untergeordneten Komponenten weiter. 

3.-
Schließlich übergibst du auch die Event-Handler, damit die untergeordneten Komponenten den Zustand des übergeordneten Elements ändern können.


Es ist hilfreich, Komponenten entweder als "kontrolliert" (gesteuert durch Props) oder als "unkontrolliert" (gesteuert durch den lokalen Zustand) zu betrachten.


Eine Komponente wird als "unkontrolliert" bezeichnet, wenn sie einen eigenen lokalen Zustand hat und nicht von ihrem übergeordneten Element gesteuert wird. Ein Beispiel dafür ist die ursprüngliche Panel-Komponente (Beispiel unten), bei der der aktive Status durch eine lokale isActive-Variable festgelegt wird.

Im Gegensatz dazu ist eine "kontrollierte" Komponente eine, bei der wichtige Informationen durch Props und nicht durch ihren eigenen lokalen Zustand gesteuert werden. Die übergeordnete Komponente hat die volle Kontrolle über ihr Verhalten. Die letzte Panel-Komponente mit der isActive-Prop wird beispielsweise von der übergeordneten Accordion-Komponente gesteuert (Beispiel unten).

Unkontrollierte Komponenten sind einfacher zu verwenden, da sie weniger Konfiguration erfordern. Allerdings sind sie weniger flexibel, wenn es darum geht, sie koordiniert einzusetzen. Kontrollierte Komponenten bieten maximale Flexibilität, erfordern jedoch eine umfassende Konfiguration durch die übergeordneten Komponenten.

In der Praxis gibt es normalerweise eine Mischung aus lokalem Zustand und Props in den Komponenten. Die Begriffe "kontrolliert" und "unkontrolliert" sind keine strengen technischen Begriffe, sondern dienen als hilfreiche Konzepte, um über das Design und die Funktionalität von Komponenten zu sprechen.

Beim Schreiben einer Komponente sollten Sie darüber nachdenken, welche Informationen durch Props kontrolliert werden sollen und welche nicht (durch den lokalen Zustand). Es ist jedoch wichtig zu wissen, dass Sie Ihre Meinung später ändern und die Komponente entsprechend anpassen können.

Ihre App wird sich ändern, während Sie daran arbeiten. Es kommt häufig vor, dass Sie den Status nach unten oder oben verschieben, während Sie noch herausfinden, wo die einzelnen Teile des Status „leben“. Das ist alles Teil des Prozesses!

[Beispiel Hilfe in Codesandbox](https://codesandbox.io/s/react-lift-up-usestates-1z8o9u?file=/App.js)


BEISPIEL 1

<img src="liftup1.png" width="616" />
<img src="liftup2.png" width="616" />


BEISPIEL 2

<img src="liftup3.png" width="616"/>


BEISPIEL 3

<img src="liftup4.png" width="616" />



Die "Single Source of Truth" (SSOT) Architektur in der Informationstechnologie bedeutet, dass Informationen und Datenmodelle so strukturiert werden, dass jedes Datenfeld nur an einer Stelle bearbeitet wird. Dadurch entsteht eine einheitliche Datenstruktur, bei der Verknüpfungen zu anderen Bereichen nur über Referenzen erfolgen. Aktualisierungen an der primären Quelle werden im gesamten System übernommen und bieten Vorteile wie höhere Effizienz, einfache Vermeidung von Inkonsistenzen und vereinfachte Versionierung. Ohne SSOT-Architektur können häufige Duplikate zu Verwirrung und geringerer Produktivität führen.

[React Denken zusammenfassung auf Deutsch](https://github.com/MariaRiosNavarro/Bootcamp-session-notes/blob/main/REACT/React%20Denken.md)









# Use State 3

### Vermeiden der State-Mutation:

Unabhängig davon, wie komplex der State in deiner Anwendung ist (Objekt, Array, Array von Objekten), musst du den State immer als unveränderlich behandeln. Das bedeutet, dass du den State nicht direkt verändern solltest, z.B. indem du ihm einen neuen Wert zuweist.

Um die Mutation des States beim Aktualisieren zu vermeiden, musst du:

1.- ein neues Objekt/Array erstellen (oder eine Kopie des vorhandenen erstellen) und


2.- die Setter-Funktion mit der kürzlich erstellten/aktualisierten Kopie verwenden, um eine erneute Rendereingabe auszulösen.


### Aktualisieren von Objekten im State:

Um eine Kopie eines Objekts zu erstellen und nur einige Eigenschaften zu ändern, kannst du die Spread-Syntax verwenden:

```js
const [person, setPerson] = useState({
  firstName: "John",
  lastName: "Doe",
});

function handleChangeFirstName(firstName) {
  setPerson({ ...person, firstName });
}

// Irgendwo anders:
handleChangeFirstName("Jane");
````

❗️ Wenn du direkt einen neuen Wert zuweisen würdest, würdest du den State mutieren. Dies ist schlecht, da wir den State als unveränderlich behandeln müssen. Das kann zu schwer zu findenden Fehlern führen

```js
// ⚠️ DAS NIEMALS TUN
function handleChangeFirstName(firstName) {
  person.firstName = firstName;
  setPerson(person);
}
````

### Aktualisieren von Arrays im State:

Wie du weißt, gibt es mehrere Möglichkeiten, Arrays zu aktualisieren. Einige von ihnen mutieren jedoch das Array, und andere nicht.


|            | Vermeiden (mutiert das Array)       | Bevorzugen (gibt ein neues Array zurück) |
| -----------|-------------------------------------|------------------------------|
| Hinzufügen | `push`, `unshift`                   | `[...arr]` spread syntax     |
| Entfernen  | `pop`, `shift`, `splice`            | `filter`                     |
| Ersetzen   | `splice`, `arr[i] = ...` assignment | `map`                        |
| Sortieren  | `reverse`, `sort`                   | copy the array first         |




💡 Es spielt keine Rolle, ob dein Array im State nur Primitive oder andere Objekte/Arrays enthält. In allen Fällen solltest du nur die bevorzugten Array-Methoden verwenden.

### Hinzufügen zu einem Array:

Um ein Element zu einem Array hinzuzufügen, kannst du die Spread-Syntax verwenden:

```js
const [numbers, setNumbers] = useState([0, 1, 2]);

function handleAppendNumber(number) {
  setNumbers([...numbers, number]);
}

// Irgendwo anders:
handleAppendNumber(3);
````
Um ein Element am Anfang des Arrays hinzuzufügen, kannst du Folgendes tun:

```js
function handlePrependNumber(number) {
  setNumbers([number, ...numbers]);
}

// Irgendwo anders:
handlePrependNumber(-1);
`````

### Entfernen aus einem Array:

Um ein Element aus einem Array zu entfernen, kannst du die filter-Methode verwenden:

```js
const [numbers, setNumbers] = useState([0, 1, 2]);

function handleRemoveNumber(numberToRemove) {
  setNumbers(numbers.filter((number) => number !== numberToRemove));
}

// Irgendwo anders:
handleRemoveNumber(1);
````

### Ersetzen eines Array-Elements:
Um ein Element in einem Array zu ersetzen, kannst du die map-Methode verwenden:

```js
const [numbers, setNumbers] = useState([0, 1, 2]);

function handleReplaceNumber(oldNumber, newNumber) {
  setNumbers(
    numbers.map((number) => {
      if (number === oldNumber) return newNumber;
      return number;
    })
  );
}

// Irgendwo anders:
handleReplaceNumber(1, 1337);
````

### Aktualisieren von Arrays von Objekten im State:

Die meiste Zeit wirst du Arrays von Objekten in deinem State haben.


### Hinzufügen eines neuen Objekts im Array (...array):

Du kannst ein neues Objekt zum Array im State hinzufügen, indem du die Spread-Syntax (...array) verwendest:

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height: 7.5 },
  { id: 1, name: "Beech", height: 6 },
  { id: 2, name: "Pine", height: 10 }
]);

function handleAddTree(newtree) {
  setTrees([...trees, newtree]);
}

// Irgendwo anders:
handleAddTree({ id: 3, name: "Spruce", height: 13 });
````

### Entfernen eines Objekts im Array (.filter):

Um ein Objekt zu entfernen, kannst du das Array nach einem eindeutigen Identifikator filtern. In den meisten Fällen befindet sich dieser Identifikator im Gültigkeitsbereich, da das relevante Objekt über .map gerendert wird.

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height: 7.5 },
  { id: 1, name: "Beech", height: 6 },
  { id: 2, name: "Pine", height: 10 }
]);

function handleRemoveTree(idToRemove) {
  setTrees(trees.filter((tree) => tree.id !== idToRemove));
}

// Irgendwo anders:
handleRemoveTree(0);
````
### Ersetzen eines Objekts im Array:

Um ein Objekt zu ersetzen, kannst du .map verwenden, um ein neues Array mit dem aktualisierten Objekt zu erstellen. Vergiss nicht, eine Kopie des Objekts zu erstellen (...array), sonst würdest du den State mutieren.

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height: 7.5 },
  { id: 1, name: "Beech", height: 6 },
  { id: 2, name: "Pine", height: 10 }
]);

function handleSetNewHeightForTree(id, height) {
  setTrees(
    trees.map((tree) => {
      if (tree.id === id) return { ...tree, height };
      return tree;
    })
  );
}

// Irgendwo anders:
handleSetNewHeightForTree(0, 8);
````

### Sortieren eines Arrays von Objekten

Um ein Array von Objekten zu sortieren, kannst du sort auf einer Kopie des Arrays (...array) mit einer benutzerdefinierten Vergleichsfunktion verwenden. Die Vergleichsfunktion gibt eine Zahl zurück, die zur Bestimmung der Reihenfolge der Elemente verwendet wird.

```js
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height: 7.5 },
  { id: 1, name: "Beech", height: 6 },
  { id: 2, name: "Pine", height: 10 }
]);

function handleSortTreesByHeight() {
  setTrees([...trees].sort((a, b) => a.height - b.height));
}
````

# Die Wahl der State-Struktur:

Beim Festlegen der Struktur deines States gibt es einige häufige Fallstricke.

Gruppierung verwandter State-Variablen:
Wenn du State hast, der zusammengehört (und zusammen aktualisiert wird), gruppiere ihn in einem einzigen Objekt. Dadurch wird die Aktualisierung des States einfacher.

```js
// ❌ NICHT OPTIMAL
const [userName, setUserName] = useState("Alex");
const [userAge, setUserAge] = useState(28);

// ✅ BESSER
const [user, setUser] = useState({ name: "Alex", age: 28 });
````

### Vermeidung von redundantem State:
Wenn du einen Wert hast, der sich aus einem State ableitet, solltest du vermeiden, ihn im State zu speichern. Verwende stattdessen eine normale Variable.

Das Problem mit redundantem State besteht darin, dass er nicht mehr mit der eigentlichen Quelle synchronisiert wird, wenn du vergisst, ihn korrekt zu aktualisieren.

```js
// ❌ SCHLECHT
const [user, setUser] = useState({ name: "Alex", age: 28 });
const [isAdult, setIsAdult] = useState(user.age >= 18);

// ✅ GUT
const [user, setUser] = useState({ name: "Alex", age: 28 });
const isAdult = user.age >= 18;
````
### Vermeidung von Duplikaten im State:
Vermeide es, den gleichen Wert an mehreren Stellen im State zu speichern. Dies kann zu Fehlern führen und die Aktualisierung des States erschweren.

```js
// ❌ SCHLECHT
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height: 7.5 },
  { id: 1, name: "Beech", height: 6 },
  { id: 2, name: "Pine", height: 10 }
]);

const [selectedTree, setSelectedTree] = useState(trees.find((tree) => tree.id === 0));

// Irgendwo anders:
setSelectedTree(trees.find((tree) => tree.id === 2));

// ✅ GUT
const [trees, setTrees] = useState([
  { id: 0, name: "Oak", height: 7.5 },
  { id: 1, name: "Beech", height: 6 },
  { id: 2, name: "Pine", height: 10 }
]);

const [selectedTreeId, setSelectedTreeId] = useState(0);

const selectedTree = trees.find((tree) => tree.id === selectedTreeId);

// Irgendwo anders:
setSelectedTreeId(2);
````

### Vermeidung von redundanten Listen im State:
Wenn du eine Liste von Elementen im State hast, solltest du vermeiden, eine abgeleitete Version dieser Liste (z. B. gefiltert oder sortiert) zusätzlich im State zu speichern. Führe die Filterung oder Sortierung stattdessen immer bei Bedarf durch

```js
// ❌ SCHLECHT
const [trees, setTrees] = useState([...]);

const [bigTrees, setBigTrees] = useState(trees.filter((tree) => tree.height > 5));

// Irgendwo anders:
setBigTrees(trees.filter((tree) => tree.height > 10));

// ✅ GUT
const [trees, setTrees] = useState([...]);

const bigTrees = trees.filter((tree) => tree.height > 5);

// Irgendwo anders:
const updatedBigTrees = trees.filter((tree) => tree.height > 10);
````

Dies sind einige bewährte Praktiken, die du bei der Verwendung von State in React beachten kannst, um die State-Mutation zu vermeiden und deine Anwendung korrekt zu aktualisieren.
  
 
----  
  
# React-Effekte und Fetch

  
UseEffekt ist eine Möglichkeit, React-Komponenten mit externen Systemen zu synchronisieren.

Beispiele für Interaktionen mit externen Systemen sind:

direkte Manipulation des DOM (z. B. Festlegen des Dokumenttitels)
Netzwerkanfragen zum Abrufen von Daten
Arbeiten mit anderen Web-APIs
Einrichten und Beenden von Abonnements und globalen Ereignisbehandlern
Timer einstellen
Integration mit Drittanbieter-Bibliotheken.
  
Die Verwendung eines Effekts ist eine "Ausbruchsklappe" aus der deklarativen Welt von React. Es ist eine Möglichkeit, imperativen Code auszuführen, der nicht direkt mit dem Rendern der Benutzeroberfläche zusammenhängt. Während die Komponentenfunktion rein sein muss, sind Effektfunktionen von Natur aus nicht rein. ***Sie umfassen Nebeneffekte.***

Ein Effekt wird als Funktion definiert, die nach dem Rendern der Komponente (und der Aktualisierung des DOM) ausgeführt wird. Er kann synchronisiert werden, um nicht nur beim Mounting, sondern auch beim Ändern aller oder nur bestimmter reaktiver Werte innerhalb der Komponentenfunktion ausgeführt zu werden.

Effektfunktionen können eine Aufräumfunktion zurückgeben, die vor der erneuten Ausführung der Effektfunktion oder beim Demounting der Komponente ausgeführt wird.

💡 Ein reaktiver Wert ist ein Wert, der sich ändert: props, state, davon abgeleitete Werte oder Werte und Funktionen, die innerhalb einer Komponentenfunktion deklariert sind.

💡 Mounting bedeutet, dass eine Komponente gerendert, in den DOM eingefügt und zum ersten Mal auf dem Bildschirm angezeigt wird. Danach können verschiedene Updates und Re-Renders auftreten (z. B. aufgrund von State-Änderungen). Demounting bedeutet, dass die Komponente entfernt wird und nicht mehr auf dem Bildschirm angezeigt wird.

### useEffect
  
Das useEffect-Hook wird verwendet, um Effekte zu einer React-Komponente hinzuzufügen. Es hat zwei Argumente:

1.- eine Funktion, die den Effekt definiert (normalerweise ***eine anonyme Funktion***).
  
2.- ein Array von Variablen, von denen der Effekt abhängt
  
Zum Beispiel wird der folgende Code den Titel der Komponente auf den Wert der "title"-Prop aktualisieren:
  

```js
  
  import { useEffect } from "react";

function Title({ title }) {
  useEffect(() => {
    // Das Aktualisieren des Dokumenttitels ist ein Nebeneffekt,
    // der nicht direkt mit dem Rendern der Benutzeroberfläche zusammenhängt
    document.title = title;
  });

  return <h1>{title}</h1>;
}
````
  
 ### Abhängigkeiten des Effekts
  
Der obige Effekt wird nach dem Rendern der Komponente und der Aktualisierung des DOMs ausgeführt. Das ist jedoch häufiger, als notwendig ist. Der Effekt sollte nur dann ausgeführt werden, wenn sich die "title"-Prop ändert. Um dies zu erreichen, können wir ein Array von reaktiven Werten an das useEffect()-Hook übergeben. Der Effekt wird nur dann ausgeführt, wenn sich einer der reaktiven Werte im Array ändert
  
```js
import { useEffect } from "react";

function Title({ title }) {
  useEffect(() => {
    document.title = title;
  }, [title]);

  return <h1>{title}</h1>;
}
````
  
  Dies wird wichtig, wenn die Komponentenfunktion mehr als eine Prop oder State-Variable hat. Stellen Sie sich vor, Sie haben einen "count"-State in der Komponente:
  
 ```js
  import { useEffect, useState } from "react";

function Title({ title }) {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = title;
  }, [title]);

  return (
    <div>
      <h1>{title}</h1>
      <p>{count}</p>
      <button type="button" onClick={() => setCount(count + 1)}>
        Erhöhen
      </button>
    </div>
  );
}
`````
  
  Die Effektfunktion wird nur dann ausgeführt, wenn die "title"-Variable einen anderen Wert als zuvor hat. Die "count"-State-Variable ist nicht Teil des Arrays, daher wird der Effekt nicht ausgeführt, wenn sich der "count"-State ändert.

💡 Fügen Sie immer alle reaktiven Werte, die in der Effektfunktion verwendet werden, zum Abhängigkeitsarray hinzu. React wird Sie mit ESLint-Warnungen darauf hinweisen, wenn Sie vergessen, eine Variable zum Abhängigkeitsarray hinzuzufügen.

Wenn der Effekt keine Abhängigkeiten hat, sollte das Abhängigkeitsarray leer sein: [].

# Ein leeres Abhängigkeitsarray sagt React, dass dieser Effekt nur einmal ausgeführt werden soll, wenn die Komponente zum ersten Mal auf dem Bildschirm erscheint.

### Aufräumfunktion
  
Die Effektfunktion kann eine Aufräumfunktion zurückgeben, die vor der erneuten Ausführung der Effektfunktion oder beim Demounting der Komponente ausgeführt wird
  
 ```js
  import { useEffect } from "react";

function Title({ title }) {
  useEffect(() => {
    // eine Kopie des alten Titels erstellen
    const oldTitle = document.title;

    document.title = title;

    // Aufräumfunktion
    return () => {
      // Rückgängig machen, was wir getan haben, indem wir den alten Titel wieder setzen
      document.title = oldTitle;
    };
  }, [title]);

  return <h1>{title}</h1>;
}
````
  
  Die Aufräumfunktion sollte die Nebeneffekte der Effektfunktion rückgängig machen. Im obigen Beispiel setzt die Aufräumfunktion den Dokumenttitel auf den Standardwert zurück.

Wenn die Effektfunktion zum Einrichten eines Abonnements oder globalen Ereignisbehandlers verwendet wird, sollte die Aufräumfunktion das Abonnement oder den Ereignisbehandler entfernen.
  
  ```js
  import { useEffect, useState } from "react";

function WindowWidth() {
  const [windowWidth, setWindowWidth] = useState();

  useEffect(() => {
    function handleResize(event) {
      setWindowWidth(event.target.innerWidth);
    }

    window.addEventListener("resize", handleResize);

    // Aufräumfunktion
    return () => {
      window.removeEventListener("resize", handleResize);
    };
  }, []);

  return <p>Das Fenster ist {windowWidth}px breit. 📏</p>;
}
`````
  
  Für Timer sollte die Aufräumfunktion den Timer löschen.
  
```js
  
  import { useEffect, useState } from "react";

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const timer = setInterval(() => {
      setSeconds((s) => s + 1);
    }, 1000);

    // Aufräumfunktion
    return () => {
      clearInterval(timer);
    };
  }, []);

  return <p>Der Timer steht bei {seconds} Sekunden. ⏱</p>;
}

  `````
  
📙 Erfahren Sie mehr über das Synchronisieren mit Effekten in der React-Dokumentation.

📙 Auch wenn Effekte unglaublich nützlich sein können, benötigen Sie möglicherweise nicht immer einen Effekt, um das zu tun, was Sie wollen. Lesen Sie mehr dazu in der React-Dokumentation unter "You might not need an effect".
  
  
📙 Read more about [**Synchronizing with Effects** in the React docs](https://react.dev/learn/synchronizing-with-effects).

📙 Even though effects can be incredibly useful, you might not actually need an effect to do what you want. Read more about [**You might not need an effect** in the React docs](https://react.dev/learn/you-might-not-need-an-effect).
  

### Wie man Daten mit Fetch in React abruft
  
Einer der häufigsten Anwendungsfälle für Effekte besteht darin, Daten von einer externen API abzurufen.

Das Konzept funktioniert wie folgt: Nachdem die Komponente zum ersten Mal gerendert wurde, wird eine Effektfunktion ausgeführt, die Daten von einer externen API abruft. Sobald die Daten abgerufen sind, wird eine State-Variable innerhalb der Effektfunktion gesetzt. Wenn der Abruf von einer Prop oder State-Variable abhängt, wird die Effektfunktion erneut ausgeführt, wenn sich die Variable ändert.

Die Effektfunktion selbst kann nicht "async" sein, aber sie kann asynchrone Funktionen aufrufen. Um dies zu umgehen, können Sie eine "async" Funktion innerhalb der Effektfunktion definieren und sie sofort aufrufen (ohne das Ergebnis tatsächlich abzuwarten).

Das folgende Beispiel zeigt, wie Daten von einer API abgerufen und in einer Komponente angezeigt werden:

```js
  import { useEffect, useState } from "react";

function Jokes() {
  const [jokes, setJokes] = useState([]);

  useEffect(() => {
    async function startFetching() {
      const response = await fetch(
        "https://example-apis.vercel.app/api/bad-jokes"
      );
      const jokes = await response.json();

      setJokes(jokes);
    }

    startFetching();
  }, []);

  return (
    <ul>
      {jokes.map(({ id, joke }) => (
        <li key={id}>{joke}</li>
      ))}
    </ul>
  );
}
`````
  
  Wenn die abzurufenden Daten von einer Prop oder State-Variable abhängen, müssen Sie sie zum Abhängigkeitsarray hinzufügen:
  
  ```js
  
  import { useEffect, useState } from "react";

function Joke({ id }) {
  const [joke, setJoke] = useState();

  useEffect(() => {
    async function startFetching() {
      const response = await fetch(
        `https://example-apis.vercel.app/api/bad-jokes/${id}`
      );
      const joke = await response.json();

      setJoke(joke);
    }

    startFetching();
  }, [id]);

  if (!joke) {
    return null;
  }

  return <p>{joke}</p>;
}
`````
  In beiden Beispielen wird die Effektfunktion nur einmal ausgeführt, da das Abhängigkeitsarray leer ist. Dies bedeutet, dass die Daten nur einmal abgerufen werden, wenn die Komponente zum ersten Mal gerendert wird.

📙 Beachten Sie, dass die Fetch-API in modernen Browsern verfügbar ist. Wenn Sie ältere Browser unterstützen müssen, können Sie eine Fetch-Polyfill-Bibliothek wie "whatwg-fetch" verwenden.

📙 Erfahren Sie mehr über das Arbeiten mit asynchronen Daten in der React-Dokumentation
  
 💡 Even when you use a data fetching library, the library will use effects (and the `useEffect` hook) under the hood to fetch data.

📙 Read more about [**Fetching Data** in the React docs](https://react.dev/learn/synchronizing-with-effects#fetching-data). The docs also describe a way to handle race conditions.



## Resources

- [React docs: Synchronizing with Effects](https://react.dev/learn/synchronizing-with-effects)
- [React docs: Fetching data example with useEffect](https://react.dev/learn/synchronizing-with-effects#fetching-dat)
- [React docs: You Might Not Need an Effect](https://react.dev/learn/you-might-not-need-an-effect) 
  

----
  
  
#  LocalStorage
  

💡 Beachte, dass die Web Storage API kein Teil von React ist. Es handelt sich um eine Browser-API, die in allen modernen Browsern verfügbar ist.

Die Web Storage API stellt zwei Methoden zum Speichern von Daten auf dem Client zur Verfügung:

1.- localStorage speichert Daten ohne Ablaufdatum.
  
2.- sessionStorage speichert Daten für eine Sitzung (Daten gehen verloren, wenn der Browser-Tab geschlossen wird).
  
Die Daten werden im Browser und pro Domain gespeichert. Das bedeutet, dass alle Daten, die von example.com gespeichert werden, von www.example.com und subdomain.example.com abgerufen werden können, aber nicht von others.org.

Dadurch ist es möglich, Daten über Seitenneuladungen und Browserneustarts hinweg auf sichere Weise zu speichern.

Zur Speicherung von Daten verwendet die API Schlüssel-Wert-Paare. Der Schlüssel ist ein String und der Wert kann ein String, eine Zahl oder ein boolescher Wert sein.

💡 Alle folgenden Beispiele verwenden localStorage, aber dasselbe gilt auch für sessionStorage.

> 📙 Read more about the [**Web Storage API** on the mdn web docs](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API).

### Daten speichern
  
 
Um Daten zu speichern, verwende die setItem()-Methode:

  
```js
localStorage.setItem("name", "Alex");
  
localStorage.setItem("age", 28);
  
localStorage.setItem("isOnline", true);
`````

  

### Daten abrufen
  
Um Daten abzurufen, verwende die getItem()-Methode:

 ```js
const name = localStorage.getItem("name"); // → "Alex"
const age = localStorage.getItem("age"); // → 28
const isOnline = localStorage.getItem("isOnline"); // → true
``````
  
  
Die getItem()-Methode gibt null zurück, wenn der Schlüssel nicht existiert.

```js
const nope = localStorage.getItem("nope"); // → null
`````
  

### Daten entfernen
  
Um Daten zu entfernen, verwende die removeItem()-Methode:

localStorage.removeItem("name");

### Alle Daten löschen
  
Um alle Daten zu löschen, verwende die clear()-Methode:

localStorage.clear();

### Komplexe Daten speichern
  
Die Web Storage API unterstützt nur Zeichenketten, Zahlen und boolesche Werte. Um komplexere Daten zu speichern, musst du sie zuerst serialisieren. Das kann mit der JSON.stringify()-Methode erfolgen:

  ```js
const user = {
name: "Alex",
age: 28,
isOnline: true,
};

localStorage.setItem("user", JSON.stringify(user));
  
  `````
  

Um die Daten abzurufen, musst du sie mit der JSON.parse()-Methode analysieren:
  
  ```js

const user = JSON.parse(localStorage.getItem("user"));
  
  `````
  

### Hilfsfunktionen
  
Um die Arbeit mit der Web Storage API zu erleichtern, kannst du Hilfsfunktionen erstellen, die die Serialisierung und Deserialisierung abstrahieren:

  ```js
// Daten speichern
function setItem(key, value) {
localStorage.setItem(key, JSON.stringify(value));
}

// Daten abrufen
function getItem(key) {
return JSON.parse(localStorage.getItem(key));
}

  `````
  
  
Diese Funktionen funktionieren sowohl mit einfachen Datentypen wie Zeichenketten und Zahlen als auch mit komplexen Datentypen.

  ```js
setItem("user", {
name: "Alex",
age: 28,
isOnline: true,
});
setItem("count", 42);

const user = getItem("user");
const count = getItem("count");
  
  `````
  

### React mit Local Storage
  
Du kannst die Web Storage API auch in React verwenden. Am häufigsten möchtest du den Zustand(state) im Local Storage persistieren, damit er über Seitenneuladungen hinweg erhalten bleibt.

React bietet verschiedene Möglichkeiten, den Zustand(state) mit dem Local Storage zu synchronisieren. Das allgemeine Konzept besteht darin, den ursprünglichen Zustand(state) aus dem Local Storage abzurufen und den Zustand im Local Storage zu speichern, wenn er sich ändert.

Da es recht kompliziert sein kann, alle verschiedenen Teile selbst richtig zu verbinden, solltest du eine Bibliothek verwenden, die einen Hook dafür bereitstellt.

 ###  ```use-local-storage-state```
  
Die Bibliothek "use-local-storage-state" bietet einen Hook, mit dem du den Zustand im Local Storage persistieren kannst.

Du kannst es als Drop-In-Ersatz für den useState-Hook verwenden (wie im folgenden Beispiel auskommentiert):

  ```js
// import { useState } from "react";
import useLocalStorageState from "use-local-storage-state";

function Counter() {
// const [count, setCount] = useState(0);
const [count, setCount] = useLocalStorageState("count", { defaultValue: 0 });

return (
<div>
<p>Zähler: {count}</p>
<button onClick={() => setCount(count + 1)}>Erhöhen</button>
</div>
);
}
 ````
  
  
Beachte, dass das erste Argument des useLocalStorageState-Hooks der Schlüssel ist, der zum Speichern des Zustands im Local Storage verwendet wird. Wenn du denselben Schlüssel für mehrere Komponenten verwendest, teilen sie sich den gleichen Zustand.

Du musst dich nicht selbst um die Serialisierung oder Deserialisierung komplexer Daten kümmern, wenn du use-local-storage-state verwendest. Die Bibliothek kümmert sich automatisch im Hintergrund darum.
  
  

> 📙 Read more about [**how to use the `use-local-storage-state` hook** in its docs](https://github.com/astoilkov/use-local-storage-state#usage).

---

## Resources

- [Web Storage API on the mdn web docs](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API)
- [use-local-storage-state on GitHub](https://github.com/astoilkov/use-local-storage-state)

  
  
----   
  
# Costum Hooks
  

Manchmal möchtest du einen Hook, der für einen spezifischeren Anwendungsfall entwickelt ist. Du kannst deine eigenen benutzerdefinierten Hooks erstellen. Das sind Funktionen, die mit "use" beginnen und andere Hooks verwenden können.

Beispiele für benutzerdefinierte Hooks:

Ein Zustand mit mehreren spezifischen Aktualisierungsfunktionen (z. B. value, increment(), decrement(), reset() → useCount()).
  
Ein Zustand, der mit Fensterereignissen und -werten synchronisiert ist (z. B. useWindowWidth()).
  
Ein Zustand, der eine abgerufene Ressource darstellt (z. B. useFetch()).
  
Ein Zustand, der im lokalen Speicher des Browsers gespeichert wird (z. B. useLocalStorageState()).
  
📙 Lies mehr über das Wiederverwenden von Logik mit benutzerdefinierten Hooks in der React-Dokumentation.
  
Beispiel eines Zählers:
  
Du könntest einen benutzerdefinierten Hook namens useCount wie folgt definieren:
  
  ```js
  import { useState } from "react";

function useCount(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  function increment() {
    setCount(count + 1);
  }

  function decrement() {
    setCount(count - 1);
  }

  function reset() {
    setCount(initialValue);
  }

  return { count, increment, decrement, reset };
}
````
  
  Und ihn wie folgt verwenden:
  
  ```js
  import { useCount } from "./useCount";

function Counter() {
  const { count, increment, decrement, reset } = useCount(0);

  return (
    <div>
      <p>Zähler: {count}</p>
      <button onClick={increment}>Erhöhen</button>
      <button onClick={decrement}>Verringern</button>
      <button onClick={reset}>Zurücksetzen</button>
    </div>
  );
}
````
  
 💡 Hier verwendet useCount intern den useState-Hook. Deshalb muss es selbst ein Hook sein. Benutzerdefinierte Hooks müssen dieselben Regeln wie normale Hooks befolgen: Ruf Hooks nur auf der obersten Ebene deiner Funktion auf und rufe sie nur in einer React-Funktionskomponente oder einem benutzerdefinierten Hook auf.

Rückgabewerte benutzerdefinierter Hooks:
Benutzerdefinierte Hooks können alles zurückgeben, was auch eine normale Funktion zurückgeben kann. Hier sind einige Beispiele für häufige Rückgabewerte:

Rückgabe eines einzelnen Wertes:
Manchmal müssen Hooks nur einen einzelnen Wert zurückgeben.
  
  ```js
  
  function useWindowWidth() {
  const [width, setWidth] = useState();

  useEffect(() => {
    function handleResize() {
      setWidth(window.innerWidth);
    }

    handleResize();

    window.addEventListener("resize", handleResize);
    return () => window.removeEventListener("resize", handleResize);
  }, []);

  return width;
}
  ````
  
  Dieser Hook gibt nur die aktuelle Fensterbreite zurück. Es muss nichts anderes zurückgegeben werden. Dem Wert kann beim Verwenden des Hooks jeder beliebige Name gegeben werden.
  
  ```js
  const aktuelleFensterbreite = useWindowWidth();
`````
  
  Rückgabe eines Arrays:
  
  ```js
  
  function useD6() {
  const [value, setValue] = useState();

  function roll() {
    setValue(Math.floor(Math.random() * 6) + 1);
  }

  return [value, roll];
}
````
  
  Dieser Hook gibt ein Array mit dem aktuellen Wert und einer Funktion zum Würfeln zurück. Die Rückgabe eines Arrays ist ein häufiges Muster, da es ermöglicht, die Werte mit Array-Destrukturierung ähnlich wie bei useState zu erhalten. Die Array-Destrukturierung hat den Vorteil, dass du den Werten leicht Namen geben kannst.
  
  ```js
  
const [ersterWürfel, würfelnMitErstemWürfel] = useD6();
const [zweiterWürfel, würfelnMitZweitemWürfel] = useD6();
````
  Rückgabe eines Objekts:

```js
  function useCount(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  function increment() {
    setCount(count + 1);
  }

  function decrement() {
    setCount(count - 1);
  }

  function reset() {
    setCount(initialValue);
  }

  return { count, increment, decrement, reset };
}
`````
  
  💡 Die return-Anweisung verwendet die verkürzte Objektschreibweise. Das ist eine schöne Möglichkeit, ein Objekt mit Eigenschaften zurückzugeben, die denselben Namen wie die Variablen haben. Das obige Beispiel ist äquivalent zu:
  
  ```js
  
  return {
  count: count,
  increment: increment,
  decrement: decrement,
  reset: reset,
};
````
  
  Wenn ein Hook mehrere Werte und Funktionen bereitstellt, ist es üblich, ein Objekt zurückzugeben. Dadurch kannst du die Objekt-Destrukturierung verwenden, um die Werte zu erhalten. Du kannst auch die Eigenschaften, die du nicht benötigst, bei der Destrukturierung einfach weglassen.
  
  ```js
  const { count, increment } = useCount(0);
````
  
  ### Parameter für Hooks:
  
Benutzerdefinierte Hook-Funktionen können wie normale Funktionen Parameter haben. Dadurch kannst du den Hook flexibler gestalten. Im obigen Beispiel des useCount-Hooks kann der Anfangswert als Parameter übergeben werden.
  
  ```js
  function useCount(initialValue = 0) {
  // ...
}

const { count, increment, decrement, reset } = useCount(1337);
`````
  
  ### Hooks und Module:
  
Benutzerdefinierte Hooks können in derselben Datei wie die Komponente definiert werden, die sie verwendet. Es ist jedoch auch üblich, sie in einer separaten Datei zu definieren und zu importieren.
  
  ```js
  // useCount.js
import { useState } from "react";

export function useCount(initialValue = 0) {
  // ...
}

// Counter.js
import { useCount } from "./useCount";

function Counter() {
  const { count, increment, decrement, reset } = useCount(0);
  // ...
}
````
  
 ### Abstrahiere wiederkehrende Logik in benutzerdefinierten Hooks:

  Ein einfacher useFetch-Hook:
Da fetch ein sehr häufiger Anwendungsfall ist, eignet es sich gut für einen benutzerdefinierten Hook. Hier ist ein einfacher useFetch-Hook, der eine Ressource abruft und die analysierte Antwort zurückgibt.
  
  ```js
  import { useState, useEffect } from "react";

export function useFetch(url) {
  const [data, setData] = useState();

  useEffect(() => {
    async function startFetching() {
      const response = await fetch(url);
      const data = await response.json();
      setData(data);
    }
    startFetching();
  }, [url]);

  return data;
}
````
  
  Und so wird er verwendet:
  
  ```js
  
  import { useFetch } from "./useFetch";

function App() {
  const jokes = useFetch("https://example-apis.vercel.app/api/bad-jokes");

  return (
    <div>
      <h1>Schlechte Witze</h1>
      <ul>
        {jokes?.map(({ id, joke }) => (
          <li key={id}>{joke}</li>
        ))}
      </ul>
    </div>
  );
}
`````
  💡 Beachte, dass dieser Hook keine fortgeschrittenen Funktionen wie die Behandlung von Wettlaufbedingungen, Fehlerbehandlung, Ladezustände oder Zwischenspeicherung implementiert.

Ein usePokemon-Hook, der useFetch verwendet:
Wenn du nun einen einfach zu verwendenden Hook für einen sehr spezifischen Anwendungsfall wie das Abrufen eines einzelnen Pokémon von der PokeAPI haben möchtest, kannst du einen usePokemon-Hook erstellen, der den useFetch-Hook intern verwendet.
  
  ```js
  
  import { useFetch } from "./useFetch";

export function usePokemon(name) {
  const pokemon = useFetch(`https://pokeapi.co/api/v2/pokemon/${name}`);

  return pokemon;
}
````
  
 und so wird er verwendet:
  
  ```js
  
  import { usePokemon } from "./usePokemon";

function App() {
  const pokemon = usePokemon("pikachu");

  return (
    <div>
      <h1>{pokemon?.name}</h1>
      <img src={pokemon?.sprites.front_default} alt={pokemon?.name} />
    </div>
  );
}
````
  
  Hier verwenden wir einen benutzerdefinierten Hook (useFetch) innerhalb eines anderen benutzerdefinierten Hooks (usePokemon). Dies ermöglicht ziemlich leistungsstarke Abstraktionen.

Wann solltest du einen benutzerdefinierten Hook erstellen?
Benutzerdefinierte Hooks sind ein leistungsstarkes Werkzeug, um wiederkehrende Logik abstrahieren. Du solltest jedoch nur dann einen benutzerdefinierten Hook erstellen, wenn du die Logik in mehreren Komponenten wiederverwenden möchtest. Wenn du die Logik nur in einer einzigen Komponente benötigst, ist es besser, sie in der Komponente selbst zu belassen.

Wenn du etwas nur einmal verwendest: Abstrahiere es nicht. Wenn du etwas zweimal verwendest: Du solltest es abstrahieren.
  
  
  ## Resources

- [Reusing Logic with Custom Hooks in the React docs](https://react.dev/learn/reusing-logic-with-custom-hooks)
  
  
  
----  
  
  [Next.js](https://github.com/MariaRiosNavarro/Bootcamp-session-notes/blob/main/NEXT.js/next.md)

---- 
  
# React auf gestylte Komponenten 
  
React Styled Components ist eine Bibliothek, die es dir ermöglicht, CSS direkt in JavaScript-Code zu schreiben. Es ist eine sogenannte "CSS-in-JS"-Bibliothek. Anstatt separate CSS-Dateien zu erstellen und diese in deinem React-Projekt zu importieren, kannst du mit Styled Components die Styling-Logik direkt in den React-Komponenten selbst definieren.

Warum verwenden wir CSS-in-JS und Styled Components? Es gibt mehrere Vorteile:

1.- Automatische Generierung von kritischem CSS: Nur das CSS, das für eine bestimmte Komponente benötigt wird, wird automatisch in den gerenderten HTML-Code eingefügt. Dadurch wird die Seitenladezeit verbessert.

2.- Keine Klassenname-Konflikte: Da jedes Styled Component eine eindeutige Klasse generiert, gibt es keine Konflikte zwischen Klassennamen in verschiedenen Komponenten.

3.- Einfaches Löschen von CSS: Wenn eine Komponente nicht mehr benötigt wird, kannst du sie einfach löschen, ohne dass du zusätzlichen CSS-Code entfernen musst.

4.- Dynamisches Styling: Du kannst das Styling einer Komponente basierend auf den Props anpassen. Dies ermöglicht es dir, eine Komponente flexibel zu gestalten und verschiedene Stile basierend auf verschiedenen Zuständen oder Daten anzuzeigen.

5.- Einfache Wartung: Da das Styling direkt in den Komponenten definiert ist, ist es einfacher, den Zusammenhang zwischen dem Styling-Code und der Komponente selbst zu verstehen und zu warten.

6.- Automatisches Hinzufügen von Vendor-Präfixen: Styled Components kümmert sich automatisch um das Hinzufügen von Vendor-Präfixen für browser-spezifische CSS-Eigenschaften.

Jetzt schauen wir uns an, wie du Styled Components verwenden kannst:

1.- Grundlegendes Styling: Du kannst ein Styled Component erstellen, indem du die styled Funktion importierst und sie verwenden, um ein Styled Component zu definieren. Das Styled Component kann dann in der return-Anweisung deiner Komponente verwendet werden.
  
  ```js
  import styled from "styled-components";

const StyledButton = styled.button`
  background-color: blue;
  color: white;
  padding: 10px;
`;

export default function MyComponent() {
  return <StyledButton>Click me!</StyledButton>;
}
 ````
  

2.- Styling einer benutzerdefinierten Komponente: Manchmal möchtest du eine bereits vorhandene Komponente mit zusätzlichem Styling erweitern. Du kannst ein Styled Component für diese Komponente erstellen und es wie jede andere Komponente verwenden.

 
 ```js
  import styled from "styled-components";
import CustomComponent from "./CustomComponent";

const StyledCustomComponent = styled(CustomComponent)`
  background-color: yellow;
  font-size: 16px;
`;

export default function MyComponent() {
  return <StyledCustomComponent>Styled Component</StyledCustomComponent>;
}
````
  
  ```js
  //components/List.js
import styled from "styled-components";

export default function List() {
  return (
    <StyledList>
      <ListItem>Item 1</ListItem>
      <ListItem>Item 2</ListItem>
      <ListItem>Item 3</ListItem>
    </StyledList>
  );
}

const ListItem = styled.li`
  background-color: crimson;
`;

const StyledList = styled.ul`
  list-style-type: none;
`;
````
  

3.- Anpassung des Stylings basierend auf Props: Du kannst das Styling eines Styled Components basierend auf den übergebenen Props anpassen. Du kannst eine Funktion verwenden, um das Styling dynamisch zu generieren.
  
  ```js
  import styled from "styled-components";

const StyledButton = styled.button`
  background-color: ${(props) => (props.primary ? "blue" : "gray")};
  color: white;
  padding: 10px;
`;

export default function MyComponent() {
  return (
    <>
      <StyledButton primary>Primary Button</StyledButton>
      <StyledButton>Secondary Button</StyledButton>
    </>
  );
}
````
  
  

4.- Verwendung von Pseudoelementen und Pseudoklassen: Du kannst Pseudoelemente und Pseudoklassen direkt in Styled Components verwenden, indem du das &-Symbol verwendest.
  
  
  
  ```js
  import styled from "styled-components";

const StyledLink = styled.a`
  color: blue;

  &:hover {
    text-decoration: underline;
  }

  &::before {
    content: "🔗";
    margin-right: 5px;
  }
`;

export default function MyComponent() {
  return (
    <StyledLink href="https://example.com">Styled Link</StyledLink>
  );
}
````




  

5.- Globales Styling: Du kannst globales Styling implementieren, indem du ein globales Styled Component erstellst. Dieses Styled Component definiert globale CSS-Regeln, die auf alle Komponenten angewendet werden.
  
  
  
```js
  import { createGlobalStyle } from "styled-components";

const GlobalStyle = createGlobalStyle`
  body {
    background-color: lightgray;
    font-family: Arial, sans-serif;
  }
`;

export default function App() {
  return (
    <>
      <GlobalStyle />
      <h1>Hello, world!</h1>
      <p>This is a global styled component example.</p>
    </>
  );
}

  ````
  

6.- Integration von Google Fonts: Du kannst Google Fonts in dein Next.js-Projekt integrieren und sie mit Styled Components verwenden, indem du das @next/font-Paket verwendest. Es optimiert automatisch die Schriftarten und entfernt externe Netzwerkanfragen für verbesserte Privatsphäre und Leistung.

  ```js
  import { createGlobalStyle } from "styled-components";
import { Open_Sans } from "@next/font/google";

const openSans = Open_Sans({ subsets: ["latin"] });

const GlobalStyle = createGlobalStyle`
  body {
    font-family: ${openSans.style.fontFamily};
  }
`;

export default function App() {
  return (
    <>
      <GlobalStyle />
      <h1>Hello, world!</h1>
      <p>This is a global styled component example with Google Fonts.</p>
    </>
  );
}

  ````
  
  
---


# TESTING:  Warum Testing im Frontend Sinn ergibt

Beim Entwickeln von Apps müssen wir diese regelmäßig testen, um sicherzustellen, dass alles wie erwartet funktioniert und um Fehler zu finden, bevor sie von den Benutzern entdeckt werden.

Das manuelle Testen der App über die Benutzeroberfläche ist zeitaufwendig und unzuverlässig. Das Rendern eines Teils der Benutzeroberfläche und das Simulieren von Interaktionen können in Komponententests automatisiert werden.

Dieser Ansatz versucht, mit der App auf die gleiche Weise zu interagieren, wie es ein echter Benutzer tun würde, indem nach bestimmten Elementen in der gerenderten App gesucht wird:

1.- Suche nach einer Überschrift mit bestimmtem Inhalt.

2.- Suche nach Eingabefeldern mit bestimmten Beschriftungen und Einfügen von Text

3.- Suche nach einer Schaltfläche mit bestimmter Beschriftung und Klicken, um ein Formular zu senden

4.- Suche nach einem erwarteten Ergebnis, das nach dem Senden angezeigt werden sollte

5.- Wir können solche Tests für jede React-Komponente in unserem Code schreiben.

In einer vorherigen Sitzung haben wir uns mit Unit-Tests beschäftigt, die sich auf eine einzelne Einheit/Funktion konzentrieren. Komponententests gehören zur Kategorie der Integrationstests, da sie testen, wie verschiedene einzelne Einheiten/Funktionen zusammenarbeiten, um ein Ergebnis auf dem Bildschirm des Benutzers zu erzeugen.

Anstatt die gesamte App oder eine vollständige Seite zu testen (dieser Ansatz würde End-to-End-Tests sein), erstellen wir getrennte kleinere Tests für einzelne Komponenten.

Die Testdatei wird direkt neben der Komponentendatei mit der Endung .test.js platziert.

Testing Library

Die Testing Library ermöglicht es uns, React-Komponenten in Jest-Tests zu rendern, Benutzerverhalten zu simulieren und die Ergebnisse nach dem erneuten Rendern der Komponente zu überprüfen.

Beispiel

### FahrenheitConverter.js


Die Komponente FahrenheitConverter rendert eine Überschrift, ein Formular und eine Ergebnisausgabe. Wenn das Formular noch nicht abgeschickt wurde, wird anstelle des Ergebnisses eine Ersatznachricht angezeigt. Nachdem das Formular abgeschickt wurde, wird die Berechnung durchgeführt und das Ergebnis im State gespeichert. Dadurch wird eine erneute Rendern der Komponente ausgelöst, sodass das Ergebnis angezeigt wird.


```js
import { useState } from "react";

export default function FahrenheitConverter() {
  const [fahrenheit, setFahrenheit] = useState();

  function handleSubmit(event) {
    event.preventDefault();

    const form = event.target;
    const formElements = form.elements;
    const celsius = formElements.celsius.value;

    setFahrenheit((celsius * 9) / 5 + 32);
  }

  return (
    <div>
      <h1>Temperature Unit Converter</h1>
      <form onSubmit={handleSubmit}>
        <label htmlFor="celsius">°C</label>
        <input type="number" id="celsius" name="celsius" />
        <button>Convert to Fahrenheit</button>
      </form>
      {fahrenheit ? (
        <output>{fahrenheit} °F</output>
      ) : (
        <p>Please enter a Celsius value and submit</p>
      )}
    </div>
  );
}
````

### FahrenheitConverter.test.js

Es gibt drei Tests für diese Komponente:

Test, ob die Überschrift angezeigt wird
Test, ob die Ersatznachricht angezeigt wird, bevor das Formular abgeschickt wurde
Test, ob die Formularinteraktion und das Absenden funktionieren und das Ergebnis korrekt berechnet und anstelle der Ersatznachricht angezeigt wird.


```js
import { render, screen } from "@testing-library/react";
import userEvent from "@testing-library/user-event";
import FahrenheitConverter from ".";

test("renders a heading", () => {
  render(<TemperatureUnitConverter />);
  const heading = screen.getByRole("heading", {
    name: /temperature unit converter/i,
  });
  expect(heading).toBeInTheDocument();
});

test("renders a fallback message if form is not yet submitted", () => {
  render(<FahrenheitConverter />);
  const message = screen.getByText(/please enter a celsius value and submit/i);
  expect(message).toBeInTheDocument();
});

test("converts Celsius to Fahrenheit and renders the result", async () => {
  const user = userEvent.setup();

  render(<FahrenheitConverter />);

  const input = screen.getByLabelText(/°C/i);
  expect(input).toBeInTheDocument();

  const button = screen.getByRole("button", { name: /convert to fahrenheit/i });
  expect(button).toBeInTheDocument();

  await user.type(input, "5");
  await user.click(button);

  const output = screen.getByText(/41 °F/i);
  expect(output).toBeInTheDocument();

  const message = screen.queryByText(
    /please enter a celsius value and submit/i
  );
  expect(message).not.toBeInTheDocument();
});
`````

### Using Queries

Mit screen können Sie Abfragen verwenden, um bestimmte Elemente zu suchen, die im generierten HTML vorhanden sein sollten.

Abfrage Beschreibung

1.-ByRole Suche nach einem Element basierend auf dessen Rolle / aria-*-Attribut (z. B. Button, Textfeld, Überschrift)

2.-ByLabelText Suche nach einem Element (wie einem Eingabefeld) mit einem bestimmten Label

3.-ByText Suche nach einem bestimmten Text

4.-ByTestId Letzte Möglichkeit, um nach einem Element zu suchen, auf das mit anderen Abfragen nicht zugegriffen werden kann. Markieren Sie das Element mit dem Attribut data-testid.

In den meisten Fällen sollten Sie Abfragen mit ***getBy*** verwenden, um sofort einen Fehler zu erhalten, wenn das Element nicht gefunden wird. Manchmal möchten Sie testen, ob etwas nicht angezeigt wird. Verwenden Sie in diesem Fall queryBy, da der Test nicht sofort fehlschlägt, sondern null zurückgibt.

Sie können einen String verwenden, um den zu suchenden Text anzugeben, z. B.: getByText("Hier Text").

Sie können den Text auch in Schrägstrichen mit einem i am Ende anstelle von Anführungszeichen für einen String platzieren, z. B.: getByText(/Hier Text/i).

Dies macht Ihre Tests robuster gegenüber Änderungen in der Implementierung: getByText("Hier Text") würde fehlschlagen, wenn die Komponente die Groß- und Kleinschreibung ändern würde. Aufgrund dessen ist dies eine sehr gängige Konvention beim Schreiben von Tests. Obwohl /Hier Text/i anfangs merkwürdig aussehen mag, gewöhnt man sich recht schnell daran.

Der Ausdruck, der in Schrägstrichen (/Hallo Welt/) eingeschlossen ist, wird als regulärer Ausdruck bezeichnet. Die i-Modifikation am Ende besagt, dass der reguläre Ausdruck keine Unterschiede in Groß- und Kleinschreibung berücksichtigen soll. Reguläre Ausdrücke werden häufig verwendet, um Dinge in großen Zeichenketten zu suchen und sind sehr leistungsstark. Um Ihre Tests zu schreiben, müssen Sie sich jedoch nicht weiter in sie vertiefen als oben gezeigt.

Die Verwendung des Testing Playground hilft Ihnen beim Schreiben von Abfragen.

### Simulieren von Benutzerereignissen


Sie können simulieren, wie Benutzer mit der Komponente interagieren. Zunächst müssen Sie einen virtuellen Benutzer mit ```userEvent.setup()```

einrichten. Anschließend können Sie Ereignisse wie "type" oder "click" simulieren. Vergessen Sie nicht, ```await``` zusammen mit den Benutzerereignissen zu verwenden.

### Verwendung von Matchern

Mit `expect` können Sie Matcher verwenden, um das erwartete Ergebnis Ihres Tests zu formulieren. Es handelt sich um dasselbe Konzept wie beim Unittesting.

Da wir HTML in den Komponententests generieren, können Sie einige zusätzliche Matcher verwenden. Der Matcher toBeInTheDocument wird sehr häufig verwendet.

### Mocks

Ein Mock ist ein Ersatz, der in den Tests anstelle einer Originalfunktion verwendet wird. Häufige Anwendungsfälle sind:

1.-Event-Handler-Funktionen, die als Prop an eine Komponente übergeben werden

2.-Ersetzen eines importierten Pakets

3.-Mocks werden verwendet, um Abhängigkeiten in einem Test zu reduzieren und eine testbare Umgebung für eine Komponente bereitzustellen.


### Mock-Funktion für Event-Handler

Angenommen, Sie haben eine Komponente Counter, die zwei Event-Handler-Funktionen als Prop akzeptiert:

```js
export default function Counter({ onDecrease, onIncrease }) {
  return (
    <>
      <button type="button" onClick={onDecrease}>
        decrease
      </button>
      <button type="button" onClick={onIncrease}>
        increase
      </button>
    </>
  );
}
`````

In einem Test möchten Sie überprüfen, ob die übergebenen Event-Handler-Funktionen aufgerufen werden, wenn auf die Buttons geklickt wird. Da Sie in dem Test keine vollständige App rendern, sondern nur diese Komponente, können Sie eine Mock-Funktion übergeben.

Mock-Funktionen können mit jest.fn() erstellt werden. Dadurch erhalten Sie eine Funktion, die Sie mit expect verwenden können.

```js
test("soll Event-Handler-Funktionen aufrufen", async () => {
  // Erstellt Mock-Funktionen
  const handleDecrease = jest.fn();
  const handleIncrease = jest.fn();

  const user = userEvent.setup();

  render(<Counter onDecrease={handleDecrease} onIncrease={handleIncrease} />);

  const decreaseButton = screen.getByRole("button", {
    name: /decrease/i,
  });
  const increaseButton = screen.getByRole("button", {
    name: /increase/i,
  });

  await user.click(increaseButton);
  await user.click(decreaseButton);
  await user.click(increaseButton);

  expect(handleDecrease).toHaveBeenCalledTimes(1);
  expect(handleIncrease).toHaveBeenCalledTimes(2);
});
`````

### Testen von Next.js (useRouter-Mock)

Wenn Sie Tests für Komponenten schreiben, die den useRouter-Hook von Next.js verwenden, müssen Sie sich einiger Stolpersteine bewusst sein. Wenn Tests ausgeführt werden, laufen sie nicht in einem echten Browser. Daher gibt es keine Browser-Locations-API und der Kontext, den Next.js verwendet, um Routing-Informationen an alle Komponenten in der App bereitzustellen, ist nicht vorhanden.

Der useRouter-Hook erfordert die Browser-Locations-API, daher wird er einen Fehler werfen und die Tests fehlschlagen lassen.

Um Komponenten einschließlich des useRouter-Hooks zu testen, müssen Sie einen Mock schreiben.

Ein Mock ist ein Ersatz, der in den Tests anstelle der Originalfunktion verwendet wird. Sie können den useRouter-Hook von next/router durch einen Mock ersetzen, wie unten beschrieben. Fügen Sie die Funktionen/Eigenschaften des Routers hinzu, die von der getesteten Komponente verwendet werden. Verwenden Sie in einem Mock die einfachste mögliche Implementierung, mit der die Tests funktionieren. Im folgenden Beispiel gehen wir davon aus, dass die getestete Komponente auf router.asPath zugreift und router.push aufruft.

```js
import MyComponent from ".";
/* ... wahrscheinlich weitere Imports hier ... */

jest.mock("next/router", () => ({
  useRouter() {
    return {
      push: jest.fn(),
      asPath: "/",
    };
  },
}));

test("soll rendern", ()
`````

---

# Global State

React Globaler Zustand

Lernen Sie die Konzepte des Prop-Drillings und des globalen Zustands kennen.

### Prop-Drilling

In vielen Situationen wird ein Zustand, der bereits in einer Komponente vorhanden ist, auch in einer anderen Komponente benötigt. Die Komponenten müssen einen gemeinsamen Zustand teilen. Um dies zu lösen, müssen Sie den Zustand in der Komponentenhierarchie nach oben verschieben zur ersten gemeinsamen übergeordneten Komponente. Dies wird als "Lifting State Up" bezeichnet. Von diesem Punkt aus werden Zustandsvariablen oder Funktionen zum Ändern des Zustands über Props an Komponenten auf niedrigerer Ebene übergeben.

Sie finden weitere Informationen zu diesem Thema in den Unterlagen "React State 2".

Prop-Drilling

Einzelne Komponenten, die Zustandsvariablen und deren gemeinsamen Vorfahren verbrauchen, in dem der Zustand definiert ist, können weit voneinander entfernt in der Komponentenhierarchie sein. Die Konsequenz ist, dass Zustandsvariablen über Props durch mehrere andere Komponenten hindurchgereicht werden müssen, bis sie in der Zielkomponente ankommen. Dies wird als "Prop-Drilling" bezeichnet.

Betrachten Sie das folgende Beispiel:

```js
function App() {
  const [userIsLoggedIn, setUserIsLoggedIn] = useState(false);

  return <ProductsPage userIsLoggedIn={userIsLoggedIn} />;
}

function ProductsPage({ userIsLoggedIn }) {
  return <ProductsList userIsLoggedIn={userIsLoggedIn} />;
}

function ProductsList({ userIsLoggedIn }) {
  return products.map((product) => (
    <ProductCard {...product} userIsLoggedIn={userIsLoggedIn} />
  ));
}

function ProductCard({ userIsLoggedIn }) {
  return <ProductActions userIsLoggedIn={userIsLoggedIn} />;
}

function ProductActions({ userIsLoggedIn }) {
  return userIsLoggedIn ? (
    <button>One-click Buy</button>
  ) : (
    <button>Add to Basket</button>
  );
}
````

Die Zustandsvariable userIsLoggedIn wird in der Komponente App definiert. Sie wird viermal weitergegeben, bis sie in der Komponente ProductActions verwendet werden kann.

Stellen Sie sich vor, es gibt noch viele weitere Komponenten in dieser App, von denen einige auch wissen müssen, ob ein Benutzer angemeldet ist oder nicht.

Das Durchreichen von Props durch einige Ebenen ist in Ordnung. Wenn jedoch der Pfad länger wird und mehrere Zustandsvariablen über Props übergeben werden, erhöht sich die Komplexität und die Wartbarkeit des Codes wird reduziert. Auf dem Weg darf das Weitergeben jeder Prop in keiner Komponente vergessen werden.

Namenskonventionen für Props und Funktionen

In den React-Props-Unterlagen finden Sie allgemeine Informationen zur Benennung von Variablen und Funktionen, die über Props übergeben werden.

Im Zusammenhang mit dem Prop-Drilling sollten Sie darauf achten, Props nicht in der Mitte umzubenennen. Wenn eine Prop umbenannt wird, geht die logische Verbindung möglicherweise verloren, was den Code schwerer verständlich macht.

Obwohl wir empfehlen, Funktionen mit handle zu kennzeichnen und entsprechende Props mit on zu kennzeichnen, müssen Sie nicht in jeder Komponente entlang des Weges

---

# React Inmutable State


Wie du gelernt hast, kannst du die im Zustand gespeicherten Daten nicht direkt ändern (mutieren). Du musst den Zustand als schreibgeschützt behandeln. Um den Zustand zu ändern, rufst du die Setter-Funktion auf und übergibst den vollständigen nächsten Zustand.

Betrachte ein Objekt wie folgt im Zustand:
```js
// Beispiel 1: Unveränderlicher Zustand mit Objekt im Zustand
const [user, setUser] = useState({
  name: "John Doe",
  email: "john@doe.com",
});

// Falsche Vorgehensweise: Direkte Zustandsmutation
user.email = "john_doe@example.com"; // ❌ Direkte Zustandsmutation: Das solltest du nicht tun!
setUser(user);

// Richtige Vorgehensweise: Kopie erstellen und Änderungen anwenden
setUser({
  ...user,
  email: "john_doe@example.com",
});

````


Es könnte verlockend sein, einen Wert im Objekt zu verändern und ihn an die Setter-Funktion zu übergeben. Dieser Code funktioniert nicht wie erwartet: Er verändert das im Zustand gespeicherte Objekt direkt!

Wenn du die Setter-Funktion aufrufst, überprüft React, ob sich das Objekt im Zustand geändert hat und die Benutzeroberfläche aktualisiert werden muss. Da du das vorherige Zustandsobjekt mutiert hast, ist es gleich dem neuen Zustand, den du an die Setter-Funktion übergeben hast. React erkennt keinen Unterschied und aktualisiert die Benutzeroberfläche nicht.

Daher musst du eine Kopie der Daten mit Hilfe der Spread-Syntax erstellen und die Änderungen auf die Kopie anwenden. Auf diese Weise mutierst du das vorherige Zustandsobjekt nicht.

```js
setUser({
    ...user,
    email: "john_doe@example.com",
});
```

### Aktualisierung von verschachtelten Zuständen

Es kann etwas komplizierter werden, wenn du Daten in einem tiefer verschachtelten Zustand ändern möchtest.

```js
// Beispiel 2: Unveränderlicher Zustand mit verschachteltem Objekt
const [user, setUser] = useState({
  name: "John Doe",
  contact: {
    email: "john@doe.com",
    phone: {
      mobile: "+001111111111",
      work: "+001234567890",
    },
  },
});
```

Wenn user.contact.phone.mobile geändert werden soll, musst du eine Kopie jeder Ebene erstellen.

```js
// Zustandsaktualisierung mit mehreren Ebenen
setUser({
  ...user,
  contact: {
    ...user.contact,
    phone: {
      ...user.contact.phone,
      mobile: "+009999999999",
    },
  },
});
```

Dieser Code funktioniert einwandfrei! Allerdings musst du eine Menge Code schreiben, um einen einzelnen Wert zu ändern.


### Verwendung von Immer in React: Der useImmer-Hook

Die Immer-Bibliothek hilft dir dabei, Werte in tiefer verschachtelten Zuständen zu aktualisieren.
The [`immer`](https://immerjs.github.io/immer/) library helps you updating values in deeper nested states.

Sie erstellt eine vollständige Kopie des vorherigen Zustands für dich. Diese Kopie ist der Entwurf für den nächsten Zustand. Da es sich um eine Kopie handelt, kannst du Mutationen beliebig anwenden. Die Immer-Bibliothek kümmert sich darum, den Zustand entsprechend zu aktualisieren.

Der useImmer-Hook ermöglicht es dir, Immer einfach in React-Komponenten einzubinden.

The [`useImmer` hook](https://github.com/immerjs/use-immer) 

Anstatt useState aufzurufen, um einen Zustand zu deklarieren, rufst du useImmer auf.
Die zurückgegebene Funktion sollte mit update statt set versehen werden.
Das vorherige Beispiel sieht mit dem useImmer-Hook wie folgt aus.

```js
// Beispiel 3: Verwendung von useImmer-Hook
const [user, updateUser] = useImmer({
  name: "John Doe",
  contact: {
    email: "john@doe.com",
    phone: {
      mobile: "+001111111111",
      work: "+001234567890",
    },
  },
});

```


Wenn du die Update-Funktion aufrufst, übergibst du eine Rückruffunktion. Die Rückruffunktion erhält einen Entwurf für den nächsten Zustand als Parameter. Du kannst Mutationen direkt auf den Entwurf anwenden.

```js

// Zustandsaktualisierung mit useImmer-Hook
updateUser((draft) => {
  // Änderungen direkt am Entwurf vornehmen
  draft.contact.phone.mobile = "+009999999999";
});

```

💡 You can find a good guide on [update patterns](https://immerjs.github.io/immer/update-patterns) in the `immer` docs.

### Arbeiten mit Objekten in Arrays

Die obigen Beispiele konzentrieren sich auf Mutationen in einem Objekt. In vielen Anwendungen arbeitet man jedoch wahrscheinlich mit Objekten, die in Arrays verschachtelt sind.

Dein Zustand könnte folgende Form haben:

```js
const [users, setUsers] = useState([
  {
    id: 1,
    name: "John Doe",
    email: "john@doe.com",
  },
  {
    id: 2,
    name: "Jane Doe",
    email: "jane@doe.com",
  },
  {
    id: 3,
    name: "James Doe",
    email: "james@doe.com",
  },
]);




```

Du kannst eine Aktualisierung durchführen, um die E-Mail-Adresse eines Benutzers mit der ID 1 wie folgt zu ändern:

```js
setUsers(
  users.map((user) =>
    user.id === 1
      ? {
          ...user,
          email: "john_doe@example.com",
        }
      : user
  )
);
```

Derselbe Vorgang mit der von useImmer bereitgestellten Update-Funktion sieht so aus:

```js

const [users, updateUsers] = useImmer([
  {
    id: 1,
    name: "John Doe",
    email: "john@doe.com",
  },
  {
    id: 2,
    name: "Jane Doe",
    email: "jane@doe.com",
  },
  {
    id: 3,
    name: "James Doe",
    email: "james@doe.com",
  },
]);



// Aktualisierung der E-Mail-Adresse eines Benutzers mit ID 1 mit useImmer-Hook
updateUsers((draft) => {
  const user = draft.find((user) => user.id === 1);
  user.email = "john_doe@example.com";
});

```

Der genaue Code, den du schreiben musst, hängt stark von der Art der Operation (Aktualisierung, Einfügen, Löschen) und von der Struktur der Daten ab, die du im Zustand speicherst.

Die Verwendung von Immer hängt von persönlichen Vorlieben und von der Komplexität der Datenstruktur ab. Bei tiefer verschachtelten Strukturen kann dir die Verwendung von Immer ermöglichen, einen einfacheren Code zu schreiben.


## Resources

- [React docs: Updating Objects in State](https://react.dev/learn/updating-objects-in-state)
- [useImmer hook](https://github.com/immerjs/use-immer)
- [Immer: update patterns](https://immerjs.github.io/immer/update-patterns)



---

# React Data Fetching


React Data Fetching (Datenabruf in React)

Lernziele:

Die Vorteile einer Datenabruf-Bibliothek im Allgemeinen verstehen.
Wissen, wie man mit SWR Daten abruft:
Fetcher-Funktion
Lade- und Validierungsstatus
Fehlerstatus
Abrufen in Intervallen
mutate()
Wissen, wie man lokale Zustände mit abgerufenen Daten kombiniert
Warum eine Datenabruf-Bibliothek anstelle von useEffect und fetch?
Bisher konnten Daten mit dem useEffect-Hook abgerufen werden. Dabei musstest du viele Dinge selbst verwalten:

Zwischenspeichern der abgerufenen Daten
Programmatisches erneutes Abrufen
Implementierung eines Fehler- und Ladezustands
Abrufen in Intervallen
und vieles mehr.
Eine Datenabruf-Bibliothek wie SWR bietet Abkürzungen für all diese Aufgaben.

📙 Erfahre mehr über die Funktionen von SWR.

Wie man SWR verwendet
Einfacher Datenabruf
Um den useSWR-Hook zu verwenden, musst du zunächst eine Fetcher-Funktion erstellen, die lediglich eine Wrapper-Funktion für den nativen Fetch ist. Ein grundlegendes Beispiel, das von der Dokumentation empfohlen wird, sieht folgendermaßen aus:

```js
const fetcher = (...args) => fetch(...args).then((res) => res.json());
````

Dann kannst du den useSWR-Hook importieren und ihm zwei Argumente übergeben: die URL, von der du die Daten abrufen möchtest, und die Fetcher-Funktion. useSWR gibt ein Datenobjekt zurück, das du in deinem JSX verwenden kannst.

````
import useSWR from "swr";

const fetcher = (...args) => fetch(...args).then((res) => res.json());

function Character() {
  const { data } = useSWR("https://swapi.dev/api/people/1", fetcher);

  // Daten rendern
  return <div>Hallo {data.name}!</div>; // Hallo Luke Skywalker!
}
````

💡 Beachte, dass useSWR ein Objekt zurückgibt, aus dem du das Datenobjekt destrukturierst. Deshalb kannst du das Datenobjekt nicht einfach beliebig aufrufen, sondern musst es entsprechend der Destrukturierungsregeln umbenennen: { data: person }.

📙 Erfahre mehr über den Einstieg in der Dokumentation.

SWR konfigurieren
Es kann nützlich sein, einige anwendungsspezifische Konfigurationen für SWR festzulegen. Du kannst dies tun, indem du ein Konfigurationsobjekt an das SWRConfig-Komponente in deiner App übergibst (in Next.js in der Datei pages/_app.js). Das folgende Beispiel legt eine anwendungsweite Fetcher-Funktion und ein anwendungsweites Aktualisierungsintervall fest:

```js
import { SWRConfig } from "swr";

const fetcher = (...args) => fetch(...args).then((res) => res.json());

function App() {
  return (
    <SWRConfig
      value={{
        fetcher,
        refreshInterval: 1000,
      }}
    >
      {/* ... deine App */}
    </SWRConfig>
      );
}
````
Das Festlegen einer anwendungsweiten Fetcher-Funktion ist sehr praktisch, wenn Sie dieselbe Fetcher-Funktion an vielen Stellen verwenden möchten.

```js
import { SWRConfig } from "swr";

const fetcher = (...args) => fetch(...args).then((res) => res.json());

function App() {
  return (
    <SWRConfig
      value={{
        fetcher,
        refreshInterval: 1000,
      }}
    >
      {/* Ihre App */}
    </SWRConfig>
  );
}
````
### Lade- und Fehlerzustand:

Das useSWR-Hook bietet einen Fehler, isLoading (lädt Daten zum ersten Mal) und isValidating (immer wenn Daten geladen werden) Zustand, den Sie verwenden können, um den entsprechenden UI-Output zu erstellen.

```js
function Character() {
  const { data, error, isLoading, isValidating } = useSWR(
    "https://swapi.dev/api/people/1"
  );

  if (error) return <div>Fehler beim Laden</div>;
  if (isLoading) return <div>Lade...</div>;

  // Daten rendern
  return (
    <div>
      <span role="img" aria-label={isValidating ? "Validiere" : "Bereit"}>
        {isValidating ? "🔄" : "✅"}
      </span>
      Hallo {data.name}!
    </div>
  );
}
````
Die `fetcher` Funktion oben wirft kein `Error` -Objekt für nicht-ok-Antworten. Das Werfen eines Fehlers ist jedoch erforderlich, damit SWR einen Fehler erkennt und ihn in die error-Eigenschaft des vom Hook zurückgegebenen Objekts einfügt.


```js
const fetcher = async (url) => {
  const res = await fetch(url);

  // If the status code is not in the range 200-299,
  // we still try to parse and throw it.
  if (!res.ok) {
    const error = new Error("An error occurred while fetching the data.");
    // Attach extra info to the error object.
    error.info = await res.json();
    error.status = res.status;
    throw error;
  }

  return res.json();
};
```


This function throws an error with the keys `info` and `status` if the status code of
the response is not in the range of 200-299.

> 💡 The advanced `fetcher` above uses two concepts we have not covered:
> [the `new` operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new)
> and
> [the `throw` statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw).
> These are advanced JS features we don't need to go into detail by now, but diving into it will
> give you a better understanding of JS as a programming language.
> 📙 Read more about [Status Code and Error Object](https://swr.vercel.app/docs/error-handling#status-code-and-error-object).

You can use the `error` object to display a more detailed error message (`message` is the string from `new Error()`):

```js
function Character() {
  const { data, error, isLoading } = useSWR("https://swapi.dev/api/people/1");

  if (error) return <div>{error.message}</div>;
  if (isLoading) return <div>loading...</div>;

  // render data
  return <div>Hello {data.name}!</div>;
}
```

### Fetch auf Intervall und Click auf Button:

Um die API in regelmäßigen Abständen neu abzurufen, übergeben Sie einen refreshInterval-Wert innerhalb eines Options-Objekts als zusätzliches Argument an den useSWR-Hook. In folgendem Beispiel wird SWR die API alle Sekunde neu abrufen:

```js
useSWR("https://swapi.dev/api/people/1", { refreshInterval: 1000 });
````

Um Daten programmgesteuert abzurufen (z. B. durch Klicken auf einen Button), können Sie die mutate-Funktion verwenden, die vom useSWR-Hook bereitgestellt wird.

```js
function Character() {
  const { data, mutate } = useSWR("https://swapi.dev/api/people/1");

  return <RefetchButton onRefetch={() => mutate()}>Daten neu abrufen</RefetchButton>;
}

function RefetchButton({ children, onRefetch }) {
  return (
    <button type="button" onClick={onRefetch}>
      {children}
    </button>
  );
}
```

### Daten werden zwischengespeichert (gecached):

SWR zwischenspeichert die abgerufenen Daten im Arbeitsspeicher des Browsers. Das bedeutet, wenn Sie dieselben Daten zweimal abrufen, werden sie beim zweiten Mal aus dem Cache anstelle des Netzwerks geladen. Das bedeutet, dass Sie den useSWR-Hook mehrmals in Ihrer App verwenden können, ohne sich Gedanken darüber machen zu müssen, dieselben Daten mehrmals abzurufen.

```js
function CharacterName() {
  const { data } = useSWR("https://swapi.dev/api/people/1");
  return <div>Hello {data.name}!</div>; // Hello Luke Skywalker!
}

function CharacterHairColor() {
  const { data } = useSWR("https://swapi.dev/api/people/1");
  return <div>His hair color is {data.hair_color}.</div>; // His hair color is blond.
}

function CharacterHeight() {
  const { data } = useSWR("https://swapi.dev/api/people/1");
  return <div>He is {data.height} cm tall.</div>; // He is 172 cm tall.
}

function App() {
  return (
    <>
      <CharacterName />
      <CharacterHairColor />
      <CharacterHeight />
    </>
  );
}
````

Diese Anwendung ruft die Daten nur einmal ab, obwohl der useSWR-Hook dreimal verwendet wird.

Zusätzlich würde bei manuellem Ändern der Daten (durch Auslösen einer erneuten Validierung) der Cache aktualisiert und die Daten würden allen Komponenten zur Verfügung stehen, die den useSWR-Hook mit demselben Schlüssel (URL) verwenden.

Das gilt auch dann, wenn Sie mutate aus einer anderen Komponente aufrufen, solange sie denselben Schlüssel (URL) hat:

```js
function RevalidateButton() {
  const { mutate } = useSWR("https://swapi.dev/api/people/1");
  return (
    <button type="button" onClick={() => mutate()}>
      Validieren
    </button>
  );
}

// ... andere Komponenten

function App() {
  return (
    <>
      <CharacterName />
      <CharacterHairColor />
      <CharacterHeight />
      <RevalidateButton />
    </>
  );
}
````
### SWR Response API:

Der useSWR-Hook gibt ein SWR-Response-Objekt zurück mit den folgenden Eigenschaften:

`data`: Die abgerufenen Daten für den gegebenen Schlüssel (URL).

`error`: Ein Fehlerobjekt, wenn die Fetcher-Funktion einen Fehler ausgelöst hat.

`isLoading`: true, wenn die Daten zum ersten Mal geladen werden.

`isValidating`: true, wenn eine Anfrage oder Validierung erfolgt.

`mutate()`: Eine Funktion zum Ändern der Daten.


### Kombinieren von abgerufenen Daten mit lokalem Zustand:

Mit SWR kontrollieren Sie den Zustand, der die abgerufenen Daten enthält, nicht selbst. Aus diesem Grund können Sie den Zustand nicht direkt ändern. Das ist gut, denn es ist eine schlechte Praxis, den Zustand, der vom Server abgerufen wurde, direkt zu ändern. Wenn Ihr Server Ihnen Daten liefert, müssen diese die einzige Quelle der Wahrheit sein.

Wenn Sie Serverdaten mit lokalem Zustand verknüpfen möchten (z. B. das Anhängen einer isFavorite-Eigenschaft an einen Film), können Sie den useSWR-Hook verwenden, um die Daten abzurufen, und den useState-Hook, um den lokalen Zustand zu verwalten. Der lokale Zustand sollte über eine eindeutige Kennung (wie ID oder Slug) mit den Serverdaten verbunden sein.

```js 
function Movies() {
  /* Nehmen wir an, die API gibt eine Liste von Filmen zurück:
    [
      {
        id: 1,
        title: "Star Wars",
        year: 1977,
      },
      {
        id: 2,
        title: "The Empire Strikes Back",
        year: 1980,
      }
    ]
  */
  const { data: moviesData } = useSWR("/api/movies");

  // Initialisiere den lokalen Zustand mit einem leeren Array
  const [moviesInfo, setMoviesInfo] = useState([]);

  function handleToggleFavorite(id) {
    setMoviesInfo((moviesInfo) => {
      // Finde den Film im Zustand
      const info = moviesInfo.find((info) => info.id === id);

      // Wenn der Film bereits im Zustand ist, ändere die `isFavorite`-Eigenschaft
      if (info) {
        return moviesInfo.map((info) =>
          info.id === id ? { ...info, isFavorite: !info.isFavorite } : info
        );
      }

      // Wenn der Film nicht im Zustand ist, füge ihn mit `isFavorite = true` hinzu
      return [...moviesInfo, { id, isFavorite: true }];
    });
  }

  return (
    <ul>
      {moviesData.map(({ id, title, year }) => {
        // Finde den Film im Zustand und destrukturiere die `isFavorite`-Eigenschaft
        // Wenn er nicht im Zustand ist, wird `isFavorite` standardmäßig auf `false` gesetzt
        const { isFavorite } = moviesInfo.find((info) => info.id === id) ?? {
          isFavorite: false,
        };

        return (
          <li key={id}>
            {title} ({year})
            <button type="button" onClick={() => handleToggleFavorite(id)}>
              {isFavorite ? "Aus Favoriten entfernen" : "Zu Favoriten hinzufügen"}
            </button>
          </li>
        );
      })}
    </ul>
  );
}

````

💡 Wenn Sie dieses Muster verwenden, verlassen Sie sich darauf, dass Ihr lokaler Zustand ad-hoc erstellt wird. Daher wird Ihr lokales Zustandsarray bei der Suche einen undefinierten Wert zurückgeben, wenn sich der Film nicht in diesem Zustand befindet. Aus diesem Grund verwenden wir den Operator ??, um den Standardwert { isFavorite: false } zu erhalten, wenn der Film nicht im Status ist.

Bei Verwendung von Immer und useImmer kann der Update-Code etwas vereinfacht werden:

```js
function handleToggleFavorite(id) {
  updateMoviesInfo((draft) => {
    // Finde den Film im Zustand
    const info = draft.find((info) => info.id === id);

    // Wenn der Film bereits im Zustand ist, ändere die `isFavorite`-Eigenschaft
    if (info) {
      info.isFavorite = !info.isFavorite;
    } else {
      // Wenn der Film nicht im Zustand ist, füge ihn mit `isFavorite = true` hinzu
      draft.push({ id, isFavorite: true });
    }
  });
}
````
[SWR Doku](https://swr.vercel.app/docs/getting-started)

> 📙 Read more about [SWR's features](https://swr.vercel.app/#features).

> [Getting Started in the docs](https://swr.vercel.app/docs/getting-started).

You can customize the `fetcher` to `throw` an `Error` with additional information (the following
[example is taken from the docs](https://swr.vercel.app/docs/error-handling#status-code-and-error-object)):


