# Backend-Grundlagen- [challenges](https://github.com/neuefische/ffm-web-23-3/blob/main/sessions/backend-basics/challenges-backend-basics.md)


Bisher haben wir JavaScript nur im Browser verwendet. Aber JavaScript kann auch außerhalb des Browsers verwendet werden.

Node.js ist eine Laufzeitumgebung für JavaScript. Es ermöglicht uns, JavaScript außerhalb des Browsers auszuführen. Node.js unterscheidet sich in einigen Punkten vom Browser. Zum Beispiel besitzt Node.js kein DOM, aber es stellt einige APIs bereit, die im Browser nicht verfügbar sind. Zum Beispiel bietet Node.js eine API zum Zugriff auf das Dateisystem.

Eine Sache, die Node.js tun kann, ist das Erstellen eines Web-Servers. Ein Web-Server ist ein Programm, das auf Anfragen lauscht und Antworten an den Client zurückschickt. Der Web-Server kann verwendet werden, um Webseiten bereitzustellen oder eine API für eine Webanwendung anzubieten.

Ausführen eines Node-Programms
Um ein Node-Programm auszuführen, muss der node-Befehl verwendet werden. Der node-Befehl nimmt den Pfad zu einer JavaScript-Datei als Argument. Der folgende node-Befehl führt die JavaScript-Datei index.js im Stammverzeichnis des Projekts aus: node index.js.

Für Bequemlichkeit enthalten unsere Vorlagen ein Skript in der package.json, mit dem das Programm mit npm run start ausgeführt werden kann. Die Vorlage enthält einen Entwicklungsmodus, der das Programm automatisch neu startet, wenn Änderungen am Code vorgenommen werden. Um den Entwicklungsmodus zu starten, kannst du npm run dev verwenden. Schau dir die package.json-Datei an, um zu sehen, wie die Skripte definiert sind.

### Ein einfaches Node.js-Programm

Ein Node.js-Programm kann fast alles sein. Es kann ein Web-Server, ein Kommandozeilenwerkzeug oder ein Skript sein, das Berechnungen durchführt. Versuche ein Node.js-Programm zu erstellen, das "Hello World" in die Konsole druckt oder einige Berechnungen durchführt.

```js
console.log("Hello World");
const answer = 32 + 4;
console.log(answer);

```


Führe das Programm mit dem node-Befehl aus. Zum Beispiel, wenn du das Programm in einer Datei namens index.js speicherst, kannst du es mit node index.js ausführen.

💡 Du kannst die console.log-Funktion verwenden, um Werte in der Konsole auszugeben. Im Falle von Node.js ist die Konsole das Terminal und nicht die Browser-Konsole.

### Node.js-Server

Du kannst Node.js verwenden, um Web-Server zu erstellen. Dazu kannst du das http-Modul von Node.js verwenden.

Du kannst ein natives Node-Modul importieren, indem du das Präfix node: verwendest. Um zum Beispiel das http-Modul zu importieren, kannst du den folgenden Code verwenden:

```js
import { createServer } from "node:http";
```


Du musst das http-Modul nicht installieren. Es ist in Node.js enthalten.

### Erstellen eines Servers

Das http-Modul bietet eine Funktion namens createServer, die eine Rückruffunktion als Argument annimmt. Die Rückruffunktion wird jedes Mal aufgerufen, wenn eine Anfrage an den Server gestellt wird. Die Rückruffunktion wird mit zwei Argumenten aufgerufen: Anfrage (request) und Antwort (response). Das Anfrage-Objekt enthält Informationen über die Anfrage, die an den Server gestellt wurde. Das Antwort-Objekt wird verwendet, um eine Antwort an den Client zu senden.

```js
import { createServer } from "node:http";

export const server = createServer((request, response) => {
response.statusCode = 200;
response.end("Hello World");
});

```


Die Eigenschaft response.statusCode wird verwendet, um den Statuscode der Antwort festzulegen. Die Methode response.end nimmt einen String als Argument an. Der String wird an den Client gesendet.

Du kannst auf das Anfrage-Objekt zugreifen, um Informationen über die Anfrage abzurufen, die an den Server gestellt wurde. Zum Beispiel kannst du auf die Eigenschaft request.url des Anfrage-Objekts zugreifen, um die angeforderte URL zu erhalten.

```js
import { createServer } from "node:http";

export const server = createServer((request, response) => {
if (request.url === "/") {
response.statusCode = 200;
response.end("Hello World");
} else {
response.statusCode = 404;
response.end("Not Found");
}
});

```

💡 Im Internet findest du die Abkürzungen req und res für request und response. Dies ist eine gängige Konvention, aber req und res sind sehr schwer zu unterscheiden, daher verwenden wir in diesem Bootcamp die vollständigen Namen.

### Starten des Servers (Lauschen auf Anfragen)

Um den Server zu starten, musst du die Methode listen auf dem Serverobjekt aufrufen. Die Methode listen nimmt zwei Argumente an: die Portnummer und eine optionale Rückruffunktion. Die Rückruffunktion wird aufgerufen, wenn der Server bereit ist, Anfragen entgegenzunehmen.

Um den Code, der den Server erstellt, vom Code, der den Server startet, zu trennen, kannst du das Serverobjekt aus einer server.js-Datei exportieren und den Server in index.js starten:

```js
// index.js
import { server } from "./server.js";

const port = 8000;
server.listen(port, () => {
console.log(Server running at http://127.0.0.1:${port}/);
});
```

💡 Wenn du listen aufrufst, wird Node.js das Programm am Laufen halten, anstatt es sofort zu beenden. Dies ist notwendig, da das Programm weiterhin laufen muss, um Anfragen entgegenzunehmen.


## Resources

- [Node.js Website](https://nodejs.org/)
- [`http.createServer()` in the Node.js Docs](https://nodejs.org/api/http.html#httpcreateserveroptions-requestlistener)
- [`server.listen()` in the Node.js Docs](https://nodejs.org/api/http.html#serverlisten)



