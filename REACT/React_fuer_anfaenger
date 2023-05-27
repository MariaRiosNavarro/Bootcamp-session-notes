### React für anfänger

#Was sind Props in React:


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
