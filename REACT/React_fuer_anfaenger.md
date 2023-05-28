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

# Zustand in React:

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

# Was passiert, wenn sich der Zustand ändert?

Um den Zustand in React zu handhaben, können wir nicht einfach eine "normale" Variable verwenden und ihr einen neuen Wert zuweisen. React muss darüber informiert werden, dass die Daten geändert wurden.

Dies hängt mit dem Renderzyklus von React-Komponenten zusammen.
Wenn React eine Komponente rendert, führt es die Komponentenfunktion aus, die JSX zurückgibt. Wenn das JSX eine Zustandsvariable enthält, verwendet es den Wert der Variablen zu diesem Zeitpunkt, um ihn in das JSX einzufügen. 

# ***Das Aufrufen der "set"-Funktion mit einem neuen Wert informiert React darüber, dass sich der Zustand geändert hat.***

Das Ändern eines Zustands (useState) löst eine erneute Rendervorgang der Komponente aus. Bei der erneuten Rendervorgang führt React die Komponentenfunktion erneut von oben nach unten aus, die dann JSX zurückgibt. Diesmal hat die Variable jedoch einen neuen Wert - den Wert, der mit dem Aufruf der "set"-Funktion übergeben wurde. Dies bedeutet, dass das zurückgegebene JSX den neuen Wert enthält.


---

# useState 2

#  Das Teilen von Zuständen zwischen Komponenten:

# lifting state up

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

# Wie mache ich ein lifting state up:

1.- Um zwei Komponenten miteinander abzustimmen, kannst du ihren Zustand in das übergeordnete Element verschieben, das sie gemeinsam haben.

2.- Dann gibst du die Informationen über Props (Requisiten) an die untergeordneten Komponenten weiter. 

3.-
Schließlich übergibst du auch die Event-Handler, damit die untergeordneten Komponenten den Zustand des übergeordneten Elements ändern können.


Es ist hilfreich, Komponenten entweder als "kontrolliert" (gesteuert durch Props) oder als "unkontrolliert" (gesteuert durch den lokalen Zustand) zu betrachten.


Eine Komponente wird als "unkontrolliert" bezeichnet, wenn sie einen eigenen lokalen Zustand hat und nicht von ihrem übergeordneten Element gesteuert wird. Ein Beispiel dafür ist die ursprüngliche Panel-Komponente, bei der der aktive Status durch eine lokale isActive-Variable festgelegt wird.

Im Gegensatz dazu ist eine "kontrollierte" Komponente eine, bei der wichtige Informationen durch Props und nicht durch ihren eigenen lokalen Zustand gesteuert werden. Die übergeordnete Komponente hat die volle Kontrolle über ihr Verhalten. Die letzte Panel-Komponente mit der isActive-Prop wird beispielsweise von der übergeordneten Accordion-Komponente gesteuert.

Unkontrollierte Komponenten sind einfacher zu verwenden, da sie weniger Konfiguration erfordern. Allerdings sind sie weniger flexibel, wenn es darum geht, sie koordiniert einzusetzen. Kontrollierte Komponenten bieten maximale Flexibilität, erfordern jedoch eine umfassende Konfiguration durch die übergeordneten Komponenten.

In der Praxis gibt es normalerweise eine Mischung aus lokalem Zustand und Props in den Komponenten. Die Begriffe "kontrolliert" und "unkontrolliert" sind keine strengen technischen Begriffe, sondern dienen als hilfreiche Konzepte, um über das Design und die Funktionalität von Komponenten zu sprechen.

Beim Schreiben einer Komponente sollten Sie darüber nachdenken, welche Informationen durch Props kontrolliert werden sollen und welche nicht (durch den lokalen Zustand). Es ist jedoch wichtig zu wissen, dass Sie Ihre Meinung später ändern und die Komponente entsprechend anpassen können.

Ihre App wird sich ändern, während Sie daran arbeiten. Es kommt häufig vor, dass Sie den Status nach unten oder oben verschieben, während Sie noch herausfinden, wo die einzelnen Teile des Status „leben“. Das ist alles Teil des Prozesses!

BEISPIEL 1
<img src="liftup1.png" width="616" height="694" />
<img src="liftup2.png" width="616" height="694" />
BEISPIEL 2
<img src="liftup2.png" width="616" height="694" />
BEISPIEL 3
<img src="liftup2.png" width="616" height="694" />








Das Handling von Formulardaten:

Verwendung von onSubmit für Formulardaten:
Wir können das onSubmit-Ereignis verwenden, um Formulardaten zu handhaben. Das onSubmit-Ereignis wird aufgerufen, wenn der Benutzer das Formular absendet. Wir können die Formulardaten (genau wie in regulärem JavaScript) aus dem Event-Objekt erhalten.

Verwendung von kontrollierten Eingabefeldern:

Wir können React verwenden, um den Wert eines Eingabefeldes zu kontrollieren. Das nennt man einen "kontrollierten Eingabewert" (controlled input). Das bedeutet, dass wir das Wert-Attribut des Eingabefelds manuell festlegen. Wir können eine Zustandsvariable (z.B. useState) mit dem Wert-Attribut des Eingabefelds verbinden. Dadurch hat das Eingabefeld immer den gleichen Wert wie die Zustandsvariable. In Kombination mit dem onChange-Ereignis können wir die Zustandsvariable (z.B. setSearchTerm) aktualisieren, wenn der Benutzer in das Eingabefeld eingibt.

State-Updates erfolgen nicht sofort:

Wenn wir die Setter-Funktion einer Zustandsvariable (z.B. setCount) aufrufen, wird der Zustand nicht sofort aktualisiert. Stattdessen aktualisiert React seinen internen Wert und plant eine erneute Rendervorgang der Komponente.

React Hooks:

Die useState-Funktion (useState) ist Teil einer umfassenderen Funktionssammlung in React, die den Komponenten zusätzliche Funktionen ermöglicht. Hooks sind Funktionen, die Komponentenfunktionen erlauben, sich in React-Funktionen einzuklinken und ihnen ermöglichen, mehr zu tun als eine traditionelle JavaScript-Funktion. Sie folgen der Namenskonvention "useXyz".

Beim Verwenden von Hooks müssen wir ein paar Regeln beachten:

Rufe Hooks nur auf der obersten Ebene auf. Rufe Hooks nicht in Schleifen, Bedingungen oder verschachtelten Funktionen auf.
Rufe Hooks nur in React-Funktionskomponenten oder benutzerdefinierten Hooks auf. Rufe Hooks nicht in regulären JavaScript-Funk
