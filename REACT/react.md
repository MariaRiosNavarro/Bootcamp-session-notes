REACT

1.[React basics](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-basics/react-basics.md) [Challenges](Challenges)

2.[React props](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/react-props/react-props.md) [Challenges](Challenges)










### React Basics

Reagieren Sie auf die Grundlagen
Lernziele
Verstehen, was React ist und warum es verwendet wird
JSX und Unterschiede zu HTML verstehen
Den deklarativen Ansatz von React verstehen
React-Komponenten erstellen
Rendering mit React verstehen
Kenntnisse über das React-Ökosystem
Was ist React und warum verwenden wir es?
React ist eine JavaScript-Bibliothek mit dem Ziel, das Leben des Entwicklers zu erleichtern: In den meisten Fällen müssen Sie nicht direkt mit der DOM-API (z. B. createElement) arbeiten. Sie schreiben einfach einfacheren (deklarativen) Code, der beschreibt, wie die Benutzeroberfläche aussehen soll, und React kümmert sich um das DOM unter der Haube.

Um deklarativen Code für React zu schreiben, verwenden Sie JSX.

Verwendung von JSX

JSX ist eine Syntaxerweiterung für JavaScript. JSX ist weder ein String noch HTML, wie wir es kennen. JSX-Ausdrücke können überall dort verwendet werden, wo ein JavaScript-Ausdruck verwendet werden kann.

const element = <p>Some Text</p>;
Wir verwenden JSX, um React-Elemente zu erstellen. React-Elemente sind ein Zwischenformat, das React während des Rendervorgangs in DOM-Elemente konvertiert. Dadurch können wir unsere Benutzeroberfläche deklarativ mit JSX beschreiben.

Elemente erstellen

Genau wie in HTML werden JSX-Elemente durch öffnende und schließende Tags beschrieben. Das öffnende Tag enthält den Tag-Namen oder den Komponententyp (siehe Verwenden von Komponenten ) und etwaige Attribute. Das schließende Tag enthält denselben Tag-Namen oder denselben Komponententyp wie das öffnende Tag und sonst nichts. Die untergeordneten Elemente des Elements werden zwischen dem öffnenden und schließenden Tag platziert. Wenn das Element keine untergeordneten Elemente hat, kann das schließende Tag weggelassen werden und das Element ist selbstschließend.

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


💡Elemente, die keine schließenden Tags in HTML unterstützen, wie <br>oder <input>müssen in JSX selbstschließend sein (wie <br />oder <input type="text" />).


💡Im Gegensatz zu HTML, das gegenüber fehlenden schließenden Tags resistent ist, ist dies bei JSX nicht der Fall. Wenn Sie vergessen, ein Tag zu schließen, erhalten Sie eine Fehlermeldung.


Komponenten verwenden

Um ein Element aus einer Komponente zu erstellen , können wir einfach über den Funktionsnamen in JSX darauf verweisen und es wie jede integrierte Komponente behandeln:

const element = <MyComponent />;
In Bezug auf Attribute und untergeordnete Elemente funktioniert das Erstellen von Elementen aus Komponententypen genauso wie bei jedem (HTML-)Tag-Namen.

💡JSX unterscheidet zwischen integrierten (HTML-)Tag-Namen und Komponenten anhand des ersten Zeichens im JSX-Tag. Wenn es in Kleinbuchstaben geschrieben ist, wird es als integrierter Tag-Name behandelt. Wenn es in Großbuchstaben geschrieben ist, wird nach einer definierten JavaScript-Funktion mit diesem Namen gesucht. Deshalb ist es wichtig, PascalCase für Komponentennamen zu verwenden.

📙Weitere Informationen zum Schreiben von Markup mit JSX finden Sie in den React Docs .


Attribute

Attribute für integrierte HTML-Elemente verwenden JavaScript-zentrierte Namen aus der DOM-API. In den meisten Fällen sind die Namen dieselben wie in HTML, es gibt jedoch einige Ausnahmen. Beispielsweise classwird das Attribut aus HTML in JSX aufgerufen className.

Die Übergabe von Zeichenfolgenwerten an Attribute erfolgt mithilfe doppelter Anführungszeichen. Um einen beliebigen JavaScript-Ausdruck zu übergeben, verwenden Sie geschweifte Klammern.

const element = <p className="text">Some Text</p>;

const myValue = "This is a string";
const input = <input type="text" value={myValue} minLength={5} />;
Verschachtelungselemente
React-Elemente können auf die gleiche Weise verschachtelt werden, wie wir unsere HTML-Elemente verschachtelt haben.

const element = (
  <div>
    <p>Some Text</p>
    <p>Some more Text</p>
  </div>
);

💡Mehrzeilige JSX-Ausdrücke werden zur besseren Lesbarkeit in Klammern gesetzt. Keine Sorge: Prettier übernimmt das für Sie.


Interpolierende Ausdrücke

Wir können jeden JavaScript-Ausdruck in JSX verwenden, indem wir ihn in geschweifte Klammern einschließen. Dies nennt man Interpolation. Es ähnelt der String-Interpolation in JavaScript-Vorlagen-Strings.

const name = "Pawtricia";
const element = <p>My cat's name is {name}</p>;
const a = 5;
const b = 10;

const element = (
  <p>
    {a} + {b} = {a + b}
  </p>
);

💡Sie können Ausdrücke nur innerhalb von JSX verwenden. Aussagen wie ifoder forsind nicht erlaubt.

💡Informationen zum Interpolieren von JavaScript-Ausdrücken innerhalb von JSX-Attributen finden Sie im Abschnitt „Attribute“ .

📙Lesen Sie mehr über JavaScript in JSX mit geschweiften Klammern in den React Docs .


Komponenten reagieren

Reaktionsanwendungen werden mithilfe von Komponenten erstellt. Eine Komponente ist ein unabhängiger und wiederverwendbarer Teil der Benutzeroberfläche, der eine eigene Struktur, Logik und möglicherweise einen eigenen Stil enthält.

React-Komponenten sind JavaScript-Funktionen, die React-Elemente zurückgeben. Diese Elemente werden dann während des Rendervorgangs von React in DOM-Elemente umgewandelt.

Um eine React-Komponente zu erstellen, schreiben wir eine benannte Funktion (mit PascalCase) und lassen sie mit JSX die gewünschten Elemente zurückgeben.

function MyButton() {
  return (
    <button type="button" className="default-button">
      I'm a button
    </button>
  );
}
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

const p = document.createElement("p");
p.classList.add("introText");
p.textContent = "Hello World!";
rootElement.append(p);
Jetzt ermöglicht uns React die deklarative Verwendung von JavaScript. Wir beschreiben React, was wir wollen, und React findet heraus, wie das DOM gemäß unserer Beschreibung aktualisiert wird.

root.render(<p className="introText">Hello World!</p>);
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
